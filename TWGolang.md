title: Golang大法好
speaker: XiyuChen
url: http://localhost:8080
transition: cards
theme: dark
highlightStyle: monokai_sublime
date: 2015-12-26

[slide]
# "我当时只是想纠集一帮人一起憎恨C++～"

[slide]
# 提纲
* 安利
* 30分钟入门
* ~~Q&A~~讨论

[slide]
# 谁在用Go
* Docker
* Google
* 七牛云存储
* Dropbox
* 美团后台流量支撑程序
* heroku

[slide]
# SO!什么是Golang？
* Google开发的一种***静态强类型***、***编译型***、***并发型***、并具有***垃圾回收***功能的编程语言。
* **罗伯特·格瑞史莫**，**罗勃·派克**（Rob Pike）及**肯·汤普逊**为主要作者
* 2009年11月正式宣布推出，成为开放源代码项目
[note]
c,Unix创始人 
开源，不用担心google甩手不干了
[/note]

[slide]
# Go的优势是？
* 效率高，编译速度快
* 强制静态编译
* 简化的oo支持
* 天生并发支持
* 标准库
* 错误处理
* simple但并不easy

[slide]
# Go关键字
```
break    default    func    interface    select    case    defer    go   

struct   chan   else   goto   package   switch   const   fallthrough 

if   range   type   continue   for   import   return   var   map 
```

[slide]
# Let's Go
```
package main

import "fmt"

func main() {
    fmt.Printf("Hello, world or 你好，世界 or καλημ ́ρα κóσμ or こんにちはせかい\n")
}
```
[note]
1. package :当前代码属于哪个包 ,import ： 引入其他包的代码
3. 包内函数使用packageName.funcName, main.main()是程序的入口，
7. 包内大写打头的是public的
1. func 关键字定义函数，main函数必须没有参数和返回值。
2. UTF8支持
[/note]

[slide]
# 变量类型
```
bool 
float64,    float32 
int8,   int16,  rune,    int32,  int64
byte,   uint8,  uint16,  uint32, uint64
complex128, complex64
string
```
[note]
rune是int32的别名，byte是uint8的别名
[/note]

[slide]
# 变量声明/定义
```
var i, j int 
k := 3.23
_, x := "i'm a string", 324.23

var arr [10]int
a := [3]int{1, 3, 5}
b := [...]float64{3.14, 1.44}
```
[note]
使用关键字`var`声明/定义，使用`:=`直接定义
有个特殊变量`_`,赋值给`_`的值都将被丢弃
[/note]

[slide]
# slice
在初始定义数组时，我们并不知道需要多大的数组，因此我们就需要“动态数组”。在Go里面这种数据结构叫slice,slice并不是真正意义上的动态数组，而是一个引用类型。slice总是指向一个底层array，slice的声明也可以像array一样，只是不需要长度。

[slide]
```
var sl1 []int

var arr [...]int{1, 2, 3, 4}
sl2 := arr[0:2]
sl3 := arr[:]
```

[slide]
#map
`map`也就是Python中字典的概念，它的格式为map[ keyType ]valueType,通俗的讲就是键值对。`map`的定义需要要使用`make`关键字。
make用来初始化一些复杂的数据结构，比如slice，map,channel等。

[slide]
```
var numbers map[string]int
numbers = make(map[string]int)

numbers["one"]=1
numbers["ten"]=10
fmt.Println("第十个数是：",numbers["ten"])
```
[slide]
# 流程控制

[slide]
# 函数

[slide]
# defer

[slide]
# range

[slide]
# struct

[slide]
# OO

[slide]
# interface 

[slide]
# 并发

[slide]
# goroutine

[slide]
# channel

[slide]
# Thanks
