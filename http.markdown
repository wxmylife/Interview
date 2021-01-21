# HTTP的概念、原理、工作机制、数据格式和 REST

## Http 是什么

> * 两种最直观的的印象
>   * 游览器地址栏输入地址，打开网页
>   * Android 中发送网络，返回对应内容
> * HyperText Transfer Protocal 超文本传输协议

 ### HTTP 报文 协议类型:服务器地址/路径
 
 #### 请求报文
  * 报文格式: Request
    > 请求行: Method + Path + HTTP version
    
    ```
    请求行   --- GET /users HTTP/1.1
    Headers --- Host: api.xxx.com
            --- Content-Type: text/plain
            --- Content-Length: 234
    Body    --- body
    ```
  * 报文格式: Response
    > 状态行: HTTP version + status code + status message
    
    ```
    状态行   --- HTTP/1.1 200 OK
    Headers --- content-type: application/json; charset=utf-8
            --- cache-control: public, max-age=60, s-message=60
            --- vary: Accept,Accept-Encoding
            --- etag: xxx
            --- content-encoding: gzip
    Body    --- json
    ```
  
  ---
  
## 重要内容
  
  * Request method
    * GET
      > 获取资源；没有 Body；幂等（即反复调用多次时会得到相同的结果）
    * POST
      > 增加或者修改资源；有 Body
    * PUT
      > 仅用于修改资源；有 Body；幂等（多次调用和一次调用相同）
    * DELETE
      > 删除资源；没有 Body；幂等
    * HEAD
      > 获取信息（文件下载使用，获取文件信息）
  * Response status code
    > 作用: 对结果做出类型化描述（如'获取成功'、'内容未找到'等）
    
    * 1xx: 临时性消息（101: HTTP 协议改变,支持 HTTP2；100:请继续发送）
    * 2xx: 成功
    * 3xx: 重定向
    * 4xx: 客户端错误
    * 5xx: 服务端错误 
  * Headers
    > 作用: HTTP消息的元数据(metadata)
    
    * Host
      > 服务器主机地址
    * Content-Type / Content-Length
      > 内容的类型 / 内容的长度（字节）
      
      * text/html 
        > html 文本,用于游览器页面响应
        
      * application/x-www-form-urlencoded
        > 普通表单,encoded URL 格式

      * multipart/form-data
        > 多部分形式，一般用于传输包含二进制内容的多项内容

      * application/json
        > json 形式，用于 Web Api 的响应或 POST/PUT 请求
      
      * image/jpeg / application/zip ...
        > 单文件，用于 Web Api 响应或 POST/PUT 请求 

    * Location
      > 重定向的目标 URL

    * User-Agent
      > 用户代理
      
    * Range / Accept-Range
      > 指定Body 的内容范围
    
    * Cookie / Set-Cookie
      > 发送 Cookie / 设置 Cookie
      
    * Authorization
      > 授权信息
      
    * Chunked Transfer Encoding 
      > 分块传输编码，用于多线程下载，断点续传
    
      * Transfer-Encoding: chunked
      * 表示 Body 长度无法确定，Content-Length 不能使用
      * Body 格式如下:
        ```
        <length 1>
        <data 1>
        <length 2>
        <data 2>
        0
        (最后传输0表示内容结束)
        ```
      * 目的：在服务器还未获取完整内容时，更快对客服端做出响应，减少用户等待 
    
    * Accept
    > 客服端能接受的数据类型，如 text/html

    * Accept-Charset
    > 客户端接受的字符集，如 utf-8
    
    * Accept-Encoding
    > 客户端接受的压缩编码类型，如 gzip
      
    * Content-Encoding
    > 压缩类型，如 gzip
  * Cache
    * Cache 和 Buffer 的区别
    > 缓存 和 缓冲
    
    * Cache-Control
      > 服务器通知客户端缓存策略
      
      * no-cache
      > **缓存但重新验证**:每次有请求发出时，缓存会将此请求发到服务器（该请求应该会带有与本地缓存相关的验证字段），服务器端会验证请求中所描述的缓存是否过期，若未过期（注：实际就是返回304），则缓存才使用本地缓存副本。 
      * no-store
      > **没有缓存**:缓存中不得存储任何关于客户端请求和服务端响应的内容。每次由客户端发起的请求都会下载完整的响应内容。
      * max-age
      > **可以缓存**:根据失效日期决定，可在失效日期之前使用
      * private / public 
      > 私有缓存和公共缓存
    * Last-Modified 
      > 资源上次修改的时间

      * If-Modified-Since 
      > 资源是否在上次时间点之后没有改过，使用 Cache,如果有改过则返回新资源
    * Etag
      * If-None-Match
      > 咨询快照是否使用，不能使用则返回新数据
      
### RESTful HTTP
  > 正确使用 HTTP

