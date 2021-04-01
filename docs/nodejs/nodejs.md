# Node.js 入门

> Node.js 是一个能够在服务器端运行 JavaScript 源代码的跨平台运行环境。
>
> 关键词： `nodejs`

<!-- TOC depthFrom:2 depthTo:3 -->

- [Node.js 工具](#nodejs-工具)
  - [nvm](#nvm)
- [引用和引申](#引用和引申)
  - [官方资源](#官方资源)
  - [教程](#教程)
  - [工具](#工具)
  - [资源收集](#资源收集)

<!-- /TOC -->

## Node.js 简介

简单的说，`Node.js` 就是运行在服务端的 JavaScript。

`Node.js` 是一个基于 Chrome JavaScript 运行时建立的一个平台。

`Node.js` 是一个事件驱动 I/O 服务端 JavaScript 环境，基于 Google 的 V8 引擎，V8 引擎执行 Javascript 的速度非常快，性能非常好。

## Node.js 工具

### nvm

[Nvm](https://github.com/creationix/nvm) 是一个简单的 bash 脚本工具，用来管理 `node.js` 版本。

它可以在同一台机器上安装多个 `Node.js` 版本，并灵活的切换版本。

安装

```sh
# 两条命令效果相同
wget -qO- https://raw.githubusercontent.com/creationix/nvm/v0.33.11/install.sh | bash
curl -o- https://raw.githubusercontent.com/creationix/nvm/v0.33.11/install.sh | bash
```

设置环境变量

```sh
export NVM_DIR="${XDG_CONFIG_HOME/:-$HOME/.}nvm"
[ -s "$NVM_DIR/nvm.sh" ] && \. "$NVM_DIR/nvm.sh"
```

使用

```sh
nvm install 6.14.4  # 安装 Node.js 版本
nvm use node6.14.4  # 指定 Node.js 版本（必须已安装）
```

## 引用和引申

> 👉 欢迎阅读 [我的前端技术教程系列：frontend-tutorial](https://github.com/dunwu/frontend-tutorial)

### 官方资源

- [Node.js 官网](https://nodejs.org/zh-cn/)
- [Node.js Github](https://github.com/nodejs/node)

### 教程

- [Node.JS 最佳实践](https://github.com/i0natan/nodebestpractices)
- [Node.js 包教不包会](https://github.com/alsotang/node-lessons)
- [一起学 Node.js](https://github.com/nswbmw/N-blog)
- [七天学会 NodeJS](https://github.com/nqdeng/7-days-nodejs)

### 工具

- [nvm](https://github.com/creationix/nvm) - Node 版本管理器

### 资源收集

- [awesome-nodejs](https://github.com/sindresorhus/awesome-nodejs) - Node.js 资源收集
