##移动端1px误差的原因以及解决方案

移动端1px问题在面试和工作中会经常遇到，系统地理解它是一个优秀前端的必修课！

为什么移动端css里面写了1px, 实际看起来比1px粗. 其实原因很好理解:这2个’px’的含义是不一样的. 移动端html的header总会有一句
```html
<meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no">
```

