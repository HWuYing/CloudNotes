##移动端1px误差的原因以及解决方案

移动端1px问题在面试和工作中会经常遇到，系统地理解它是一个优秀前端的必修课！

为什么移动端css里面写了1px, 实际看起来比1px粗. 其实原因很好理解:这2个’px’的含义是不一样的. 移动端html的header总会有一句
```html
<meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no">
```

这句话定义了本页面的viewport的宽度为设备宽度,初始缩放值和最大缩放值都为1,并禁止了用户缩放。 

手机存在一个能完美适配的理想viewport, 分辨率相差很大的手机的理想viewport的宽度可能是一样的, 这样做的目的是为了保证同样的css在不同屏幕下的显示效果是一致的, viewport的好处就在于一套css可以适配多个机型。

在window对象中有一个devicePixelRatio属性，他可以反应css中的像素与设备的像素比。然而1px在不同的移动设备上都等于这个移动设备的1px，这是因为不同的移动设备有不同的像素密度。有关这个属性，它的官方的定义为：设备物理像素和设备独立像素的比例，也就是：

```javascript
devicePixelRatio = 物理像素 / 独立像素
```