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
## 提纲
* 安利
* 30分钟入门
* ~~Q&A~~讨论

[slide]
## SO!什么是Golang？
* Google开发的一种***静态强类型***、***编译型***、***并发型***、并具有***垃圾回收***功能的编程语言。
* **罗伯特·格瑞史莫**，**罗勃·派克**（Rob Pike）及**肯·汤普逊**为主要作者
* 2009年11月正式宣布推出，成为开放源代码项目
[note]
c,Unix创始人
[/note]

[slide]
## Go的优势是？
* 强制静态编译
* 简化的oo支持
* 天生并发支持
* 标准库
* 错误处理
* simple但并不easy

[slide]
# Let's Go
```
package main

import "fmt"

func main() {
    fmt.Printf("Hello, world or 你好，世界 or καλημ ́ρα κóσμ or こんにちはせかい\n")
}
```
`package <pkgName>`（在我们的例子中是package main）这一行告诉我们当前文件属于哪个包，而包名main则告诉我们它是一个可独立运行的包，它在编译后会产生可执行文件。除了main包之外，其它的包最后都会生成*.a文件,为了打印Hello, world...，我们调用了一个函数Printf，这个函数来自于fmt包，所以我们在第三行中导入了系统级别的fmt包：`import "fmt"`。
