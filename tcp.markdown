# TCP/IP 和 HTTPS 详解
> 一系列协议所组成的一个网络分层模型

## TCP/IP
> 分层原因:实现网络的不可靠性

* 分层
  * Application Layer 应用层：HTTP、FTP、DNS
  * Transport Layer 传输层：TCP、UDP
  * Internet Layer 网络层：IP
  * Link Layer 数据链路层：以太网、Wi-Fi

```flow
st=>start: Start
op=>operation: 应用层 HTTP SSL TLS DNS
op1=>operation: 传输层 TCP UDP
op2=>operation: 网络层 IP
op3=>operation: 数据链路层 WIFI 以太网
e=>end
st->op->op1->op2->op3->e
```
* TCP 连接
> HTTP 无状态，TCP 有状态，建立连接后才能通信

  * 连接：三次握手
  * 关闭：四次挥手

## HTTPS

* HTTP Secure / HTTP over  SSL / HTTP over TLS
* SSL: Secure Socket Layer **安全套接层** -> TLS Transport Layer Security **安全传输层协议**
* 定义: 在 HTTP 之下增加的一个安全层，用于保障 HTTP 的加密传输
* 本质: 在客户端和服务器之间用非对称加密协商出一套对称秘钥，每次发送信息之前将内容加密，收到之后解密，达到内容的加密传输

### HTTPS 连接

* 客户端请求建立 TLS 连接
* 服务器发回证书
* 客户端验证服务器证书
* 客户端信任服务器后，和服务器协商对称秘钥
* 使用对称秘钥开始通信

![连接过程](images/banner_example.gif)
  
