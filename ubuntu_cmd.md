# 网络

## 配置当前终端使用代理网络下载相应的资源

```bash
export http_proxy=http://127.0.0.1:7890
export https_proxy=http://127.0.0.1:7890
```

## 将本地端口与服务器端口打通

```bash
ssh -L 本地端口:目标地址:目标端口 服务器用户名@服务器IP
# 示例
ssh -L 6006:localhost:6006 l@isaacyy.cn
```

# 存储

## 查看当前文件夹存储

```bash
du -sh *
```

# Git

## 第一次使用配置

设置 GitHub 账号：

```bash
git config --global user.name "name"
git config --global user.email "email"
```

SSH 密钥并配置到 GitHub：

1. 生成 SSH 密钥

   ```bash
   ssh-keygen -t ed25519 -C "GitHub邮箱"
   ```

2. 查看并复制公钥

   ```bash
   cat ~/.ssh/id_ed25519.pub
   ```

3. 把公钥粘贴到 GitHub

   打开 `GitHub` 的 `SSH and GPG keys`，创建新的 SSH 密钥。

## clone

打开要克隆到本地的文件夹后执行：

```bash
git clone git@github.com:ChandlerIsaac/ubuntu_cmd.git
```

## push

```bash
git status
git add .
git commit -m "本次修改说明"
git push
```

## pull

下载最新代码：

```bash
git pull
```

## git checkout

回到指定版本：

```bash
git checkout commit编号
```

回到最新版本：

```bash
git checkout main
```

## git reset

彻底重置到指定版本（**危险！会覆盖当前代码**）：

```bash
git reset --hard commit编号
```
