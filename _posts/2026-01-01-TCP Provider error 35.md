---
title: "A connection was successfully established with the server, but then an error occurred during the pre-login handshake. (provider: TCP Provider, error: 35 - An internal exception was caught)"
categories:
  - Docker
tags:
  - Docker
---

 

### 方法一：

可在Dockerfile中添加以下代码：

```
RUN sed -i 's/TLSv1.2/TLSv1/g' /etc/ssl/openssl.cnf
```

### 方法二：

编辑容器里的 /etc/ssl/openssl.cnf 文件，文件最后修改为：

```
MinProtocol = TLSv1

CipherString = DEFAULT@SECLEVEL=1
```