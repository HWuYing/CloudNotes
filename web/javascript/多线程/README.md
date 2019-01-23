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