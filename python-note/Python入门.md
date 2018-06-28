# Python 基础
[官网](https://www.python.org)
[官方文档](https://docs.python.org)

编程功底的最好体现是数据结构。

语言分类：
- 编译型语言：C C++
- 解释型语言：JavaScript Python
- 工业型语言：Java C#

Python 分为解释器，扩展标准库

### Python能做什么?
- 爬虫
- 大数据与数据分析(spark)
- 自动化运维与自动化测试
- Web开发框架 Flask Django
- 机器学习 TensorFlow
- 胶水语言：混合其他语言来编程

### 进制转换
- `bin()` 用于进制转换成二进制
- `int()` 转换十进制
- `hex()` 转换十六进制
- `oct()` 转换八进制

### Bool 类型
Python 中的布尔类型要大写
```
True
False
```
Python 的 Bool 类型是*数字类型*

###  String 字符串
- `\` 是python的转义字符串
- `'''`或者`"""` 可以输入多行字符串
- print() 会解析转义字符
- 单引号字符串行尾使用`\`可以换行

输出一个原始字符串:
```python
# 使用 r 来声明原始字符串
print(r"hello /n world")
```

#### 字符串可以使用运算符
``` python
"hello" + "world"
>> helloworld

# * 号后面的必须是数字
"hello" * 3
>> hellohellohello

# 输出第一个下标为0的字符
"hello world"[0]
>> h

# 输出第四个下标为3的字符
"hello world"[3]
>> l 

# 从末尾往开头，不再代表下标而代表步长
"hello world"[-3]
>> r

# 方括号中第一个数字代表起始位置，第二个数字代表步长
"hello world"[0:4]
>> hell

# 从下标为0的字符串开始取到最后一个下标前面的字符
"hello world"[0:-1]
>> hello worl

# 从下标为6的字符开始取值到结束
"hello world"[6:]
>> world

# 两种步长设定的方法
"hello world"[0:-4]
"hello world"[:-4]
>> hello w

# 截取后五个字符
"hello world"[-5:]
>> hello
```

### 列表 list
用`[]`标示列表

一个简单的列表：`[1,2,3,4,5,6]`
```python
print(type([1,2,3,4,5,6]))
>> class 'list'

# 再诸如:
# 混合数据列表
["hello","world",1,9,True,False]
# 嵌套列表
[[1,2],["hello","world"],[True,False]]
# 列表拼接
[1,2,3]+[4,5,6]
>> [1,2,3,4,5,6]
```

#### 判断是否在列表中：
```python
3 in [1,2,3,4]
>> True

10 in [1,2,3,4]
>> False

3 not in [1,2,3,4]
>> False
```

### 元组 tuple
用`()`标示元组

`()` 代表空元组

例如：
```python
(1,2,3,4)
# 取下标为0的元组成员
(1,2,3,4)[0]
>> 1
```

#### 元组的特性
- 元组是不可变的，而列表是可变的
- 元组通常由不同数据，而列表是相同类型的数据队列
- 元组标示的是结构，而列表表示的是顺序

例如把元组理解进棋盘中，一对元组代表一个点
```python
# 表示一个点
point = (1,2)
# 表示一个系列点
point = [(1,2),(1,3),(4,5)]
```
元组支持的操作比列表小，元组故所以相对列表更快

### 统计和运算函数
- len() 统计字符串字符数或列表资源总数
- max() 抛出列表中最大的数字
- min() 抛出列表中最小的数字
- ord() 得到字符的 ascll 码 (字符间大小比较时会起作用)

### 集合 set
- 序列是有序的
- 集合是无序的

`{}`代表集合

一个简单的集合: `{1,2,3,4,5,6}`

一个集合不可以有重复的元素，重复的元素会被覆盖合并

```python
# 计算两组集合的差集
{1,2,3,4,5} - {3,4}
>> {1,2,5}
# 计算两组集合的交集
{1,2,3,4,5} & {3,4}
>> {3,4}
```

### 字典 dict
无序的，无法用下标访问
Key Value  
```
{key1: Value1 ,key2: Value2...}
```
- 字典相同的键值对会被最后一个相同的键值所覆盖
- 字典的 Value 可以任何甚至是字典
- key 可以使元祖，不可以是列表
`{}` 代表空的字典

### 变量
声明一个变量名为A的列表：
```
A = [1,2,3,4,5,6]
```

变量名规则：
- 首字母必须是字母或者下划线
- 不可以使用python的保留关键字
- 区分大小写

动态语言变量不需要声明数据类型

- 引用类型可变，值类型不可变
- 引用类型：list set dict
- 值类型： int str tuple

id() 显示某一个变量在内存中的地址
```python
b = [1,2,3]
# 列表变量追加，元组不知此这个操作
b.append(4)
>> [1,2,3,4]
```

### 运算符号 (记录个别)
2**2 代表2的2次方

#### 赋值运算符
先做运算再赋值
- `+=`
- `*=`
- `/=`
- `%=`
- `**=`
- `//=`

> python 不支持 `++` `--` 自增运算符 

#### 比较运算符
- `==`
- `!=`
- `>`
- `<`
- `>=`
- `<=`

#### 逻辑运算符
- `and`
- `or`
- `not`

- 0 被认为是 `False`
- 非 0 标示 `True`
- [] 空的列表标示 `False`,非空则是 `True` (tuple,set,dict 可以用相同的逻辑表示)

#### 成员运算符
判断一个元素是否存在于另一组元素中
- `in`
- `not in`

#### 身份运算符
- `is`
- `not is`

如果两个变量取值相等，则 is 返回 True

比较两个变量身份(内存地址) 是否相等

#### 位运算符
把数字当成二进制数进行运算
- `&` 按位与
- `|` 按位或
- `^` 按位异或
- `~` 按位取反
- `<<` 左移动
- `>>` 右移动

### python 如何区分代码块
python 使用缩进来控制代码块，不同于一般代码的 `{ do...something... }`

### 条件控制
`if else`

```python
mood = True
if mood:
    print('go to left')
else:
    print('go to right')

>> go to left
```

简单定义一个用户登录输入账号密码验证:
```python
account = 'youngdee'
password = '123456'

print('请输入账号:')
user_account = input()
print('请输入密码:')
user_password = input()

if account == user_account and password  == user_password:
    print('登录成功')
else:
    print('登录失败')

```

`if`语句可以单独使用

嵌套使用：
```python
# 普通的嵌套
if condition:
    if condition:
        pass
    else:
        pass
else:
    if condition:
        pass
    else:
        pass

# 使用 elif 嵌套
if condition:
    pass
elif conditin:
    pass
else:
    pass
```

python 中没有 switch，官方推荐使用`elif`代替，或者使用字典的方式来代替switch

### 循环语句
`while` `for`

`while`(递归的时候常用到)
```python
while condition:
    pass

# 示例
counter = 1
while counter <= 10: 
    counter += 1 
    print(counter)
else:
    # 程序结束后才运行这里的语句
    print("EOF")
>> 2 
>> 3
...
>> 11
>> EOF
```

`for` (主要用来遍历/循环 序列或者集合/字典)
```python
# 基础使用
a  = ['apple','orange','banana','grape']
for x in a:
    print(x)

# 遍历复杂数据,嵌套循环
a  = [['apple','orange','banana','grape'],(1,2,3)]
for x in a:
    for y in x:
        # end="" 每次输出结束后输出一个定义的字符串 
        print(y,end=" | ")
else:
    # 当列表中所有元素遍历完了之后执行
    print('fruit is gone')

>> apple | orange | banana | grape | 1 | 2 | 3 | fruit is gone
```
在循环中可以使用`continue`和`break`来执行响应逻辑的循环的跳出/终止

#### range(起始位置,偏移量,步长)
```python
for x in range(0,10):
    print(x,end=" ")
>> 0 1 2 3 4 5 6 7 8 9

for x in range(0,10,2):
    print(x,end=" ")
>> 0 2 4 6 8

for x in range(10,0,-2):
    print(x,end=" ")
>>  10 8 6 4 2

# 输出下面列表中的奇数
a = [1,2,3,4,5,6,7,8]
for i in range(0,len(a),2):
    print(a[i],end=' | ')
>> 1 | 3 | 5 | 7

# 用数列的切片来实现上面
b  = a[0:len(a):2]
>> 1 | 3 | 5 | 7
```

### Python 工程的组织结构： 包 模块 类(函数，变量)
Python 中包的名字等同于目录的名字,模块等同于目录下的文件,包的下面也可以包含一个包可以有平级的模块,包目录下必须包含一个`__init__.py`文件。
> python 一切都是面向对象

区分不同包两个相同的模块：Pone.c4 Ptwo.c4

`import MODULE_NAME` 导入模块(只能导入到模块,不能导入到类或者模块中的成员)

`import MODULE_NAME as m` 可以这样来简化命名空间

`from MODULE_NAME import a` 这样调用可以直接使用模块中的成员a

`from MODULE_NAME import *` 这样调用可以直接使用模块中的所有成员

在模块中定义内置属性`__all__`列成列表可以定义要被import导出的变量


