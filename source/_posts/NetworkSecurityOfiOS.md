---
title: Network Security
date: 2016-09-05 16:52:17
tags:
---
iOS 为了有效的减少入侵的肯能在网络层，限制了端口，并且移除了 不需要的网络工具，例如 telnet, shell, web server, 无需额外的的防火墙软件在iOS设备上。

### TLS
iOS 支持Transport Layer Security (TLS v1.0, TLS v1.1, TLS v1.2) 和 DTLS，Safari，Calendar，等系统app默认使用了这些机制来保证网络的加密通信。高级API（如CFNetwork）可以让我们很方便的引入TLS，底层API（ [SecureTransport](https://developer.apple.com/library/mac/documentation/Security/Reference/secureTransportRef/)）对于TLS提供了更细颗粒度的控制。

#### App Transport Security
当前若不做特殊处理，我们默认需要满足App Transport Security提出了安全需求，最好使用如下API进行网络连接：NSURLConnection、CFURL、NSURLSession。我们的服务器端也至少需要支持TLS1.2。
对于iOS9，默认是需要满足App Transport Security的要求，如需要修改其默认要求，需要在info.plist中复写App Transport Security。

### VPN
iOS的VPN配置，可以分为不同维度安全连接保证，例如：全局开启、针对某个App开启、针对某个域名开启。

### Wi-Fi
