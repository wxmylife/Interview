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
    请求行 --- GET /users HTTP/1.1
    请求头 --- Host: api.xxx.com
          --- Content-Type: text/plain
          --- Content-Length: 234
    请求体 --- body
    ```
  * 报文格式: Response
    > 状态行: HTTP version + status code + status message
    
    ```
    状态行 --- HTTP/1.1 200 OK
    响应头 --- content-type: application/json; charset=utf-8
          --- cache-control: public, max-age=60, s-message=60
          --- vary: Accept,Accept-Encoding
          --- etag: xxx
          --- content-encoding: gzip
    响应体 --- json
    ```
  
  ---
  
## 重要内容
  
  * Request method
    * GET
      > 获取资源；没有 Body
    * POST
      > 增加或者修改资源；有 Body
    * PUT
      > 修改资源；有 Body；幂等（多次调用和一次调用相同）
    * DELETE
      > 删除资源；没有 Body 幂等
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
  * Body
