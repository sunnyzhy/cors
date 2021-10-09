# CORS

CORS 全称是"```跨域资源共享```"(```Cross-origin resource sharing```)。

跨源资源共享 (CORS) 是一种基于 HTTP 头的机制，该机制通过允许服务器标示除了它自己以外的其它 origin（域、协议和端口），这样浏览器可以访问加载这些资源。

跨源资源共享还通过一种机制来检查服务器是否会允许要发送的真实请求，该机制通过浏览器发起一个到服务器托管的跨源资源的 OPTIONS "预检"请求。在预检中，浏览器发送的头中标示有 HTTP 方法和真实请求中会用到的头。

## 同源策略

1. 同源策略 SOP（Same origin policy）是一种约定，它是浏览器最核心也最基本的安全功能，如果缺少了同源策略，浏览器很容易受到 XSS、CSFR 等攻击。
2. 所谓同源是指 ```协议 + 域名 + 端口``` 三者相同
   |URL|结果|原因|
   |--|--|--|
   |```http://store.company.com/dir2/other.html```|同源|只有路径不同|
   |```http://store.company.com/dir/inner/another.html```|同源|只有路径不同|
   |```https://store.company.com/secure.html```|失败|协议不同|
   |```http://news.company.com/dir/other.html```|失败|域名不同|
   |```http://store.company.com:81/dir/etc.html```|失败|端口不同|
3. 同源策略限制以下几种行为：
   - Cookie、LocalStorage 和 IndexDB 无法读取
   - DOM 和 Js 对象无法获得
   - AJAX 请求不能发送

## 为何会跨域

同源指的是 ```域名、协议、端口``` 都相同。如果其中有一个不同，浏览器就会认为不同源，也就是跨域。
