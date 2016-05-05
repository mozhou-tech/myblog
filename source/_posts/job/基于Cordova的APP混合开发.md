title: 基于Cordova的APP混合开发
date: 2016-04-29 10:09:34
tags:
- APP开发
- Cordova
categories:
- 工作预研
-----------

原生开发太贵了，如果并非对APP要求较高的C端产品，混合开发已经足够。技术选型时决定使用[ngCordova](http://ngcordova.com/)和[ionic Framework](http://ionicframework.com/)。该方案的缺点是：在性能较差的安卓机VIEW渲染效果较差。[Cordova](https://cordova.apache.org)自定义插件你调用原生lib类库通过js传递给java就行了。

![](/images/2016/ionic-developing-mobile-apps-for-the-real-world-daniel-comas-4-638.jpg)

**关于Cordova集成第三方SDK的参考**:
+ [官方文档：Android Platform Guide](http://cordova.apache.org/docs/en/3.6.0/guide/hybrid/plugins/index.html)
+ http://ionichina.com/topic/55368e249ee76e05064d4b11
+ https://forum.ionicframework.com/t/calling-native-code-sdks-from-ionic/12748
