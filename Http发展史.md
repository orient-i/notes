### 什么是 HTTP

[MDN](https://developer.mozilla.org/zh-CN/docs/Web/HTTP)定义：超文本传输协议（HTTP）是一个用于传输超媒体文档（例如 HTML）的[应用层](https://zh.wikipedia.org/wiki/%E5%BA%94%E7%94%A8%E5%B1%82)协议。它遵循经典的[客户端-服务端模型](https://zh.wikipedia.org/wiki/%E4%B8%BB%E5%BE%9E%E5%BC%8F%E6%9E%B6%E6%A7%8B)，客户端打开一个连接以发出请求，然后等待直到收到服务端响应。HTTP 是[无状态协议](http://zh.wikipedia.org/wiki/%E6%97%A0%E7%8A%B6%E6%80%81%E5%8D%8F%E8%AE%AE)，这意味着服务器不会在两个请求之间保留任何数据（状态）。

### HTTP 的诞生

1989 年 3 月 12 日，CERN（欧洲核子研究组织）的 Tim Berners-Lee 博士为方便学术研究，提出了一种能让远隔两地的研究者们共享知识的设想。这个设想最初的基本理念是：借助多文档之间相互关联形成的超文本（HyperText），连成一个可以互相参阅的信息管理系统。  
1989 年 11 月中旬，Tim Berners-Lee 博士通过互联网实现了超文本传输协议（HTTP）客户端和服务器之间的首次成功通信。  
1990 年，在项目实施的实施过程中，系统命名由原来的 _Mesh_ 被更改为*万维网*（World Wide Web）。  
1991 年 8 月 16 日，Tim Berners-Lee 博士在公开的超文本新闻组上发表的[文章](https://www.w3.org/People/Berners-Lee/1991/08/art-6484.txt)被视为万维网公共项目的开始。  
<img src=https://cdn.britannica.com/94/123894-050-53EC378E/Tim-Berners-Lee-2005.jpg width=30% alt="Tim Berners-Lee"/>

### HTTP/0.9

由于 HTTP 初衷只是为了学术共享，只需要传输体积很小的 HTML 文件，所以最早版本的 HTTP/0.9 极其简单。这个版本下的请求只由一行指令构成，以唯一可用的请求方法 GET 开头，后面再跟目标资源的请求 URI。

`GET /mypage.html`

服务器的响应也很简单，只包含请求的资源。

```
<html>
  这是一个非常简单的 HTML 页面
</html>
```

![HTTP/0.9](https://static001.geekbang.org/resource/image/db/34/db1166c68c22a45c9858e88a234f1a34.png?wh=1142*309)  
由于 HTTP/0.9 的响应内容除了资源（HTML 文件）本身之外，再不包含其他内容，没有什么所谓的状态码或者错误代码。出现问题时，一个特殊的包含问题描述信息的 HTML 文件将被发回，供人查看。

### HTTP/1.0

1993 年 1 月，现代浏览器的祖先 NCSA （美国国家超级计算机应用中心）研发的 Mosaic 问世。它以 in-line 等形式将图像和文本一起显示出来，而不是在单独的窗口另外显示图像，图像方面出色的表现让它迅速在世界范围内流行开来。  
![NCSA Mosaic](https://upload.wikimedia.org/wikipedia/commons/e/ea/NCSA_Mosaic_Browser_Screenshot.png)  
1994 年 12 月，网景公司发布了 Netscape Navigator 1.0，1995 年微软公司发布了 Internet Explorer 1.0 和 2.0，两家公司都各自对 HTML 做了扩展。同年 4 月，Web 服务器标准之一的 Apache 发布了首个公开版本 0.6.2，同年 11 月 HTML 2.0 版本发布。这一年，Web 技术的发展突飞猛进。  
Web 技术的高速发展带来了许多新的需求，例如浏览器中展示的内容不再只是 HTML 文件，还包含 JavaScript、CSS、图片、音频、视频等各种不同类型的文件，只能传输 HTML 文件的 HTTP/0.9 已经不再满足新兴网络的发展。  
1996 年 5 月，HTTP/1.0 发布。

相对于 HTTP/0.9，HTTP/1.0 的变化主要在以下几点：

- 提出了状态码的概念。状态码会在响应开始时发送，使浏览器能够了解请求是否执行成功，并根据状态码相应地调整行为（例如更新或者直接使用本地缓存、重定向等等）。
- 引入了 HTTP 标头。在请求和响应信息中新增了用来描述元数据的请求头和响应头，用以帮助客户端和服务器更好地进行数据交互。例如前面提到的“多种类型的文件传输”场景，作为 HTTP/1.0 的核心诉求之一，HTTP/1.0 可以通过请求头中的 `accept`、`accept-encoding`、`accept-Charset` 字段来告诉服务器，客户端所期望资源的类型、压缩方式和编码格式。此外，HTTP 标头也使得协议变得更加灵活，易于扩展。后续若是再次修订版本，只需要往 HTTP 标头中添加新的元数据字段即可。
- 引入 Cache 机制。为减轻服务器的压力，HTTP/1.0 首次引入了 Cache 机制用来缓存已经下载过的资源。

3. Http 各个版本的定义、解决的问题、带来的问题

### 参考资料

https://httpd.apache.org/ABOUT_APACHE.html
