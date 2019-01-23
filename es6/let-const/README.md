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

现在问题来了，我们不自觉地添加了一个同名变量 t ；而这个 t 的作用域会发生改变，不再是第一次定义时的t了。可见，JS中的变量类似于Photoshop中的油漆桶工具，至声明开始可以向前或向后作用直到碰到函数边界，我们称之为“抬升”。这个例子中抬升导致的结果是，以 t 为计算对象的结果会产生NaN。

#####问题二：变量在循环体中的共享

请先看下面：

