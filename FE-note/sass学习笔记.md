# Sass 学习笔记
Sass 是对 CSS 的扩展。

### 特点
- 完全兼容 CSS3
- 在 CSS 语言基础上添加了扩展功能，比如变量，嵌套(nesting),混合(mixin)
- 对颜色和其他值进行操作的 {Sass::Script::Functions 函数}
- 函数指令控制之类的高级功能
- 良好的格式，可对输出格式进行定制
- 支持 Firebug

### 语法
Sass 有两种语法
1. 第一种被称为 SCSS(Sassy CSS)， 是一个 CSS3 语法的扩充版本。 
2. 第二种被称为缩排语法(或者就称为"Sass")，提供了一种更简洁的 CSS 书写方式。它不使用花括号，而是通过缩排的方式来表达选择符的嵌套层级。

任何一个语法都可以导入另一种语法撰写的文件中。只要使用 `sass-convert` 命令行工具，就可以将一种语法转换成另一种语法。
```
# 将 sass 转换为 scss 
$ sass-convert style.sass style.scss
# 将 scss 转换为 sass 
$ sass-convert style.scss style.sass
```
具体区别可以参考sass[官方网站文档指南部分](https://sass-lang.com/guide)

### 安装
Sass 有三种使用方式：命令行工具、独立的 Ruby 模块，以及包含 Ruby on Rails 和 Merb 作为支持 Rack 的框架的插件。所有这些方式第一步都是安装 Sass gem:
```
$ gem install sass
```
tip:请先安装Ruby

如果要在命令行中运行 Sass，只要输入
```
sass input.scss output.css
```
你还可以命令 Sass 监视文件的改动并更新 CSS：
```
sass --watch input.scss:output.css
```
如果你的目录中有很多 Sass 文件，你还可以命令 Sass 监视整个目录：
```
sass --watch app/sass:public/stylesheets
```
使用 `sass --help` 可以列出完整的帮助文档。

