### Node 基础
安装参考官方文档

升级node.js和npm：
```javascript
$ npm install -g n
$ n stable
$ npm install -g npm@next
```

### 简单实现一个 nodejs 程序 hello.js：
```javascript
console.log('hello world')
```

### 简单实现一个 nodejs web 服务 server.js：
```javascript
// 使用 require 来载入 http 模块，将实例化的 HTTP 赋值给变量 http 
var http = require('http');

http.createServer(function (request, response) {

    // 发送 HTTP 头部 
    // HTTP 状态值: 200 : OK
    // 内容类型: text/plain
    response.writeHead(200, {'Content-Type': 'text/plain'});

    // 发送响应数据 "Hello World"
    response.end('Hello World\n');
}).listen(8888);

// 终端打印如下信息
console.log('Server running at http://127.0.0.1:8888/');
```
使用 node 命令执行:
```
$ node server.js
# 会有如下提示
Server running at http://127.0.0.1:8888
```

### npm 的使用
```
$ npm insatll <Module Name>
# 安装一个web框架模块 express 
$ npm install express
```
安装好之后，express 包放在了项目目录(运行了命令行的目录)下的 `node_modules` 目录中，在代码中只要 `require('express')` 的方式就好，无需指定第三方包路径
```
var express = require('express');
```

#### 全局安装和本地安装
```
npm install express  # 本地安装
npm install express -g # 全局安装
```

#### 查看所有安装的模块
```
# 查看所有全局安装的模块
$ npm list -g
# 查看模块的版本号(例如查看grunt)
$ npm list grunt
```

#### 使用 package.json
`package.json` 位于模块的目录下，用于定义包的属性。

#### package.json 属性说明
- name - 包名
- version - 包的版本号
- description - 包的描述
- homepage - 包的官网 url
- author - 包的作者姓名
- contributors - 包的其他贡献者姓名
- dependencies - 依赖包列表。如果依赖包没有安装，npm 会自动将依赖包安装在 node_module 目录下
- repository - 包代码存放的地方的类型，可以是 git 或 svn，git 可在 github 上
- main - main 字段指定了程序的主入口文件 ,require('moduleName') 就会加载这个文件，这个字段的默认值是模块根目录下面的 index.js
- keywords - 关键字

#### 卸载模块
```
$ npm uninstall express
```
卸载后，可以到 `node_modules` 目录下查看包是否还存在，或用以下命令查看
```
$ npm ls
```

#### 更新模块
```
$ npm udpate express
```

#### 搜索模块
```
$ npm search express
```

#### 创建模块
```
$ npm init
This utility will walk you through creating a package.json file.
It only covers the most common items, and tries to guess sensible defaults.

See `npm help json` for definitive documentation on these fields
and exactly what they do.

Use `npm install <pkg> --save` afterwards to install a package and
save it as a dependency in the package.json file.

Press ^C at any time to quit.
name: (node_modules) runoob                   # 模块名
version: (1.0.0) 
description: Node.js 测试模块(www.runoob.com)  # 描述
entry point: (index.js) 
test command: make test
git repository: https://github.com/runoob/runoob.git  # Github 地址
keywords: 
author: 
license: (ISC) 
About to write to ……/node_modules/package.json:      # 生成地址

{
  "name": "runoob",
  "version": "1.0.0",
  "description": "Node.js 测试模块(www.runoob.com)",
  ……
}


Is this ok? (yes) yes
```
以上的信息，根据情况输入，最后生成 package.json 文件
接下来可以使用以下命令在 npm 资源库中注册用户(使用邮箱注册):
```
$ npm adduser
```
接下来可以如下来发布模块
```
$ npm publish
```
#### 版本号
使用 NPM 下载和发布代码都会接触到版本号。NPM 使用语义版本来管理代码。

语义版本号分为 X.Y.Z 三位，分别代表主版本号，次版本号和补丁版本号。代码变更时，版本号按以下原则更新。

- 如果只是修复bug，需要更新Z位
- 如果是新增了功能，但是向下兼容，需要更新Y位
- 如果有大变动，向下不兼容，需要更新X位

版本号有了这个保证后，在申明第三方依赖时，除了可依赖于一个固定版本号外，还可依赖于某个范围的版本号。[版本号指定范围](https://npmjs.org/doc/files/package.json.html#dependencies)

#### 其他
```
# 查看 npm 的所有命令
$ npm help
# 查看 npm 某个模块的命令
$ npm help <command>
```






