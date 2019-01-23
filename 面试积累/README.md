1、js 是单线程，如何实现多线程 （web worker）

2、有没有看过react经过webpack打包之后的JS文件


3、浅拷贝 与 深拷贝

4、console.log( 1 = ‘1’)

7、拿到了后端一次性返回的很多数据，如何在前端更好的渲染，给用户更好的体验（分页）

8、浏览器渲染过程， dom tree, css tree , render tree , 词法分析，从上到下
        
9、css 盒模型

10、http://www.cnblogs.com/Maculish/p/5228948.html

11、 sass，less

12、 html5，语义化

13、浏览器适配，响应式设计

14、 JavaScript设计模式

15、react 生命周期
        
16、redux 思想
    
17、react-router4
18、cdn托管图片，为什么能提升图片加载的效率呢
        CDN，内容分发网络，主要是通过在现有的internet中，增加一层新的网络架构，将网站的内容发布到最接近用户的‘网络边缘’，使得用户可以就近获取所需有的内容，解决网络阻塞情况，提高用户访问网站的响应速度。

19、如何判定一个数是2的乘方，（递归）（先这个这个数转为二进制，再判断二进制数据，是否只有第一个是1， 其余的都是0，满足这种情况就是2的乘方）
20
、
    
21、给一个长宽为200的div，如何实现多行文字水平垂直居中（多种方案）

22、给ABC三个div，如何实现水平自适应排列

23、目前除了react，你还了解哪些主流框架，比如react-navite，桌面应用

24、做过的东西中，主要兼容哪些浏览器，碰到过哪些兼容性问题

25、手写一个格式化时间的函数

26、对继承了解多少？说一下有哪些继承方式

27、对设计模式了解多少？除了发布订阅、单例，还了解其他的设计模式不
         https://segmentfault.com/a/1190000010914032
         http://garychang.cn/2017/01/14/%E8%AE%BE%E8%AE%A1%E6%A8%A1%E5%BC%8F/

28、react跨组件通信  https://www.jianshu.com/p/fb915d9c99c4
        父组件 -> 子组件 ： props
        子组件 -> 父组件： 回调函数，父组件将函数通过props传递给子组件，子组件执行该方法，就是在和父组件进行沟通了
        跨级组件通信（父组件 -> 子组件的子组件）：层层传递 props；  使用 context 对象
        非嵌套组件通信：利用二者共同父组件的context通信；使用自定义事件的方式（事件订阅）

29、了解那些增强 action 的中间件框架，类似于 middware 的小框架
        redux-saga、redux-thunk、thunk-middleware

30、比较react、angular、vue的优缺点
        react：VDOM，提高渲染速率；有生命周期控制；关注UI组件化；数据单向更新；学习成本低
        angular：数据双向绑定；依赖注入；脏检查机制；学习成本高；指令
        Vue：API设计简单；v-modal实时渲染； 指令；学习成本低

31、图片懒加载，是如何实现的？图片预加载，是如何实现的？
        预加载，是提前把图片加载到本地，之后之间从缓存那儿拿图片。
        懒加载，是当图片出现在了可视化窗口之后，图片才加载到本地。主要是要如何判断图片出现在了视野区域

32、JS事件，什么是捕获，什么是冒泡，如何阻止他们？
        IE 事件机制：只有冒泡，阻止冒泡 cancelBubble;
        标准事件机制：先从上到下捕获，然后执行，最后从下到上冒泡，preventDefault. +. stopPropagation
        netscape 事件机制：

33、时间负责度和空间复杂度，怎么计算的。。会哪些算法

35、继承，有哪几种实现方式。（原型继承、call | apply 继承、构造函数继承、混合继承）

36、了解敏捷开发的流程不？

37、你公司开发，是怎么样的流程？你担任什么样的角色

38、事件委托是用的什么样的机制 （浏览器的事件冒泡机制）

39、Promise三个状态，是哪三个（resolve，rejected，pending）
        pending. ->  resolve （未完成 -> 已完成）
        pending  ->  rejected （未完成 ->  失败）

40、实现跨域，有哪些方式。（webpack 配置跨域， jsonp，domain）
        webpack  配置 proxy
        jsonp  需要前后端一起配合实现跨与
       document.domain   
        nginx  反向代理
        CORS. 跨资源共享
        window.name + iframe
        window.postMessage
        websocket

41、HTTP请求的状态码有哪些？（1 xx -- 5 xx）都是哪些原因造成的这些状态码？400 状态码，有没有可能是服务器端的问题造成的  
        http://www.cnblogs.com/alifpga/p/7802399.html
        1xx：信息性状态码，接收的请求正在处理
        2xx：成功状态码，请求正常处理完毕
        3xx：重定向状态码，需要添加附加操作以完成请求
        4xx：客户端错误状态码，服务器无法处理请求
        5xx：服务器错误状态码，服务器处理请求错误

42、HTTP与HTTPS的区别是啥子   https://www.cnblogs.com/ranyonsue/p/5984001.html
        HTTP v0.9：只允许发送GET请求，且不支持协议头，所以只支持纯文本内容；
        HTTP v1.0：在0.9版本上支持协议头，支持GET、POST，有明显的响应状态，响应对象不仅限于文本，支持长链接、缓存机制以及身份认证；
        HTTP v1.1：目前运用最广泛的版本，请求头和响应头新增HOST头域，新增了更多的请求方式，以及缓存处理
        HTTP v2.0：基本上就是用https，把数据格式进行二进制分帧，改进传输性能。

        HTTPS 在HTTP的基础上新增了一个SSL/TLS协议，HTTPS = HTTP + SSL/TLS
        SSL，安全套接字，位于TCP/IP协议与各应用层协议之间，为数据提供安全支持；
        TLS，传输层安全
        SSL/TLS 所用到的加密算法，一般就是对称加密、非对称加密、哈希算法、数字签名
        对称加密：加密和解密都是使用同一个秘钥。DES、AES-GCM
        非对称加密：分为公钥和秘钥，算法性能低，但是安全性很高。RSA、DSA、DH
        哈希算法：将任意长度的信息转为较短的固定长度的值，且算法不可逆。MD5、SHA-1
        数字签名：在信息的后面加一段信息，用来证明内容没有修改过。

43、对 es6 了解多少？有没有使用过new Map 的东西？async \ await 是用来解决什么问题而出现的？迭代器如何实现同步
        es6 新增特性：
                                let   const   解构赋值   箭头函数   … 操作符  class   iterable 可枚举类型
        es7 新增特性：
                               Array.prototype.includes
        es8 新增特性：
                                Object.values   Object.entries   async/await

44、react生命周期。https://segmentfault.com/a/1190000004168886
        组件实例化时：
                                getDefaultProps.  设置 props 的初始值
                                getInitialState.      设置state 初始值
                                componentWillMount   挂载虚拟Dom前执行的
                                render   形成虚拟DOM
                                componentDidMount.  组件已挂载好了，已经有了真实的DOM节点，主要是在这儿处理http请求，拿回数据
        组件实例存在期：
                                componentWillReceiveProps.
                                shouldComponentUpdate    多次渲染，默认返回true，可设置返回false来阻止多次渲染
                                componentWillUpdate.
                                render
                                componentDidUpdate
        组件销毁时期：
                                componentWillUnmount  
                                render
                                componentDidUnmount
        


45、redux 中间件，用过哪些？每个中间件库，有哪些区别
        redux-thunk   处理异步action，可以获得各个异步操作时期的值
        redux-actions  简化redux的操作
        redux-promise  轻松创建和处理异步action
        redux-saga.  

46、 深拷贝和浅拷贝的机制，深拷贝是新开辟一个内存地址来存放数据，浅拷贝是更改数据的可读属性。自己编码实现一个深拷贝

47、文件缓存和数据缓存，是什么样子的. https://zhuanlan.zhihu.com/p/44789005
        前端数据缓存：cookie、sessionStorage、localStorage、IndexDB、manifset、Cache Storage
        文件缓存：( 操作系统是先读内存，再读硬盘 )
            缓存位置：Service Worker > Memory Cache（内存中的缓存） > Disk Cache （硬盘中的缓存）> 网络请求
               

            失效策略：Cache-Control > ETag

48、什么是web语义化，有哪些好处（SEO什么的）
        使用恰当的HTML标签、class类名等内容，让页面具有良好的结构和含义。，从而让人和机器都能够快速的理解网页。
        好处：正确的标签做正确的事情；页面内容结构化；无CSS的时候也能容易读懂；便于爬虫和SEO

49、background的 rgba 和 opacity 有啥子区别
        rgba，只针对设置的背景颜色做透明度处理；
        opacity，是针对该元素做透明处理，包括该元素内的东西，都会被透明处理；
        filter，滤镜，也是针对元素来设置的，不过可以更强大，可以设置黑白灰颜色，模糊度，饱和度等。

50、事件循环机制，比如给一个setTimeout和一个Promise，会先打印哪一个里面的内容

51、clip 和background-clip（背景图片切割）

52、无限滚动，如何做优化
        不会一次性把数据渲染完全，而是只渲染可视区域，等向下滑动的时候，再追加一屏幕的数据上去。

53、websocket 接口数据会频繁跟新状态，这个时候肯定会有性能问题，这个时候怎么办？（定时处理）
        在websocket没有出现之前，基本上这种频繁的数据更新是通过长轮训来实现的，也就是不断的频繁的去请求接口拿回数据，但是这样会增加服务器端的压力，并且每一次的回来的数据并不意味着就是最新的数据。而websocket基本上就是为了解决长轮训的这种问题，使得我们可以在客户端进行实时通信。客户端和服务端，通过建立websocket通信，两端是可以直接进行交换数据的。而websocket基本上就是一个基于TCP/IP的协议，所以在数据传输的稳定性和数据量的方面比较有优势。
        如果频繁的拿回数据前端需要渲染，可以将数据累计到一定程度，再去渲染，操作DOM，比如一次性渲染5 条，10条。。

54、https://my.oschina.net/jsan/blog/741317


55、数据类型：基本数据类型 string、boolean 、number、null、undefined， es6新增的Symbol数据类型
                            引用数据类型：Object、Function、Array

56、定义一个变量不赋值，为什么是undefined
         因为js中，每一个变量有一个配置对象，配置对象会配置该变量包括初始值等的初始属性， 而unddefined就是配置对象里面的默认值

57、 es6 bind 自己实现个方法呢？
        
58、绑定this的几个方法？call、apply、bind, 有什么区别？
        （1）、call（this，a，b，c）；apply（this，【a，b，c】）；bind（XXX），把东西绑定到xxx上，并返回一个对象

59、变量与对象的区别？

60、描述new一个对象的过程？自己写一个函数来实现new的过程呢？
        创建一个对象 => this指向这个对象 => 执行代码，给this赋值 => 返回 this

61、一个瞎子，如何把52张牌中，有10张牌向上的，分为两堆，并保证两堆牌中的正面向上的牌的数量是一致的呢？

62、在一个生序数组中，如何优化快速的查找，两个值和为K的这两个值。中间有哪些需要优化
        例如：array = [1，2，3，4，6，7，8，9，10，11，12，13，14，15]， k = 15, 因为 1 + 14 = 15， 所以可得出结果

63、ant-design 的盒子模型是怎么样的？

64、你所在的项目组，下了一个订单，是如何与其他端进行通信的呢？

65、有没有考虑过，如何防止客户恶意下单？比如通过扫码点餐这种，用户把二维码保存下来，在屋头恶意下单？
        （1）、内网实现，只有用店铺自己的Wi-Fi才能点餐成功
        （2）、加一层地理位置的控制，如果不在该店铺内，不能点单成功
        （3）、进门扫签到码，关注公众号。只有扫了码之后的才能正常点餐
        （4）、实行动态码，扫过一次即作废
        （5）、一桌多单，是先付钱再吃饭；一桌一单，会有锁单机制

66、你们所开发的点餐系统实时性还是挺高的，是如何做的？（websocket）
        （1）、消息推送太多，固定一个时间差，来进行渲染

67、你们是如何做高并发的控制的？
        后端服务器，开启多线程服务，把所有消息分块似得堆放到kafafa中。

68、什么是敏捷开发？你在当中充当什么样的角色？
        敏捷开发，基本上就是一个迭代的，渐进式的开发过程。项目会在初期被分为多个子任务，每个任务经过开发、测试等流程具备可视、可集成和可运行使用的特征。

69、当你发现有错误的时候，你会去如何沟通？

70、如何快速得出一个字符串中出现次数最多的字符，大概只循环一次

71、es6中，class 和 extend 有什么关系？

72、你们项目中用的webpack是哪个版本？有没有关注过新版本那些？

73、项目中react用的什么版本？新版本的react新增了哪些东西？你比较关注哪一部分？
        （1）、WeChat  react-v15.3.0 版本, web pack -v3.8.0版本；WeChat2.0 react- v15.6.1. web pack-v3.0.0
        （2）、最新web pack -v4.28.2.  react-v16.6
        （3）、新版本的react增加了
                        Ref   以前是使用字符串，现在尽量用回掉函数
                        context  跨组件通信
                        React.PurComponent  默认新增了浅比较
                        Fragments.  可以定义返回数组和字符串
                        Portals   支持声明性的将子树渲染到另一个DOM节点上

74、你比较关注公司的哪一方面？你会着重考虑哪些东西，在办公环境中；

75、箭头函数与普通函数的区别？
        （1）、this的指向，普通函数是指向调用该函数的对象，箭头函数是指向外层的作用域
        （2）、箭头函数不绑定arguments，而是使用reset参数
        （3）、箭头函数不能作为构造函数，也没有原型

76、渐进增强和优雅降级

77、什么是SEO？

78、浏览器同源策略？

79、异步编程（回调函数、事件监听、发布/订阅、Promise对象）
        回调函数，会导致多层嵌套，代码横向发展，乱成一团，无法管理，这种情况称为’回调用函数噩梦’；
        promise，就是为了解决回调函数噩梦这一现象的，允许代码纵向发展，但是代码冗余，一堆 then ，原来的语义变得不清楚了；
        generator  函数，可以让代码交出函数的控制权，一个generator函数，就是一个封装的异步任务，需要暂停的地方，用 yield 来标注，调用next一次就执行一次
        async/await  主要是用来解决异步流程问题的，避免回调地狱情况的。

80、捕获异常问题

81、描述一下DNS解析过程

82、前端需要注意哪些SEO？
        （1）、合理的title、description、keywords
        （2）、重要的内容不用JS输出，因为爬虫不会执行JS获取内容
        （3）、如果图片不是单纯的装饰图片，必须添加alt
        （4）、重要的HTML放再起那么，因为爬虫重是从上到下开始搜索的
        （5）、使用语义化的HTML代码，符合W3C标准
        （6）、提高网站速度
        （7）、不要使用iframe标签，搜索引擎抓取不到

88、HTTP method都有哪些，有什么区别？
        （1）、safe methods
        （2）、idempotent methods
        （3）、options
        （4）、GET
        （5）、POST
        （6）、HEAD
        （7）、PUT
        （8）、delete
        （9）、tract
        （10）、connect

89、性能优化，前端 / 非前端？

90、HTTP状态码以及含义？

91、从浏览器输入url到显示页面的步骤？

92、数据结构，数组、链表、二叉树、堆、栈、队列？

93、谈谈grunt、gulp、webpack的区别？

94、TCP三次握手机制，TCP和UDP有什么区别？

95、森马是渐进增强和优雅降级？

96、常见的web安全问题以及防护原理？

97、了解HTML5新特性，新api有哪些？

98、HTTP和HTTPS，为什么HTTPS更加安全呢？

99、HTTP2的了解程度？

100、请描述一下，cookies、session Storage、local Storage的区别？

101、谈谈对node的理解，他与传统服务器最大的区别是什么？适用的场景有哪些？

102、谈谈对前端发展史的掌握，谈谈前端工程化的理解？

103、谈谈对前端自动化构建工具的理解，gulp和webpack的区别是什么？

104、解释器和编译器语言的区别和利弊？JIT（just-in-time）的特点是什么？

105、css选择器有哪些？选择器的权重，如何计算？

106、盒子模型，标准盒子模型和怪异盒子模型？

107、如何实现水平居中和垂直居中，尽可能多的办法？

108、对css3的了解，新特性？

109、css清除浮动的几种方法？

110、作用域、作用域链；原型、原型链；this、闭包？

111、前端跨域有哪些解决方案，实战过哪些方案？

112、JS实现继承的6中方式是什么？

113、es6的掌握情况？

114、MVC、MVVM的理解，angular、vue、react的认识？

115、JS引擎执行队列，微任务、宏任务？

116、JS垃圾回收方法有哪些？引用计数、标记清零？

117、前端缓存的掌握，etag、expirse、cache-control？

118、JS延迟加载有哪些方法，defer和asyn的区别？

119、什么是事件委托？用的什么原理来实现的？

120、loader和plugin的区别？

121、sass中，include和extend的区别？编译出来的代码有什么不同？

122、高清屏幕方案，css如何实现？

123、高清屏幕为什么会有1px显示2px？为什么会这样？

124、手机的一个input框，点击的时候弹出键盘，怎么避免被顶上去看不见？

125、做一个banner，用left 和 transform的区别？

126、react中setState做了什么？

127、如何封装一个组件，如何避免样式全局污染？命名空间，shadow dom隔离释义，知道否？

128、组件css，如何适应不同屏幕rem，如何配置root font-size，避免别人重写呢？

129、viewport ，像素比...？

130、箭头函数 this 的指向？

131、手写一个bind函数？

132、国际化打包的时候如何避免数据过多？

133、HTTP2.0有哪些新东西？

134、Ajax和fetch 的区别，fetch如何实现跨域？

135、setState的过程，为什么要这样做？