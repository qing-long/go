# Go

![5c986fcb1f09a](assets/5c986fcb1f09a.png)

## 环境

- mac os 上安装go

```bash
brew install go

# ~/.zshrc 或者 ~/.bashrc 里面加入
export GOPATH=$HOME/go

source ~/.zshrc
```

- 国内不挂代理下载如`golang/x/net`包

```bash
export GOPROXY=https://goproxy.io

go get package
```

- 使用go mod 方式

```bash
export GO111MODULE=on

# 初始化项目
go mod init package-name

# 下载依赖
go mod download
```

## 类型

## 语法

## 进阶


