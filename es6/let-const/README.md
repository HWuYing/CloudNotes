## 类语法let和const

本文介绍的是有关let和const关键字的使用。

对于JS而言，开发者有可能遇到以下两个问题。

#####问题一：区块不等同于作用域。

在一个JS函数中声明的变量的作用域是在整个函数里，由此将会引发两个问题。

第一个是区块里定义的变量的作用域不仅限于区块，而是作用于整个函数中。请看以下例子，里面定义的变量是t：

```javascript
function runTowerExperiment(tower, startTime) {
  var t = startTime;

  tower.on("tick", function () {
    ... code that uses t ...
  });
  ... more code ...
}
```
如果要增加一个用于检测保龄球速度的功能，可能会这样写：
```javascript
function runTowerExperiment(tower, startTime) {
  var t = startTime;

  tower.on("tick", function () {
    ... code that uses t ...
    if (bowlingBall.altitude() <= 0) {
      var t = readTachymeter();
      ...
    }
  });
  ... more code ...
}
```