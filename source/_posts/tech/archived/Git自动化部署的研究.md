title: Git自动化部署的研究
date: 2015-12-04 16:18:22
tags:
categories: IT技术
---

在来一掌时使用的手动Git部署脚本

    #!/bin/sh
    echo 'Starting Deployment...'
    cd /alidata/wwwroot/laiyizhang_v2
    sudo -u apache git reset --hard
    sudo -u apache git pull git@bitbucket.org:laiyizhang/laiyizhang_v2.git master
    
    gulp mobile-lib-js
    gulp mobile-app-js
    gulp mobile-app-css
    
    php composer.phar dump-autoload
    php artisan cache:clear
    php artisan route:cache
    
    


