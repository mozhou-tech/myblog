title: LiveReload实现浏览器自动刷新
date: 2016-01-06 16:47:28
tags: 快速笔记
categories: IT技术
---

## 再也不用按F5，节省了不少时间

昨天突然阅读到一篇文章[LiveReload admin Browsersync with Laravel](http://andremadarang.com/livereload-and-browsersync-with-laravel/)，于是乎发现了两个不错的前端开发辅助项目[Browsersync](https://www.browsersync.io/)和[LiveReload](http://livereload.com/)。

## LiveReload
1. 目前使用的是PhpStorm编辑器，使用的是Laravel，所以配置文件可能和gulp.js-livereload不同，以下是gulpfile.js配置详细：

        var elixir = require('laravel-elixir');
            require('laravel-elixir-livereload');       
            elixir(function (mix) {
            mix.livereload();
        });
        
2. 安装[Chrome插件](https://chrome.google.com/webstore/detail/livereload/jnihajbhpnppcggbcgedagnkighmdlei?hl=zh-CN)
3. 如果你没有使用Laravel，那么请参考[中文资料](https://cnodejs.org/topic/53427d16dc556e3b3901861e)，对应的grulpfile.js：

        var gulp = require('gulp'),livereload = require('gulp-livereload');
        gulp.task('watch', function () {    // 这里的watch，是自定义的，写成live或者别的也行
            var server = livereload();
            // app/**/*.*的意思是 app文件夹下的 任何文件夹 的 任何文件
            gulp.watch('app/**/*.*', function (file) {
                server.changed(file.path);
            }); 
        });
        
4. 执行gulp watch并点击浏览器上的“Enable Livereload”开始你的前端开发新旅程吧！

### 提示：
网页要使用服务器打开，如果你使用laravel，则运行

        php artisan serve

如果是在线调试，打开你对应的页面，只要在对应的页面开启“Livereload”插件即可。        

## Browsersync
这是从官网翻译来的介绍，
> Browsersync能让浏览器实时、快速响应您的文件更改（html、js、css、sass、less等）并自动刷新页面。更重要的是 Browsersync可以同时在PC、平板、手机等设备下进项调试。您可以想象一下：“假设您的桌子上有pc、ipad、iphone、android等设备，同时打开了您需要调试的页面，当您使用browsersync后，您的任何一次代码保存，以上的设备都会同时显示您的改动”。无论您是前端还是后端工程师，使用它将提高您30%的工作效率。

想必你已经心动了吧？稍后奉上详细的配置方法。




