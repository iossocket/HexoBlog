---
title: Network Security
date: 2016-09-05 16:52:17
tags:
---
iOS 为了有效的减少入侵的肯能在网络层，限制了端口，并且移除了 不需要的网络工具，例如 telnet, shell, web server, 无需额外的的防火墙软件在iOS设备上。

### TLS
iOS 支持Transport Layer Security (TLS v1.0, TLS v1.1, TLS v1.2) 和 DTLS，Safari，Calendar，等系统app默认使用了这些机制来保证网络的加密通信。高级API（如CFNetwork）易于采用TLS，底层API
