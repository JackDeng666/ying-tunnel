<h1 align="center">Ying Tunnel</h1>

## 简介

这是一个使用 ts 和 nodejs 实现的内网穿透服务与连接客户端，所有代码都在此仓库并以 pnpm 的 workspace 去管理。

## 直接使用

在服务器中安装 `ying-tunnel-server`

```bash
docker pull jackdeng666/ying-tunnel-server
```

### 作者开发环境版本

- node v18.18.2
- pnpm v8.15.6

## 其他

### 服务打包与本地启动

```bash
docker build --tag ying-tunnel-server:test --target server-runner .
```

```bash
docker run --name ying-tunnel-server -d \
  -p 5859:5859 \
  -p 4948:4948 \
  -p 3435:3435 \
  -e TUNNEL_SERVER_HOST=local.ying.top \
  -e TUNNEL_SERVER_PORT=4948 \
  -e PROXY_SERVER_PORT=3435 \
  -e ADMIN_SERVER_PORT=5859 \
  -e ADMIN_PASSWORD=123456 \
  ying-tunnel-server:test
```

### 发布 packages

```bash
pnpm build:packages
```

```bash
pnpm changeset add
pnpm changeset version
pnpm changeset publish
```