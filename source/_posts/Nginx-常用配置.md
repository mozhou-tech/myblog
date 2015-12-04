title: Nginx 常用配置
date: 2015-12-04 13:59:06
tags:
categories: IT技术
---

收集一些常用的Nginx配置方法，具体说明见注释。
1. [HTTP访问控制(CORS)](https://developer.mozilla.org/zh-CN/docs/Web/HTTP/Access_control_CORS)
2. [CORS on Nginx 官方配置](http://enable-cors.org/server_nginx.html)


    location / {
        index  index.php index.html index.htm;
        # 隐藏index.php
        try_files $uri $uri/ /index.php$is_args$query_string;
        # CORS 预请求
        if ($request_method = 'OPTIONS') {
            add_header Access-Control-Allow-Origin *;
            add_header Access-Control-Allow-Credentials true;
            add_header Access-Control-Allow-Methods 'GET, POST, OPTIONS';
            add_header 'Access-Control-Allow-Headers' 'DNT,X-Mx-ReqToken,Keep-Alive,User-Agent,X-Requested-With,If-Modified-Since,Cache-Control,Content-Type';
            return 200;
        }
    }
    # 配置字体可以跨站调用
    location ~* \.(eot|ttf|woff|svg)$ {
        add_header Access-Control-Allow-Origin *;
    }
    
     # pass the PHP scripts to FastCGI server listening on 127.0.0.1:9000
     #
     location ~ \.php$ {
        fastcgi_pass   127.0.0.1:9000;
        fastcgi_index  index.php;
        fastcgi_param  SCRIPT_FILENAME  $document_root$fastcgi_script_name;
        include        fastcgi_params;
     }
     
3. 配置Nginx缓存，加速访问[官方参考](http://nginx.org/en/docs/http/ngx_http_headers_module.html)


    # cache.appcache, your document html and data
    location ~* \.(?:manifest|appcache|html?|xml|json)$ {
      expires -1;
      access_log logs/static.log;
    }
    
    # Feed
    location ~* \.(?:rss|atom)$ {
      expires 1h;
      add_header Cache-Control "public";
    }
    
    # Media: images, icons, video, audio, HTC
    location ~* \.(?:jpg|jpeg|gif|png|ico|cur|gz|svg|svgz|mp4|ogg|ogv|webm|htc)$ {
      expires 1M;
      access_log off;
      add_header Cache-Control "public";
    }
    
    # CSS and Javascript
    location ~* \.(?:css|js)$ {
      expires 1y;
      access_log off;
      add_header Cache-Control "public";
    }
    
    # WebFonts
    # If you are NOT using cross-domain-fonts.conf, uncomment the following directive
    # location ~* \.(?:ttf|ttc|otf|eot|woff|woff2)$ {
    #  expires 1M;
    #  access_log off;
    #  add_header Cache-Control "public";
    # }


