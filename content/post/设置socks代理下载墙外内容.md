​	





## 使用socks连接VPN代理服务下载ntlk的包内容等

```python
import socket
import socks

# 设置 SOCKS 代理
socks.set_default_proxy(socks.SOCKS5, "127.0.0.1", 10793)
socket.socket = socks.socksocket

```

