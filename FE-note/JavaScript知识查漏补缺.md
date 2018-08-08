# JavaScript 知识查漏补缺
记录从学习过程中积累的概念和不懂的知识点

### 什么是 Mixin 模式
这是一种 JavaScript 的设计模式，同样属于JavaScript 设计模式的还有：构造器模式，模块化模式，暴露模块化模式，单例模式，观察者模式，中介者模式，原型模式...等等。

而 mixin 模式简单来说就是 **将一个对象的属性复制给另一个对象** ，ES5 中，mixin 为 object 提供“混合”能力，由于 JavaScript 的原型继承机制，通过 mixin 一个或多个对象到构造器的 prototype 上，能够间接提供为“类”的实例混合功能的能力。从一定程度上，mixin 弥补了 JavaScript 单一原型链的却下，可以实现类似于多重继承的效果。在 ES6 中，可以采用全新的基于类继承的“mixin”模式设计更优雅的“语义化”接口。

具体有关于 JavaScript 设计模式的问题，会开个新项目来进行研究...

### JavaScript 函数节流和函数去抖
[参考](https://webfem.com/post/debounce)
