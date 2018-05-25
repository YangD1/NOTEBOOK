### npm 模块安装机制简介

npm 是 Node 的模块管理器

```
npm install
```

`npm install` 命令用来安装模块到 `node_modules` 目录
```
npm install <packageName>
```

安装之前，`node_modules` 目录中是否已经存在指定模块。如果存在，就不再重新安装了，即使远程仓库已经又了一个新版本，也是如此。

使用`-f`或`--force`强制重新安装
```
    npm install <packageName> --force
```
### npm update

更新已安装模块
```
npm update <packageName>
```

> 先到远程仓库查询最新版本，然后查询本地版本。如果本地版本不存在，或者远程版本较新，就会安装。

### registry
`npm update` 命令怎么知道每个模块的最新版本呢？

例如下面这个查询 npmjs.org 

[https://registry.npmjs.org/](https://registry.npmjs.org/)

网址后面跟上模块名，就会得到一个 JSON 对象，里面是该模块所有版本信息，例如访问[https://registry.npmjs.org/react](https://registry.npmjs.org/react) 就会看到 react 模块所有版本的信息。

