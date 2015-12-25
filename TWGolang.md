title: Golang大法好
speaker: XiyuChen
transition: stick
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
* 语言简单
* 效率高，编译速度快
* 天生并发支持
* 标准库

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
    [note]
    * 无序,不能通过index获取，必须通过key获取
    * 长度是不固定的，和slice一样，是一种引用类型
    * len函数适用于map，返回map拥有的key的数量
    [/note]

[slide]
# 流程控制
[slide]
# for
```
for expression1; expression2; expression3 {
    //...
}
```
``` 
for i := 0 ; i < 1 ; i++ {
    //...
}
```
```
for i < 1 {
    //...
}
```
```
for k, v =: range map {
    //...
}
```

[slide]
# if
```
if expressions {
    ...
} else {
    ...
}
```

[slide]
# switch
```
switch sExpr {
case expr1:
    some instructions
case expr2:
    some other instructions
case expr3:
    some other instructions
default:
    other code
}
```
    [note]
    * case后面不需要是常量噢～
    * 默认不需要break
    * `fallthrough`
    [/note]
```
switch {
case score >= 90 && score <= 100:
    //...
case score >= 80 && score <90:
    //...
default:
    //...
}
```
[slide]
# goto
无条件跳转到某标号。`慎用`

[slide]
# 函数
Go的核心设计，通过`func`关键字来定义函数

[slide]
```
func funcname(intput1 type1, intput2 type2)(type3, type4){
    //.....
    return output1, output2
}
```
    [note]
    多值返回，不定个数参数，参数解包
    [/note]


[slide]
# 函数是一等公民
    [note]
    * 函数能接受函数作为参数，也能将函数作为返回值
    [/note]


[slide]
```
package main
import "fmt"

type testInt func(int) bool // 声明了一个函数类型

func isOdd(integer int) bool {
    if integer%2 == 0 {
        return false
    }
    return true
}

func filter(slice []int, f testInt) []int {
    var result []int
    for _, value := range slice {
        if f(value) {
            result = append(result, value)
        }
    }
    return result
}

func main(){
    slice := []int {1, 2, 3, 4, 5, 7}
    fmt.Println("slice = ", slice)
    odd := filter(slice, isOdd)    // 函数当做值来传递了
    fmt.Println("Odd elements of slice are: ", odd)
}
```


[slide]
# 闭包
由函数及其相关引用环境组成的实体。


[slide]
# 闭包与对象

[slide]
# defer
延迟语句的执行到函数退出的时候
    [note]
    * open file close file
    * 栈
    [/note]

[slide]
```
package main
import "fmt"

func main(){
    var arr [...]int{1, 2, 3, 4, 5}
    
    for i := range arr{
       defer fmt.Println(i)
    }
}
```
    [note]
    常用于文件的打开与关闭,信道的打开与关闭
    [/note]

[slide]
# range
用在循环语句中，允许依次取出map，array，slice里面的元素进行遍历.
```
for _, v := range map{
    fmt.Println(v)
}
```


[slide]
# struct
    [note]
    将一类属性或者字段进行打包
    首字母大写字段为export字段,类似与public
    [/note]


[slide]
```
type persion struct{
    name string
    age int
}
```

[slide]
# 简化的OO


[slide]
# method
Go允许我们为特定的类型绑定方法。


[slide]
```
package main
import "fmt"

type Rectangle struct {
    width, height float64
}

func area(r Rectangle) float64 {
    return r.width*r.height
}

func main() {
    r1 := Rectangle{12, 2}
    r2 := Rectangle{9, 4}
    fmt.Println("Area of r1 is: ", area(r1))
    fmt.Println("Area of r2 is: ", area(r2))
}
```

[slide]
```
package main
import (
    "fmt"
    "math"
)

type Rectangle struct {
    width, height float64
}

type Circle struct {
    radius float64
}

func (r Rectangle) area() float64 {
    return r.width*r.height
}

func (c Circle) area() float64 {
    return c.radius * c.radius * math.Pi
}


func main() {
    r1 := Rectangle{12, 2}
    c1 := Circle{10}

    fmt.Println("Area of r1 is: ", r1.area())
    fmt.Println("Area of c1 is: ", c1.area())
}
```
    [note]
    虽然method的名字一模一样，但是如果接收者不一样，那么method就不一样
    method里面可以访问接收者的字段
    调用method通过.访问，就像struct里面访问字段一样
    接收者可以是指针
    [/note]


[slide]
# interface 
一组method的集合，并取了个名字。
    [note]
    不用显示的实现
    [/note]

[slide]
# duck typing
1. 定义鸭子的样子：走路、游泳...
2. 看到了一个物体
3. 该物体能像鸭子一样走路、游泳...那么我们就说这个物体是鸭子

[slide]
```
type someOne interface{
    sayHi()
}
type dog struct{
    //....
}
type cat struct{
    //....
}
type bird struct{
    //....
}
type duck struct{
    //....
}
type cow struct{
    //....
}
type mouse struct{
    //....
}
```


[slide]
```
func (d dog) sayHi(){
    fmt.Println("woof~")
}
func (c cat) sayHi(){
    fmt.Println("meow~")
}
func (b bird) sayHi(){
    fmt.Println("tweet~")
}
func (du duck) sayHi(){
    fmt.Println("quack~")
}
func (co cow) sayHi(){
    fmt.Println("moo~")
}
func (m mouse) sayHi(){
    fmt.Println("squeek~")
}

func saySomething( it someOne){
    it.sayHi()
}
```


[slide]
# 并发
* 并发：同一时间段执行多个任务(程序的并发执行）
* 并行：同一时刻执行任务(cpu/gpu并行计算）

[slide]
# goroutine
goroutine是Go并行设计的核心。goroutine说到底其实就是线程，但是它比线程更小，十几个goroutine可能体现在底层就是五六个线程，Go语言内部帮你实现了这些goroutine之间的内存共享。


[slide]
```
package main

import (
    "fmt"
    "runtime"
)

func say(s string) {
    for i := 0; i < 5; i++ {
        runtime.Gosched() //将时间片让给其他goroutine
        fmt.Println(s)
    }
}

func main() {
    go say("world") //开一个新的Goroutines执行
    say("hello") //当前Goroutines执行
}
//  Output:
// hello
// world
// hello
// world
// hello
// world
// hello
// world
// hello
```

[slide]
# channel

[slide]
# Thanks
