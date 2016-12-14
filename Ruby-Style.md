title: Ruby Style Guide
speaker: XiyuChen
transition: stick
theme: dark
highlightStyle: monokai_sublime
date: 2015-12-26

[slide]
# Ruby Style

[slide]
1. Ruby Style
2. Rails Style

[slide]
# 代码排版

[slide]
* 使用 UTF-8 作为源文件的编码
* 每个缩排层级使用两个空格。不使用制表符
* 使用 Unix 风格的换行符。
* 不使用`;`隔开语句与表达式。(一行一条语句)
* 避免在非必要的情形下使用续行符`\`

[slide]
* 方法定义避免使用单行定义(空方法除外)

---
```Ruby
# not good
def too_much; something; something_else; end

# good
def some_method
  body
end

# so so
def no_op; end
```

[slide]
* 没有主体的类，尽量使用单行定义

---
```Ruby
# not good
class FooError < StandardError
end

# good
FooError = Class.new(StandardError)
```

[slide]
* 操作符前后适当地添加空格(指数操作除外)，在逗号`,`、冒号`:`及分号`;`之后添加空格

---
```Ruby
# good
sum = 1 + 2
a, b = 1, 2
class FooError < StandardError; end

# not good
e = M * c ** 2

# good
e = M * c**2
```

[slide]
* `(`、`[`之后，`]`、`)`之前，不添加空格。在`{`前后，在`}`之前添加空格。

---
```Ruby
# not good
some( arg ).other
[ 1, 2, 3 ].each{|e| puts e}

# good
some(arg).other
[1, 2, 3].each { |e| puts e }
```

[slide]
* `!`之后，不要添加任何空格
* 范围的字面量语法中，不要添加任何空格

---
```Ruby
# not good
1 .. 3
'a' ... 'z'

# good
1..3
'a'...'z'
```

[slide]
* 把`when`与`case`缩排在同一层级。(《Programming Ruby》与《The Ruby Programming Language》推荐)

---
```Ruby
# not good
case
  when song.name == 'Misty'
    puts 'Not again!'
  when song.duration > 120
    puts 'Too long!'
  when Time.now.hour > 21
    puts "It's too late"
  else
    song.play
end

# good
case
when song.name == 'Misty'
  puts 'Not again!'
when song.duration > 120
  puts 'Too long!'
when Time.now.hour > 21
  puts "It's too late"
else
  song.play
end
```

[slide]
* 保持分支缩排在同一层级。

---
```Ruby
# bad
kind = case year
when 1850..1889 then 'Blues'
when 1890..1909 then 'Ragtime'
when 1910..1929 then 'New Orleans Jazz'
when 1930..1939 then 'Swing'
when 1940..1950 then 'Bebop'
else 'Jazz'
end

result = if some_cond
  calc_something
else
  calc_something_else
end
```

[slide]
```Ruby
# Good
kind = case year
       when 1850..1889 then 'Blues'
       when 1890..1909 then 'Ragtime'
       when 1910..1929 then 'New Orleans Jazz'
       when 1930..1939 then 'Swing'
       when 1940..1950 then 'Bebop'
       else 'Jazz'
       end

result = if some_cond
           calc_something
         else
           calc_something_else
         end

# Good
kind =
  case year
  when 1850..1889 then 'Blues'
  when 1890..1909 then 'Ragtime'
  when 1910..1929 then 'New Orleans Jazz'
  when 1930..1939 then 'Swing'
  when 1940..1950 then 'Bebop'
  else 'Jazz'
  en    d

result =
  if some_cond
    calc_something
  else
    calc_something_else
  end
```

[slide]
* 在各个方法定义之间添加空行，并且将方法分成若干合乎逻辑的段落。

---
```Ruby
def some_method
  data = initialize(options)

  data.manipulate!

  data.result
end

def some_method
  result
end
```

[slide]
* 避免在方法调用的最后一个参数之后添加逗号，尤其当参数没有分布在同一行时。

---
```Ruby
# not good
some_method(
  size,
  count,
  color,
)

# not good
some_method(size, count, color, )

# good
some_method(size, count, color)
```

[slide]
* 当给方法的参数赋予默认值时，在`=`前后添加空格

---
```Ruby
# bad
def some_method(arg1=:default, arg2=nil, arg3=[])
  # do something
end

# good
def some_method(arg1 = :default, arg2 = nil, arg3 = [])
  # do something
end
```

[slide]
* 当方法调用参数过长时，将它们排列在多行并对齐。若对齐后长度超过行宽限制，将首个参数位置挪到下一行进行缩排

```Ruby
# not good
def send_mail(source)
  Mailer.deliver(to: 'bob@example.com', from: 'us@example.com', subject: 'Important message', body: source.text)
end

# good
def send_mail(source)
  Mailer.deliver(to: 'bob@example.com',
                 from: 'us@example.com',
                 subject: 'Important message',
                 body: source.text)
end
```

[slide]
* 当构建数组时，若元素跨行，应当保持对齐。

---
```Ruby
# not good
menu_item = ['Spam', 'Spam', 'Spam', 'Spam', 'Spam', 'Spam', 'Spam', 'Spam',
  'Baked beans', 'Spam', 'Spam', 'Spam', 'Spam', 'Spam']

# good
menu_item = [
  'Spam', 'Spam', 'Spam', 'Spam', 'Spam', 'Spam', 'Spam', 'Spam',
  'Baked beans', 'Spam', 'Spam', 'Spam', 'Spam', 'Spam'
]

# good
menu_item =
  ['Spam', 'Spam', 'Spam', 'Spam', 'Spam', 'Spam', 'Spam', 'Spam',
   'Baked beans', 'Spam', 'Spam', 'Spam', 'Spam', 'Spam']

menu_item = %w(Spam, Spam, Spam, Spam, Spam, Spam, Spam, Spam,
              Baked beans, Spam, Spam, 'Spam, Spam, Spam)
```
[slide]
* 使用`_`语法改善大数的数值字面量的可读性。

---
```Ruby
# not good
num = 1000000

# good
num = 1_000_000
```

[slide]
* 当数值需要前缀标识进制时，倾向使用小写字母。使用`0o`标识八进制，使用`0x`标识十六进制，使用`0b`标识二进制。十进制数值无需前缀`0d`标识。

---
```Ruby
# not good
num = 01234
num = 0O1234
num = 0X12AB
num = 0B10101
num = 0D1234
num = 0d1234

# good
num = 0o1234
num = 0x12AB
num = 0b10101
num = 1234
```

[slide]
* 将单行长度控制在 80 个字符内。
* 避免行尾空格。
* 文件以空白行结束。

[slide]
* 不要使用区块注释。它们不能被空白字符引导，且不如常规注释容易辨认。

---
```Ruby
# not good
=begin
comment line
another comment line
=end

#  good
# comment line
# another comment line]
```

[slide]
# 语法

[slide]
* 使用`::`引用常量（包括类与模块）与构造器（比如 Array()、Nokogiri::HTML()）。不要使用`::`调用常规方法。

```Ruby
# not good
SomeClass::some_method
some_object::some_method

# good
SomeClass.some_method
some_object.some_method
SomeModule::SomeClass::SOME_CONST
SomeModule::SomeClass()
```

[slide]
* 使用`def`定义方法时，如果有参数则使用括号，如果无参数则省略括号

---
```Ruby
# not good
def some_method()
 # do something
end

# good
def some_method
 # do something
end

# not good
def some_method_with_parameters param1, param2
 # do something
end

# good
def some_method_with_parameters(param1, param2)
 # do something
end
```

[slide]
* 方法调用应当使用括号包裹参数，尤其是第一个参数由`(`开头
* 如下情况省略括号
    + 无参数调用
    + 内部DSL组成(rake, rails, rspec)

---
```Ruby
x = Math.sin y  # not good
x = Math.sin(y) # good

array.delete e  # not good
array.delete(e) # good

temperance = Person.new 'Temperance', 30  # not good
temperance = Person.new('Temperance', 30) # good

expect(bowling.score).to eq 0  # not good
expect(bowling.score).to eq(0) # good
```

[slide]
* 使用默认参数时，将默认参数放置在参数列表最后

---
```Ruby
# not good
def some_method(a = 1, b = 2, c, d)
  puts "#{a}, #{b}, #{c}, #{d}"
end

some_method('w', 'x') # => '1, 2, w, x'
some_method('w', 'x', 'y') # => 'w, 2, x, y'
some_method('w', 'x', 'y', 'z') # => 'w, x, y, z'

# good
def some_method(c, d, a = 1, b = 2)
  puts "#{a}, #{b}, #{c}, #{d}"
end

some_method('w', 'x') # => '1, 2, w, x'
some_method('w', 'x', 'y') # => 'y, 2, w, x'
some_method('w', 'x', 'y', 'z') # => 'y, z, w, x'
```

[slide]
* 除非必要，否则避免在并行赋值时使用单字符的`_`变量。优先考虑前缀形式的下划线变量，而不是直接使用`_`,因为前者可以提供一定的语义信息。但当赋值语句左侧出现带`*`操作符的变量时，使用`_`也是可以接受的

---
```Ruby
foo = 'one,two,three,four,five'

# not good - 可有可无，且无任何有用信息
first, second, _ = foo.split(',')
first, _, _ = foo.split(',')
first, *_ = foo.split(',')

# good
a, = foo.split(',')
a, b, = foo.split(',')

# good - 可有可无，但提供了额外信息
first, _second = foo.split(',')
first, _second, = foo.split(',')
first, *_ending = foo.split(',')

# good - 占位符，_ 担当最后一个元素
*beginning, _ = foo.split(',')
*beginning, something, _ = foo.split(',')
```

[slide]
* 用迭代器代替for(for 未引入新的作用域)

---
```Ruby
arr = [1, 2, 3]

# bad
for elem in arr do
  puts elem
end

# 注意，elem 可在 for 循环外部被访问
elem # => 3

# good
arr.each { |elem| puts elem }

# 注意，elem 不可在 each 块外部被访问
elem # => NameError: undefined local variable or method `elem'
```

[slide]
* 不要在多行`if／unless` 中使用`then`

---
```Ruby
# not good
if some_condition then
  # do something
end

# good
if some_condition
  # do something
end
```

[slide]
*  倾向使用三元操作符`?:`而不是`if/then/else/end`结构。前者更为常见且简练。

```Ruby
# not good
result = if some_condition then something else something_else end

# good
result = some_condition ? something : something_else
```

[slide]
* 三元操作符的每个分支只写一个表达式。即不要嵌套三元操作符。嵌套情况请使用`if/else`结构
* 避免使用多行三元操作符`?:`。使用`if/unless`来替代。

```Ruby
# not good
some_condition ? (nested_condition ? nested_something : nested_something_else) : something_else

# good
if some_condition
  nested_condition ? nested_something : nested_something_else
else
  something_else
end
```

[slide]
* 避免使用`!!`

```Ruby
# bad
x = 'test'
# 令人费解的 nil 检查
if !!x
  # do something
end

# good
x = 'test'
unless x.nil?
  # do something
end
```

[slide]
* 对于单行主体，倾向使用`if/unless`修饰语法。另一种方法是使用流程控制`&&/||`

```Ruby
# not good
if some_condition
  do_something
end

# good
do_something if some_condition

# good - 使用流程控制
some_condition && do_something
```

[slide]
* 对于否定条件，倾向使用`unless/until`而不是`if/while`

```Ruby
# not good
unless success?
  puts 'failure'
else
  puts 'success'
end

# good
if success?
  puts 'success'
else
  puts 'failure'
end

# not good
do_something while !some_condition

# good
do_something until some_condition
```

[slide]
* 对于单行主体，倾向使用 while/until 修饰语法。

```Ruby
# not good
while some_condition
  do_something
end

# good
do_something while some_condition
```

[slide]
* 对于可选参数的哈希，省略其外围的花括号

---
```Ruby
# bad
user.set({ name: 'John', age: 45, permissions: { read: true } })

# not good
user.set(name: 'John', age: 45, permissions: { read: true })
```

[slide]
* 对于 DSL 的内部方法调用，同时省略其外围的圆括号与花括号

---
```Ruby
class Person < ActiveRecord::Base
  # 差
  validates(:name, { presence: true, length: { within: 1..10 } })

  # 好
  validates :name, presence: true, length: { within: 1..10 }
end
```

[slide]
*  当被调用方法是当前区块中唯一操作时，倾向使用简短的传参语法

```Ruby
# not good
names.map { |name| name.upcase }

# good
names.map(&:upcase)
```

[slide]
* 对于单行主体，倾向使用`{...}`而不是`do...end`对于多行主体，避免使用`{...}`对于“流程控制”或“方法定义”

---
```Ruby
names = %w(Bozhidar Steve Sarah)

# not good
names.each do |name|
  puts name
end

# good
names.each { |name| puts name }

# not good
names.select do |name|
  name.start_with?('S')
end.map { |name| name.upcase }

# good
names.select { |name| name.start_with?('S') }.map(&:upcase)
```

[slide]
* 优先考虑使用显式区块参数，以避免某些情况下通过创建区块的手法来传递参数给其他区块。此规则对性能有所影响，因为区块会被转换为 Proc 对象。

---
```Ruby
require 'tempfile'

# not good
def with_tmp_dir
  Dir.mktmpdir do |tmp_dir|
    Dir.chdir(tmp_dir) { |dir| yield dir }  # 通过创建区块的手法来传递参数
  end
end

# good
def with_tmp_dir(&block)
  Dir.mktmpdir do |tmp_dir|
    Dir.chdir(tmp_dir, &block)
  end
end

with_tmp_dir do |dir|
  puts "dir is accessible as a parameter and pwd is set: #{dir}"
end
```

[slide]
*  避免在不需要流程控制的情况下使用`return`。

---
```Ruby
# not good
def some_method(some_arr)
  return some_arr.size
end

# good
def some_method(some_arr)
  some_arr.size
end
```

[slide]
* 避免在不需要的情况下使用 self。（只有在调用 self 的修改器时才需要)

```Ruby
# not good
def ready?
  if self.last_reviewed_at > self.last_updated_at
    self.worker.update(self.content, self.options)
    self.status = :in_progress
  end
  self.status == :verified
end

# good
def ready?
  if last_reviewed_at > last_updated_at
    worker.update(content, options)
    self.status = :in_progress
  end
  status == :verified
end
```

[slide]
* 避免局部变量遮蔽方法调用，除非它们具有相同效果

```Ruby
class Foo
  attr_accessor :options

  # 勉强可以
  def initialize(options)
    self.options = options
    # 此处 self.options 与 options 具有相同效果
  end

  # 差
  def do_something(options = {})
    unless options[:when] == :later
      output(self.options[:message])
    end
  end

  # 好
  def do_something(params = {})
    unless params[:when] == :later
      output(options[:message])
    end
  end
end
```
[slide]
* 不要在条件表达式中使用 =（赋值语句）的返回值，除非赋值语句包裹在括号之中。这种惯用法被称作条件表达式中的安全赋值。

```Ruby
# not good - 会出现警告
if v = array.grep(/foo/)
 do_something(v)
 ...
end

# good - 尽管 Ruby 解释器仍会出现警告
if (v = array.grep(/foo/))
 do_something(v)
 ...
end

# good
v = array.grep(/foo/)
if v
 do_something(v)
 ...
end
```

[slide]
* 优先考虑简短的自我赋值语法。

```Ruby
# not good
x = x + y
x = x * y
x = x**y
x = x / y
x = x || y
x = x && y

# good
x += y
x *= y
x **= y
x /= y
x ||= y
x &&= y
```

[slide]
* 当变量尚未初始化时，使用 ||= 对其进行初始化(避开bool值的初始化)

```Ruby
# not good
name = name ? name : 'Bozhidar'

# not good
name = 'Bozhidar' unless name

# good
name ||= 'Bozhidar'
```

[slide]
*

```Ruby

```
