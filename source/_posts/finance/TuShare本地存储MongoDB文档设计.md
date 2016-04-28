title: TuShare本地存储MongoDB文档设计
date: 2016-03-17 17:36:24
tags:

- 快捷笔记 
- MongoDB

categories: IT技术
---

TsShare是一个很强大的股票行情抓取项目，但并不提供本地存储的能力。因为项目需要把数据存储在MongoDB，写了这个集合文档设计供参考。

***后来发现使用数据库存储数据的效率相当底，以至于多次卡死。后来终于放弃了采集Ticks数据的方法，转而分析k线数据***


# 集合设计
## stocks   
说明：基础数据，记录数据完整性等

        {
            _id:600496,
            update_at:{                 // 各数据上次更新时间
                stock_basics:2015-08-09 09:00:00,       
                stock_trades:2016-08-09 09:00:00,
                stock_news:2016-08-09 09:00:00
                stock_news_compute:2016-08-09 09:00:00
            }
        }
## stock_basics  
说明：分类、基本面、财报、其它参考数据，每季度刷新一次

        {
            code:600496,
            name:平安银行,
            industry:银行,
            area:深圳,
            pe:6.65,
            forecast:{              // 参考数据-业绩报告
                type,业绩变动类型【预增、预亏等】
                report_date,发布日期
                pre_eps,上年同期每股收益
                range,业绩变动范围
            },
            fund_holdings:{                         //参考数据-基金持股
                date:报告日期
                nums:基金家数
                nlast:与上期相比（增加或减少了）
                count:基金持股数（万股）
                clast:与上期相比
                amount:基金持股市值
                ratio:占流通盘比率
            },
            report:{                        //业绩报告（主表）
                eps,每股收益
                eps_yoy,每股收益同比(%)
                bvps,每股净资产
                roe,净资产收益率(%)
                epcf,每股现金流量(元)
                net_profits,净利润(万元)
                profits_yoy,净利润同比(%)
                distrib,分配方案
                report_date,发布日期
            },        
            profit:{                         //盈利能力
                roe,净资产收益率(%)
                net_profit_ratio,净利率(%)
                gross_profit_rate,毛利率(%)
                net_profits,净利润(万元)
                eps,每股收益
                business_income,营业收入(百万元)
                bips,每股主营业务收入(元)
            },      
            operation:{                     //营运能力
                arturnover,应收账款周转率(次)
                arturndays,应收账款周转天数(天)
                inventory_turnover,存货周转率(次)
                inventory_days,存货周转天数(天)
                currentasset_turnover,流动资产周转率(次)
                currentasset_days,流动资产周转天数(天)
            },      
            growth:{                            //成长能力
                mbrg,主营业务收入增长率(%)
                nprg,净利润增长率(%)
                nav,净资产增长率
                targ,总资产增长率
                epsg,每股收益增长率
                seg,股东权益增长率
            },          
            debtpaying:{                                     //偿债能力
                currentratio,流动比率
                quickratio,速动比率
                cashratio,现金比率
                icratio,利息支付倍数
                sheqratio,股东权益比率
                adratio,股东权益增长率
            },    
            cashflow:{                            //现金流量
                cf_sales,经营现金净流量对销售收入比率
                rateofreturn,资产的经营现金流量回报率
                cf_nm,经营现金净流量与净利润的比率
                cf_liabilities,经营现金净流量对负债比率
                cashflowratio,现金流量比率
            },
            
        }
## stock_trades  
说明：K线、成交量、分笔数据 ，每天下午6点更新当天数据

        {
            code:600496,
            date:2017-09-08,
            kline:{
                open：开盘价
                high：最高价
                close：收盘价
                low：最低价
                volume：成交量
                price_change：价格变动
                p_change：涨跌幅
                ma5：5日均价
                ma10：10日均价
                ma20:20日均价
                v_ma5:5日均量
                v_ma10:10日均量
                v_ma20:20日均量
                turnover:换手率[注：指数无此项]
            },
            ticks:[
                {
                    time：时间
                    price：成交价格
                    change：价格变动
                    volume：成交手
                    amount：成交金额(元)
                    type：买卖类型【买盘、卖盘、中性盘】
                }
            ]
        }
        
## stock_news  
说明：临时数据，实验阶段


        {
            code:600496,
            date:2016-09-18,
            sina:[
                {
                    title:'xxx',
                    views:1212,
                    reply:123,
                    tend_score:19       tend_score:内容评级
                }
            ],
            eastmoney:[
                {
                    title:'xxx',
                    views:1212,
                    reply:123,
                    tend_score:19       tend_score:内容评级
                },
            ]
        }
     