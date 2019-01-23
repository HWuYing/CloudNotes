###多线程理解

&emsp;&emsp;首先，我们要理解什么是多线程，百度百科上说：多线程（英语：multithreading），是指从软件或者硬件上实现多个线程并发执行的技术。具有多线程能力的计算机因有硬件支持而能够在同一时间执行多于一个线程，进而提升整体处理性能。具有这种能力的系统包括对称多处理机、多核心处理器以及芯片级多处理（Chip-level multithreading）或同时多线程（Simultaneous multithreading）处理器。[1]  在一个程序中，这些独立运行的程序片段叫作“线程”（Thread），利用它编程的概念就叫作“多线程处理（Multithreading）”。具有多线程能力的计算机因有硬件支持而能够在同一时间执行多于一个线程（台湾译作“执行绪”），进而提升整体处理性能。

&emsp;&emsp;按照我的理解就是不阻塞的前提下，时间最优的方法，不局限于流水线（单线）的方法。理解多线程的原理后，结合javascript，本身javascript是不支持多线程的。把异步处理的东西放到一个池中，当同步的解决完即图中的t1到t7，然后唤醒异步队列。
![](/assets/695604-20160731004725184-1393633490.png)


###Concurrent.Thread.js

Concurrent.Thread.js库是利用setTimeout和setInterval方法来模拟线程的概念。并行执行任务。

主要是为了解决浏览器死卡的现象，当一个函数执行非常浪费时间和内存的时候，给另外开辟一个线程。因为javascript是单线程，会阻塞。这时候我们引入这个库文件，可以使代码不阻塞哦，应用方法主要是create方法创建一个单线程。

```javascript
Concurrent.Thread.create(function(){
    $('#test').click(function  () {
        alert(1);
    });
    /*下面有一段特别复杂的函数*/
    for (var i = 0;i<1000000;i++) {
        console.log(i);
    };
});
```

这么就可以在浏览器上边点击div有效果，同时console也在一直不停的打印数据。各忙各的。

这是理解Concurrent.Thread.js库应用的最简单方法。Concurrent.Thread提供了一个应用JavaScript 的异步通信方式实现的定制通信库。类似于AJAX的原理，用get或者post方法发送和响应数据。具体参考可以穿越链接http://www.cnblogs.com/0banana0/archive/2011/06/01/2067402.html，这里可以看到更详细的解释。

###WebWork

&emsp;&emsp;js是单线程的去跑代码，比如如果做一个循环从0到一个很大的数字相加然后输出，浏览器可能会假死（无响应状态）。但是用webwork以后，就可以非常方便的进行渲染网页的同时，计算这个数据。在 HTML5 中提出了工作线程（Web Worker）的概念，并且规范出 Web Worker 的三大主要特征：能够长时间运行（响应），理想的启动性能以及理想的内存消耗。Web Worker 允许开发人员编写能够长时间运行而不被用户所中断的后台程序，去执行事务或者逻辑，并同时保证页面对用户的及时响应。

WebWork能做什么？

1.可以加载一个JS进行大量的复杂计算而不挂起主进程，并通过postMessage，onmessage进行通信, 在主线程与子线程间进行通信，使用的是线程对象的postMessage和onmessage方法。不管是谁向谁发数据，发送发使用的都是postMessage方法，接收方都是使用onmessage方法接收数据。postMessage只有一个参数，那就是传递的数据，onmessage也只有一个参数，假设为event，则通过event.data获取收到的数据。

2.可以在worker中通过importScripts(url)加载另外的脚本文件，即多个js文件

3.可以使用 setTimeout(), clearTimeout(), setInterval(), and clearInterval()：定时器可以使用线程 

4.可以使用XMLHttpRequest来发送请求，使用AJAX

5.可以访问navigator的部分属性：可以在localStorage和sessionStorage

下面来具体说明一下webwork的专用线程使用步骤。

###专用线程：Dedicated Worker

（1）.当然是创建线程
```javascript
var worker = new Worker("worker.js");
```
（2）为了在页面主程序接收从多线程传递过来的消息，我们需要使用多线程的 onmessage 事件处理器，定义 onmessage 的实例代码如下：
```javascript
worker.onmessage = function (event) { ... };
```
（3）将数据传给线程