### GO 基础语法
Go 保留的关键字只有25个：

| break | default | func | interface | select |
| :---: | :----: | :--: | :-------: | :----: |
| case | defer | go | map | struct |
| chan | else | goto | package | switch |
| const | fallthrough | if | range | type |
| continue | for | import | return | var |

GO 语言36个预定义标识符，包括基础数据类型和系统内嵌函数：

| append | bool | byte | cap | close | complex |
| :---: | :----: | :--: | :-------: | :----: | :---: |
| complex64 | complex128 | uint16 | copy | false | float32 |
| float64 | imag | int | int8 | int16 | uint32 |
| int32 | int64 | iota | len | make | new |
| nil | panic | uint64 | print | println | real |
| recover | string | TRUE | uint | uint8 | unitprt |

注释形式：
1. // 单行注释
2. /* */ 多行注释

基础语法：
```GO
package main
import "fmt"
const NAME = "name"
var mainName = "main name"
func main()
{
    fmt.Print(mainName)
    fmt.Print(NAME)
}

/*
*  结果输出 name  main name
*/
```

