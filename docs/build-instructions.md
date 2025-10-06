# CLI Proxy API 构建说明

## 环境要求

- Go 1.24 或更高版本
- 网络连接（用于下载依赖包）

## 构建步骤

### 1. 安装 Go

如果您的系统中没有安装 Go，请先安装：

```bash
# 使用 Homebrew (macOS)
brew install go

# 或使用其他方式安装 Go 1.24+
```

验证 Go 安装：
```bash
go version
```

### 2. 配置 Go 代理（可选，但推荐在中国地区）

如果遇到依赖包下载问题，可以配置 Go 代理：

```bash
go env -w GOPROXY=https://goproxy.cn,direct
```

### 3. 构建项目

在项目根目录下执行以下命令：

```bash
go build -o cli-proxy-api ./cmd/server
```

### 4. 验证构建结果

构建成功后，会在当前目录生成 `cli-proxy-api` 可执行文件：

```bash
ls -la cli-proxy-api
```

验证可执行文件是否正常：

```bash
./cli-proxy-api --help
```

## 故障排除

### 网络问题

如果构建过程中出现网络超时错误，如：
```
dial tcp 142.250.73.13:443: i/o timeout
```

请按照第2步配置 Go 代理，然后重试构建。

### 依赖包问题

如果遇到依赖包下载问题，可以尝试：

```bash
# 清理 Go 模块缓存
go clean -modcache

# 重新构建
go build -o cli-proxy-api ./cmd/server
```

## 运行

构建完成后，可以通过以下命令启动服务器：

```bash
./cli-proxy-api
```

默认情况下，服务器将在 8317 端口上运行。

如需查看所有可用选项：

```bash
./cli-proxy-api --help