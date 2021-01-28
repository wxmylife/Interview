# TCP/IP 和 HTTPS 详解
> 一系列协议所组成的一个网络分层模型

## TCP/IP
> 分层原因:实现网络的不可靠性

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

## HTTPS
