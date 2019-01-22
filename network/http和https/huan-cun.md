## http/https 缓存
1：web缓存的实现

web缓存：

WEB缓存(cache)位于Web服务器和客户端之间。

缓存会根据请求保存输出内容的副本，例如html页面，图片，文件，当下一个请求来到的时候：如果是相同的URL，缓存直接使用副本响应访问请求，而不是向源服务器再次发送请求。

HTTP协议定义了相关的消息头来使WEB缓存尽可能好的工作。如下图。

2：缓存的优点

减少延迟 减少网络带宽的消耗；

减少相应延迟：因为请求从缓存服务器(离客户端更近)而不是源服务器被相应，这个过程耗时更少，让web服务器看上去相应更快。

减少网络带宽消耗：当副本被重用时会减低客户端的带宽消耗;客户可以节省带宽费用，控制带宽的需求的增长并更易于管理。

3：与缓存相关的http扩展消息头

Expires：指示响应内容过期的时间，格林威治时间GMT

Cache-Control：更细致的控制缓存的内容  max-age就是确定缓存的时间。

Last-Modified：响应中资源最后一次修改的时间

ETag：响应中资源的校验值，在服务器上某个时段是唯一标识的。

Date：服务器的时间

If-Modified-Since：客户端存取的该资源最后一次修改的时间，同Last-Modified。

If-None-Match：客户端存取的该资源的检验值，同ETag。![](/assets/1016870-20170524204929497-1424374939.png)

4：缓存（cache）生效的过程

服务器收到请求时，会在200OK中回送该资源的Last-Modified和ETag头，客户端将该资源保存在cache中，并记录这两个属性。当客户端需要发送相同的请求时，会在请求中携带If-Modified-Since和If-None-Match两个头。两个头的值分别是响应中Last-Modified和ETag头的值。服务器通过这两个头判断本地资源未发生变化，客户端不需要重新下载，返回304响应。常见流程如下图所示：
![](/assets/wKiom1UHicXCwfANAAE4cmFXWn4730.jpg)

5：http的缓存机制

HTTP/1.1中缓存的目的是为了在很多情况下减少发送请求，同时在许多情况下可以不需要发送完整响应。前者减少了网络回路的数量;HTTP利用一个“过期(expiration)”机制来为此目的。后者减少了网络应用的带宽;HTTP用“验证(validation)”机制来为此目的。

HTTP定义了3种缓存机制：

1)Freshness：允许一个回应消息可以在源服务器不被重新检查，并且可以由服务器和客户端来控制。例如，Expires回应头给了一个文档不可用的时间。Cache-Control中的max-age标识指明了缓存的最长时间;

2)Validation：用来检查以一个缓存的回应是否仍然可用。例如，如果一个回应有一个Last-Modified回应头，缓存能够使用If-Modified-Since来判断是否已改变，以便判断根据情况发送请求;

3)Invalidation： 在另一个请求通过缓存的时候，常常有一个副作用。例如，如果一个URL关联到一个缓存回应，但是其后跟着POST、PUT和DELETE的请求的话，缓存就会过期。

6：断点续传和多线程下载的原理

（一）HTTP协议的GET方法，支持只请求某个资源的某一部分;

206 Partial Content 部分内容响应;

Range 请求的资源范围;

Content-Range 响应的资源范围;

在连接断开重连时，客户端只请求该资源未下载的部分，而不是重新请求整个资源，来实现断点续传。

（二）分块请求资源实例：

Eg1：Range: bytes=306302- ：请求这个资源从306302个字节到末尾的部分;

Eg2：Content-Range: bytes 306302-604047/604048：响应中指示携带的是该资源的第306302-604047的字节，该资源共604048个字节;

客户端通过并发的请求相同资源的不同片段，来实现对某个资源的并发分块下载。从而达到快速下载的目的。目前流行的FlashGet和迅雷基本都是这个原理。

多线程下载的原理：

下载工具开启多个发出HTTP请求的线程;

每个http请求只请求资源文件的一部分：Content-Range: bytes 20000-40000/47000;

合并每个线程下载的文件。

7：https

HTTPS(全称：Hypertext Transfer Protocol over Secure Socket Layer)，是以安全为目标的HTTP通道，简单讲是HTTP的安全版。即HTTP下加入SSL层，HTTPS的安全基础是SSL，因此加密的详细内容请看SSL。

见下图：

![](/assets/wKiom1UHifeDl4skAABktLVbDso348.jpg)

https所用的端口号是443。
