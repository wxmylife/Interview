# [登录和第三方授权](登录和第三方授权)
 
## Cookie
  1. Cookie 的工作机制
    > 客户端和服务端共同配合的信息存储机制
    * 客户端通过Http Header Cookie 传递参数
    * 服务端处理数据后通过 Header:Set-Cookie 将结果返回客户端

  2. Cookie 的作用
    * 会话管理: 登录状态(Session:Id)、购物车等
    * 个性化: 用户偏好、主题
    * Tracking: 分析用户行为
    * XSS (Cross-site scripting): HttpOnly Set-Cookie: session_id=123;HttpOnly(任何 JavaScript 拿不到 Cookie)
      > 跨站脚本攻击
      ``` 
      Set-Cookie: session_id=123;HttpOnly(任何 JavaScript 拿不到 Cookie)
      ```
    * XSRF (Cross-site request forgery): Referer
      > 跨站请求伪造

## Authorization
  1. Basic
    > Authorization: Basic <username:password(Base64ed)>
    ```
      GET /user HTTP/1.1
      Host: xxx.com
      Authorization:Basic xxxxxx
      401: 授权失败
    ```
  2. Bearer
    > Authorization: Bearer <bearer token>
    * OAuth2
      * OAuth2 流程
        ```
        GET /user HTTP/1.1
        Host: github.com
        Authorization:Bearer xxxxxx
        ```
      * 微信登录
    * App 中的 Bearer token
    * refresh token
      ```
      {
        "token_type":"Bearer",
        "access_token":"xxxx",
        "refresh_toke":"xxxx",
        "expires_time":"xxxx"
      }
      ```
