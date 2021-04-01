# Yarn 入门

> `Yarn` 是一个 `Node.js` 包管理器，比 `Npm` 更快，具有离线支持，并且更可预测地获取依赖关系。可以替代 npm 的功能。
>
> 关键词： `nodejs`, `包管理`, `yarn`

<!-- TOC depthFrom:2 depthTo:3 -->

- [1. 简介](#1-简介)
- [2. 安装](#2-安装)
- [3. Yarn 工作流](#3-yarn-工作流)
- [4. Yarn 常用命令](#4-yarn-常用命令)
  - [4.1. 初始化新项目](#41-初始化新项目)
  - [4.2. 添加依赖包](#42-添加依赖包)
  - [4.3. 更新依赖包](#43-更新依赖包)
  - [4.4. 删除依赖包](#44-删除依赖包)
  - [4.5. 安装依赖项](#45-安装依赖项)
- [5. 创建一个新项目](#5-创建一个新项目)
- [6. 配置文件](#6-配置文件)
- [7. 参考资料](#7-参考资料)

<!-- /TOC -->

## 1. 简介

**Yarn 是快速、可靠、安全的 js 包管理器。**

- **快速** - Yarn 会缓存它下载的每个包，所以无需重复下载。它还能并行化操作以最大化资源利用率，安装速度之快前所未有。
- **安全** - Yarn 会在每个安装包被执行前校验其完整性。
- **可靠** - Yarn 使用格式详尽而又简洁的 lockfile 文件和确定性算法来安装依赖，能够保证在一个系统上的运行的安装过程也会以同样的方式运行在其他系统上。

## 2. 安装

先决条件：已安装 Nodejs。

执行命令：`npm i -g yarn`

虽然还有其他安装方式，但并不推荐。

## 3. Yarn 工作流

Yarn 工作流：

1. 创建一个新项目
2. 增加／更新／删除依赖
3. 安装／重装你的依赖
4. 引入版本控制系统（例如 git）
5. 持续集成

## 4. Yarn 常用命令

**每个命令都会更新 `package.json` 和 `yarn.lock` 文件。**

### 4.1. 初始化新项目

```sh
yarn init
```

### 4.2. 添加依赖包

在使用一个包之前，你需要执行以下命令将其加入依赖项列表：

```sh
yarn add [package]
```

`[package]`会被加入到`package.json`文件中的依赖列表，同时`yarn.lock`也会被更新。

```diff
  {
    "name": "my-package",
    "dependencies": {
+     "package-1": "^1.0.0"
    }
  }
```

你可以用以下参数添加其它[类型](https://yarnpkg.com/zh-Hans/docs/dependency-types)的依赖：

- `yarn add --dev` 添加到 `devDependencies`
- `yarn add --peer` 添加到 `peerDependencies`
- `yarn add --optional` 添加到 `optionalDependencies`

通过指定[依赖版本](https://yarnpkg.com/zh-Hans/docs/dependency-versions)和[标签](https://yarnpkg.com/zh-Hans/docs/cli/tag)，你可以安装一个特定版本的包：

```sh
yarn add [package]@[version]
yarn add [package]@[tag]
```

`[version]` 或 `[tag]` 会被添加到 `package.json`，并在安装依赖时被解析。

例如：

```sh
yarn add package-1@1.2.3
yarn add package-2@^1.0.0
yarn add package-3@beta
{
  "dependencies": {
    "package-1": "1.2.3",
    "package-2": "^1.0.0",
    "package-3": "beta"
  }
}
```

**将依赖项添加到不同依赖项类别**

分别添加到 `devDependencies`、`peerDependencies` 和 `optionalDependencies`：

```sh
yarn add [package] --dev
yarn add [package] --peer
yarn add [package] --optional
```

### 4.3. 更新依赖包

```sh
yarn upgrade [package]
yarn upgrade [package]@[version]
yarn upgrade [package]@[tag]
```

这会更新`package.json`和`yarn.lock` 文件。

```diff
  {
    "name": "my-package",
    "dependencies": {
-     "package-1": "^1.0.0"
+     "package-1": "^2.0.0"
    }
  }
```

### 4.4. 删除依赖包

```
yarn remove [package]
```

这会更新`package.json`和`yarn.lock` 文件。

### 4.5. 安装依赖项

`yarn install` 是用于安装一个项目的所有依赖。 Yarn 会从 `package.json` 中读取依赖，并将依赖信息存储到 `yarn.lock` 中。

如果你正在开发一个包，通常你会在以下情况之后进行依赖安装：

- 你刚检出需要这些依赖项的项目代码。
- 项目的另一个开发者添加了新的依赖，你需要用到。

有很多参数可以控制依赖安装的过程，包括：

- 安装所有依赖 - yarn 或 yarn install
- 安装一个包的单一版本 - yarn install --flat
- 强制重新下载所有包 - yarn install --force
- 只安装生产环境依赖 - yarn install --production

> 参考：`yarn install` 的 [完整参数列表](https://yarnpkg.com/zh-Hans/docs/cli/install)。

## 5. 创建一个新项目

不论是已经有了现成的代码仓库（目录），还是正着手启动一个全新项目，你都可以使用同样的方法引入 Yarn。

在命令行终端里，跳转到准备引入 Yarn 的目录（通常是一个项目的根目录），执行以下命令：

```sh
yarn init
```

这将打开一个用于创建 Yarn 项目的交互式表单，其中包含以下问题：

```
name (your-project):
version (1.0.0):
description:
entry point (index.js):
git repository:
author:
license (MIT):
```

你既可以回答这些问题，也可以直接敲回车键（enter/return）使用默认配置或者留空。

## 6. 配置文件

为了别人能使用你的包，以下文件必须被提交进版本控制系统：

- `package.json` - 包含包的所有依赖信息；
- `yarn.lock` - 记录每一个依赖项的确切版本信息；
- 包实现功能的实际项目代码。

> 请参阅[Yarn Example Package](https://github.com/yarnpkg/example-yarn-package)项目，查看一个可用的 Yarn 包所需的最少文件配置。

现在应该创建了一个和下面文件内容类似的 `package.json`：

```json
{
  "name": "my-new-project",
  "version": "1.0.0",
  "description": "My New Project description.",
  "main": "index.js",
  "repository": {
    "url": "https://example.com/your-username/my-new-project",
    "type": "git"
  },
  "author": "Your Name <you@example.com>",
  "license": "MIT"
}
```

执行`yarn init`之后，除了以上文件被创建之外，没有任何副作用。你可以随意编辑此文件。

`package.json`文件里存储了项目的有关信息。 包括项目名称、维护者信息、代码托管地址，以及最重要的：项目依赖。

## 7. 参考资料

- [Yarn 官网](https://yarnpkg.com/zh-Hans/)
- [Yarn Github](https://github.com/yarnpkg/yarn)
