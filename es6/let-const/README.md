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
```javascript
var messages = ["Hi!", "I'm a web page!", "alert() is fun!"];

for (var i = 0; i < messages.length; i++) {
  alert(messages[i]);
}
```

这段代码的运算结果是显而易见的，但是如果换成下面这种方式呢？
```javascript
var messages = ["Meow!", "I'm a talking cat!", "Callbacks are fun!"];

for (var i = 0; i < messages.length; i++) {
  setTimeout(function () {
    cat.say(messages[i]);
  }, i * 1500);
}
```

结果是连续三个undefined？！原因就是变量的共享问题。仅有的变量 i 被循环体以及所有timeout回调共享了，其结果就是当循环结束时i=3，所以使用messages[3]作为输出会显示undefined，因为没有定义这个元素。如果要解决这个问题，有好几种方法，详见

#####使用let代替var

为了解决向后兼容的编码问题，Brendan Eich引入了关键字let。当你要进行全局搜索的时候，如果之前使用var来定义变量，那么会导致编码不能连续。所以在ES6里，请尝试使用let而不是var。

这两者的主要区别是：

<ul>
  <li><font size=6>let变量是区域变量</font>：let定义的变量仅限于局部区块内，而不是整个函数体内。所以使用let就可避免前述的变量共享问题。</li>
</ul>
