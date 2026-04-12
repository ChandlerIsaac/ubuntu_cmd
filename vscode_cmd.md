# 网络相关问题

## 连接远程服务器

### VS Code 使用 Codex 插件通过 SSH 连接远程服务器

方法来自 [CSDN Codex远程服务器登录错误：Token exchange failed: token endpoint returned status 403 Forbidden](https://blog.csdn.net/Jspb_LIu/article/details/157511783)

方法思路：远程服务器上没有安装 VPN 等相关软件，将服务器的 `17890` 端口请求发送到本地电脑的 `7890` 端口，本地再通过相关 VPN 软件连接外网。

1. 打开本地 VS Code 的 SSH 配置文件：

   ```bash
   Host 4090
   HostName xxx.cn
   Port 2223
   User x
   RemoteForward 17890 127.0.0.1:7890
   ```

   `RemoteForward 17890 127.0.0.1:7890` 表示在远程服务器上开一个 `17890` 端口，把这个端口收到的流量通过 SSH 隧道转发到本地电脑的 `127.0.0.1:7890`。

2. 远程配置：

   在 VS Code 客户端使用 `Ctrl+Shift+P`，搜索 `Preferences: Open Remote Settings (JSON)`，添加：

   ```bash
   {
       "http.proxy": "http://127.0.0.1:17890",
       "https.proxy": "http://127.0.0.1:17890",
       "http.proxySupport": "override"
   }
   ```

3. 测试：

   在远程服务器控制台输入：

   ```bash
   curl --proxy http://127.0.0.1:17890 https://www.google.com
   ```

   能得到响应则配置成功。

4. 在 VS Code 的 Codex 插件中登录 ChatGPT 账号。
