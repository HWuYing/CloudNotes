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
1px变粗的原因： viewport的设置和屏幕物理分辨率是按比例而不是相同的. 移动端window对象有个devicePixelRatio属性, 它表示设备物理像素和css像素的比例, 在retina屏的iphone手机上, 这个值为2或3, css里写的1px长度映射到物理像素上就有2px或3px那么长。

####解决方案 

1.rem解决：
```javascript
////根据屏幕大小及dpi调整缩放和大小 
(function () {
        var scale = 1.0;
        var ratio = 1;
        if (window.devicePixelRatio >= 2) {
            scale *= 0.5;
            ratio *= 2;
        }
        var text = '<meta name="viewport" content="initial-scale=' + scale + ', maximum-scale=' + scale + ',' + ' minimum-scale=' + scale + ', width=device-width,' + ' user-scalable=no" />';
        document.write(text);
        document.documentElement.style.fontSize = 50 * ratio + "px";
})();
```
2.flexible.js 

这是淘宝移动端采取的方案, github的地址:https://github.com/amfe/lib-flexible. 前面已经说过1px变粗的原因就在于一刀切的设置viewport宽度, 如果能把viewport宽度设置为实际的设备物理宽度, css里的1px不就等于实际1px长了么. flexible.js就是这样干的。

&lt; meta name=”viewport” &gt;里面的scale值指的是对ideal viewport的缩放, flexible.js检测到IOS机型, 会算出scale = 1/devicePixelRatio, 然后设置viewport
```javascript
metaEl = doc.createElement('meta');
metaEl.setAttribute('name', 'viewport');
metaEl.setAttribute('content', 'initial-scale=' + scale + ', maximum-scale=' + scale + ', minimum-scale=' + scale + ', user-scalable=no');
```

3.伪类+transform实现
原理：是把原先元素的 border 去掉，然后利用 :before 或者 :after 重做 border ，并 transform 的 scale 缩小一半，原先的元素相对定位，新做的 border 绝对定位。 
```html
<!DOCTYPE html> 
<html> 
 <head> 
 <meta charset="UTF-8"> 
 <title>test</title> 
 </head> 
 <body> 
<div class="box-shadow-1px scale">box-shadow-1px</div>
<style>
.box-shadow-1px {
    height: 200px;
    width: 200px;
    text-align: center;
}
.scale{
  position: relative;
  margin-bottom: 20px;
  border:none;
}
.scale:after{
  content: '';
  position: absolute;
  top: 0;
  left: 0;
  border: 1px solid #000;
  -webkit-box-sizing: border-box;
  box-sizing: border-box;
  width: 200%;
  height: 200%;
  -webkit-transform: scale(0.5);
  transform: scale(0.5);
  -webkit-transform-origin: left top;
  transform-origin: left top;
}
</style>
 <script> 
console.log(typeof ('a'+1))
 </script> 
 </body> 
</html>
```