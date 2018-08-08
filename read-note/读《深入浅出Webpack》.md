# 读 《深入浅出Webpack》
读书时产生的一些碎片笔记，抽象理解的笔记去onenote搜索同名笔记

## 入门
### 1-1 前端的发展
#### 模块化
模块化是指把一个复杂的系统分解到多个模块以方便编码。

非模块化的问题：
- 命名空间冲突，两个库可能会使用同一个名称，例如 Zepto 和 jQuery 都放在了 `window.$`
- 无法合理的管理项目的依赖和版本
- 无法方便的控制依赖的加载顺序

#### CommonJS
CommonJS 是一种广泛的 JavaScript 模块化规范，核心思想是通过 `require` 方法来同步地加载依赖的其他模块，通过 `module.exports` 导出需要暴露的接口。(Nodejs 很久以来都是用的这种方式，后来这种方式被引入到了网页开发中)

一个典型的 CommonJS 导入导出实例：
```javascript
// 导入
const expModule = require('./expModule');

// 导出 (这里的 expModule 是一个对象，里面有不同的属性和方法，也可以直接暴露对象中的某个方法)
module.exports = expModule
```
CommonJS 的缺点？代码无法直接运行在浏览器环境下，必须通过工具转换成标准的ES5

#### AMD(Asynchronous module definition)
同样也是一种 JavaScript 的模块化规范，最CommonJS 最大的不同在于采用异步的方式去加载所依赖的模块，AMD 规范主要是针对浏览器环境的模块化问题，比如我使用过的 requirejs

AMD 导入导出实例：
```javascript
// 定义一个模块
define('module', ['dep'], function(dep) {
  return exports;
});

// 导入和使用
require(['module'], function(module) {
});
```

#### ES6 模块化
是欧洲计算机制造联合会 ECMA 提出的 JavaScript 模块化规范，它在语言层面上实现了模块化。它将逐渐取代 CommonJS 和 AMD 规范，成为浏览器和服务器通用的模块化解决方案。

ES6 模块化 导入导出实例：
```javascript
// 导入
import { readFile } from 'fs';
import React from 'react';
// 导出
export function hello() {};
export default {
  // ...
};
```
ES6 模块化的缺点在于目前无法直接运行在大部分的 JavaScript 运行环境下，必须通过工具转换标准的 ES5 后才能正常运行。


#### 样式文件中的模块化
前端开发里的样式文件也支持模块化，例如 SCSS ，把一些常用的样式片段放进一个通用的文件里，再在另一个文件中通过 @import 语句去导入使用样式片段。
```scss
// util.scss 文件

// 定义样式片段
@mixin center {
  // 水平竖直居中
  position: absolute;
  left: 50%;
  top: 50%;
  transform: translate(-50%,-50%);
}

// main.scss 文件

// 导入和使用 util.scss 中定义的样式片段
@import "util";
#box{
  @include center;
}
```
#### 新框架
直接操作 DOM 的方式将不再是开发主流，许多新思想跟着框架被引入到了前端开发中。
- React 
- Vue
- Angular2
> 这里的框架不再做详细描述，每个框架都有自己实现模块化的方式，例如 react 的 jsx，vue的.vue

#### 新语言
ECMAScript 6.0 (ES6) 是 JavaScript 语言的下一代标准（当然现在已经有 ES7 了）

ES6 的典型特点：
- 规范模块化
- Class 语法
- 用 `let` 声明代码块内有效的变量，用 `const` 声明常量
- 箭头函数 `let funcName = () => { //... }`
- async 函数(声明异步方法)
- Set 和 Map 数据结构

#### 结
任何模块方方案现在源代码都无法直接运行，必须通过转换之后才可以正常运行。

