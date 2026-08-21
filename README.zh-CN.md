[English](./README.md) | 中文

## 第一步 — 安装 mkcert 并生成证书

```bash
# 以下脚本适用于 Windows
# 安装 mkcert
winget install FiloSottile.mkcert

# 将本地 CA 安装到 Windows 证书信任链（仅需执行一次）
mkcert -install

# 在项目根目录执行，证书输出至 nginx/certs/
mkcert -cert-file nginx/certs/cert.pem -key-file nginx/certs/key.pem vaultwarden.local localhost 127.0.0.1
```

## 第二步 — 配置 hosts 文件

添加以下一行：

```
127.0.0.1  vaultwarden.local
```

## 第三步 — 启动服务

```bash
docker compose up -d
```

## 第四步 — 配置浏览器插件

在 Bitwarden chrome插件的自托管服务器地址栏中填写以下 URL。

```
https://vaultwarden.local:18443
```

> **注意：** 使用 `18443` 和 `1880` 端口是因为 Docker Compose 的端口映射有意避开了标准端口 `80` 和 `443`。