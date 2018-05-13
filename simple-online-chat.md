## WHAT

一个简单的在线聊天WEB应用。输入昵称即可进入聊天室开始聊天

### 目录结构

```
入口文件 index.ts


./src             ------------------------   业务代码库
  |
  |
  |
  |---- event     ------------------------   业务逻辑所需定义的事件处理器，包含登录处理，注销处理，消息处理等
  |       |
  |       |---- LOGIN.ts   ---------------   登录事件处理器
  |       |
  |       |---- LOGOUT.ts  ---------------   注销事件处理器
  |       |
  |       |---- NUM_PEOPLE.ts ------------   人数处理器
  |       |
  |       |---- SPEAK.ts -----------------   消息处理器
  |       |
  |       |---- index.ts
  |
  |---- frontend -------------------------   前端代码，包含页面UI以及逻辑
  |       |
  |       |---- static -------------------   静态资源
  |       |       |
  |       |       |---- index.js ---------   前端index页面逻辑，前端websocket处理逻辑包含于此
  |       |       |
  |       |       |----  index.css -------   UI
  |       |
  |       |---- index.html ---------------   index页面（首页）
  |
  |
  |
  |---- app.ts ---------------------------   工厂创建Websocket Server与HTTPServer
  |
  |
  |---- render.ts ------------------------   渲染前端文档，以及部分静态资源
  |
  |
  |---- serverHandler.ts -----------------   HTTP请求处理器
  |
  |
  |---- wssHandler.ts --------------------   Websocket连接处理器，解析数据并分发到不同的事件处理器

```

## WHY

学习下Websocket


## HOW

核心环境为Nodejs，开发语言为TypeScript，无数据库，即用户状态在目前版本并不能维持

本人在学习Websocket，顺手写了一个这个。并无过多较复杂语法，如果想学习类似技术可参考

需要说明的是，当前版本并不能用于生产环境！

### START

首先需要安装Node环境

定位到项目目录：

```
npm i
npm run start
```

项目将默认监听于本机器3000端口（http://127.0.0.1:3000）

### 如何使用

需要演示的话请使用不同的浏览器，因为在单个域下的状态在一个浏览器中是相同的

### NOTICE

需要说明的是，本项目离成熟的在线聊天类应用还差的比较远。本项目目前仅仅实现了简单的文本信息收发，状态维持，查看成员列表以及个数等为数不多的功能搭配一个简陋的前端UI。同时在安全性，可用性等方面都是不足的

本项目的学习价值远大于其使用价值，在后期维护过程中，前端可能会选择Angular SPA活着Vue SPA，甚至PWA都可能。而后端可能会重构为Koa.js或者采用Python或者Golang

## 当前版本更新记录

### 0.3.0

> * 将EVENT移出了wssHandler.ts，让wssHandler逻辑更清晰，解耦
> * 现在可以退出了

### 0.2.0

> * 重构了整个项目，移除了编译产生Javascript，现在直接ts-node运行TypeScript
> * 重写了simpleRender函数，现在可以处理静态资源了
> * 实现了基于令牌的会话保持机制


## TODO

> * ~~会话保持~~
> * ~~唯一昵称以及昵称长度限制~~
> * ~~高持久化的会话保持~~
> * 重构前端代码，使用Rx响应式实现
> * 二进制（例如图片）聊天
> * ~~完成退出功能~~
> * 美化一下UI
> * 端到端测试