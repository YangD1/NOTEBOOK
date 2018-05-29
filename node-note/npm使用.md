### npm 模块安装机制简介

[淘宝国内npm镜像](https://npm.taobao.org/)

npm 是 Node 的模块管理器

```
npm install
```

`npm install` 命令用来安装模块到 `node_modules` 目录
```
npm install <packageName>
```

安装之前，`node_modules` 目录中是否已经存在指定模块。如果存在，就不再重新安装了，即使远程仓库已经又了一个新版本，也是如此。

使用`-f`或`--force`强制重新安装
```
    npm install <packageName> --force
```
`install` 后面可以跟的参数
- `-g`:全局安装
- `--save`:将保存配置信息至 `package.json`
- `-dev`:将保存`package.json`的`devDependencies`节点，不指定-dev将保存至`dependencies`节点

npm install 可以直接从 github 下载：
```
$ npm install git://github.com/package/path.git
$ npm install git://github.com/package/path.git#0.1.0
```

### npm update

`npm update` 工作过程：
1. 先到远程仓库查询最新版本
2. 对比本地版本，如果本地版本不存在，或者远程版本较新
3. 查看 package.json 中对应的语义版本规则
4. 如果当前新版本符合语义规则，就更新，否则不更新

更新已安装模块
```
npm update <packageName>
```

> 先到远程仓库查询最新版本，然后查询本地版本。如果本地版本不存在，或者远程版本较新，就会安装。

### 卸载本地 package `npm uninstall`
```
# 普通的删除
npm uninstall <package-name>
# 删除项目的同时移除 package.json 中对它的依赖
npm uninstall --save lodash
# 卸载全局 package 
npm uninstall -g <package>
```

### npm run 
npm 可以直接运行 package.json 中的 scripts 指定的脚本：
```
{
  "name": "demo",
  "scripts": {
    "lint": "jshint **.js",
    "test": "mocha test/"
  }
}
```
命令行输入 `npm run lint` 或者 `npm run-script lint` 就会执行 `jshint **.js` 。

### npm info
```
# 查看指定包的信息
npm info <package-name>
```

### npm adduser
```
# 在 npmjs.com 注册一个用户
$ npm adduser
Username: YOUR_USER_NAME
Password: YOUR_PASSWORD
Email: YOUR_EMAIL@domain.com
```

#npm home/repo
`npm home <package-name>`命令可以打开指定模块的主页； 
`npm repo <package-name>`命令则是打开指定模块的代码仓库。

### registry
`npm update` 命令怎么知道每个模块的最新版本呢？

例如下面这个查询 npmjs.org 

[https://registry.npmjs.org/](https://registry.npmjs.org/)

网址后面跟上模块名，就会得到一个 JSON 对象，里面是该模块所有版本信息，例如访问[https://registry.npmjs.org/react](https://registry.npmjs.org/react) 就会看到 react 模块所有版本的信息。

