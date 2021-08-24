## 基础语法

### 起步

python是`动态类型`的语言，不需要声明变量的类型。

实际上，python中的变量仅仅只是用来保存一个数据对象的地址。无论是什么数据对象，在内存中创建好数据对象之后，都只是把它的地址保存到变量名中。所以变量名是类型无关的，但它指向的值是类型相关的，可以是数值、字符串、列表、函数、类、对象等等。这些内存**对象中都至少包含3部分：`对象类型`、`对象的引用计数`(用来判断改对象是否可被垃圾回收器回收)、`对象的值`**。

因此，`a = 3`中，变量名a保存的是数据对象 3 的地址，之后可以为其赋值一个字符串`a = "hello"`，这时a保存的是"hello"字符串的地址。在这个类型改变的过程中，a仅仅只是修改了一下地址而已。

#### 第一个 Python 程序

**交互式编程**

交互式编程不需要创建脚本文件，是通过 Python 解释器的交互模式进来编写代码。

linux上你只需要在命令行中输入 Python 命令即可启动交互式编程,提示窗口如下：

命令行中输入 `Python` 命令即可启动`交互式编程`

```python
print ("Hello, Python!")  # Hello, Python!
```



**脚本式编程**

通过脚本参数调用解释器开始执行脚本，直到脚本执行完毕。当脚本执行完成后，解释器不再有效。

所有 Python 文件将以` .py `为扩展名。将以下的源代码拷贝至 hello.py 文件中。

已经设置了 Python 解释器 PATH 变量

```python
print ("Hello, Python!") #Hello, Python!
```

```shell
python hello.py  #终端输入
```



**另外一种运行python的程序的方法**

代码第一行写入执行时的python解释器路径，编辑完后需要对此python文件添加'x'权限

```python
#!/usr/bin/python 

print("Hello, Python!")
```

```shell
$ chmod +x Hello.py     # 脚本文件添加可执行权限
$ ./test.py            #Hello, Python!
```

#### 中文编码

如果输出中文字符 就有可能会碰到中文编码问题。

```python
print ("你好，世界")
 
File "test.py", line 1
SyntaxError: Non-ASCII character '\xe4' in file test.py on line 2, but no encoding declared; see http://www.python.org/peps/pep-0263.html for details
```

Python中默认的编码格式是 ASCII 格式，在没修改编码格式时无法正确打印汉字，所以在读取中文时会报错。

解决方法为只要在文件开头加入` **# -\*- coding: UTF-8 -\*-** `或者

` **# coding=utf-8** `

> **注意：# coding=utf-8 的 =号两边不要空格。**

```python
# -*- coding: UTF-8 -*-
 
print( "你好，世界" )  #你好，世界
```

**注意：**Python3.X 源码文件默认使用`utf-8`编码，所以可以正常解析中文，无需指定 UTF-8 编码。

**注意：**如果你使用编辑器，同时需要设置 py 文件存储的格式为 UTF-8，否则会出现类似以下错误信息：

```python
SyntaxError: (unicode error) ‘utf-8’ codec can’t decode byte 0xc4 in position 0:
invalid continuation byte
```

#### Python 标识符

在 Python 里，标识符由`字母`、`数字`、`下划线`组成。

在 Python 中，所有标识符可以包括英文、数字以及下划线(_)，但`不能以数字开头`。

不要跟关键字（有特殊含义的单词，后面会讲到）和系统保留字（如函数、模块等的名字）冲突。

Python 中的标识符是`区分大小`写的。



以下划线开头的标识符是有特殊意义的。
		以`单下划线开头_foo` 的代表`不能直接访问的类属性`，需通过类提供的接口进行访问，不能用` from xxx import * `而导入。

​		以`双下划线开头`的` __foo `代表类的`私有成员`，以`双下划线开头和结尾`的 `__foo__ `代表 Python 里特殊方法专用的标识，如`__init__() `代表类的构造函数。



Python 可以同一行显示多条语句，方法是用分号 ; 分开，如：

```python
>>> print ('hello');print ('runoob');
hello
runoob
```

#### Python 保留字符

下面的列表显示了在Python中的保留字。这些保留字不能用作常数或变数，或任何其他标识符名称。

所有 Python 的关键字只包含小写字母。

| and      | exec    | not    |
| -------- | ------- | ------ |
| assert   | finally | or     |
| break    | for     | pass   |
| class    | from    | print  |
| continue | global  | raise  |
| def      | if      | return |
| del      | import  | try    |
| elif     | in      | while  |
| else     | is      | with   |
| except   | lambda  | yield  |



#### 行和缩进

Python 的代码块不使用大括号 **{}** 来控制类，函数以及其他逻辑判断。python 最具特色的就是用缩进来写模块。

缩进的空白数量是可变的，但是所有代码块语句必须包含相同的缩进空白数量，这个必须严格执行。

以下实例缩进为四个空格:

```python
if True:
    print ("True")
else:
    print ("False")
```

**IndentationError: unindent does not match any outer indentation level**错误表明，你使用的`缩进方式不一致`，有的是 tab 键缩进，有的是空格缩进，改为一致即可。

如果是 **IndentationError: unexpected indent** 错误, 则 python 编译器是在告诉你可能是`tab和空格没对齐`的问题**"，所有 python 对格式要求非常严格。

因此，在 Python 的代码块中必须使用相同数目的行首缩进空格数。

建议你在每个缩进层次使用 **单个制表符** 或 **两个空格** 或 **四个空格** , 切记不能混用

#### 多行语句

Python语句中一般以新行作为语句的结束符。

但是我们可以使用斜杠（` \`）将一行的语句分为多行显示，如下所示：

```python
total = item_one + \
        item_two + \
        item_three
```

语句中包含 [], {} 或 () 括号就不需要使用多行连接符。如下实例：

```python
days = ['Monday', 'Tuesday', 'Wednesday',
        'Thursday', 'Friday']
```

#### Python 引号

Python 可以使用引号( `'` )、双引号( `"` )、三引号( `'''` 或 `"""`) 来表示字符串，引号的开始与结束必须是相同类型的。

其中`三引号`可以由多行组成，编写多行文本的快捷语法，常用于文档字符串，`在文件的特定地点，被当做注释`。

```python
word = 'word'
sentence = "这是一个句子。"
paragraph = """这是一个段落。
包含了多个语句"""
```



#### Python空行

函数之间或类的方法之间用空行分隔，表示一段新的代码的开始。类和函数入口之间也用一行空行分隔，以突出函数入口的开始。

空行与代码缩进不同，空行并不是Python语法的一部分。书写时不插入空行，Python解释器运行也不会出错。但是空行的作用在于分隔两段不同功能或含义的代码，便于日后代码的维护或重构。

**记住：空行也是程序代码的一部分。**



#### 多个语句构成代码组

缩进相同的一组语句构成一个代码块，我们称之代码组。

像if、while、def和class这样的复合语句，首行以关键字开始，以冒号( : )结束，该行之后的一行或多行代码构成代码组。

我们将首行及后面的代码组称为一个子句(clause)。

如下实例：

```python
if expression : 
   suite 
elif expression :  
   suite  
else :  
   suite 
```



#### print(),input()

使用`input()`函数获取键盘输入(`字符串`)
使用`int()`函数将输入的字符串转换成整数
使用`print()`函数输出带占位符的字符串

```python
a = int(input('a = '))
b = int(input('b = '))
print('%d + %d = %d' % (a, b, a + b))
print('%d - %d = %d' % (a, b, a - b))
print('%d * %d = %d' % (a, b, a * b))
print('%d / %d = %f' % (a, b, a / b))
print('%d // %d = %d' % (a, b, a // b))
print('%d %% %d = %d' % (a, b, a % b))
print('%d ** %d = %d' % (a, b, a ** b))
```

**说明**：上面的print函数中输出的字符串使用了占位符语法，其中`%d`是整数的占位符，`%f`是小数的占位符，`%%`表示百分号（因为百分号代表了占位符，所以带占位符的字符串中要表示百分号必须写成`%%`），字符串之后的`%`后面跟的变量值会替换掉占位符然后输出到终端中



**换行输出**

在输出的时候，如果有`\n`那么，此时`\n`后的内容会在另外一行显示

```python
print("1234567890-------")   # 会在一行显示

print("1234567890\n-------") # 一行显示1234567890，另外一行显示-------
```


**常用的格式符号**

| 格式符号 |             转换             |
| :------: | :--------------------------: |
|    %c    |             字符             |
|    %s    | 通过str() 字符串转换来格式化 |
|    %i    |       有符号十进制整数       |
|    %d    |       有符号十进制整数       |
|    %u    |       无符号十进制整数       |
|    %o    |          八进制整数          |
|    %x    |   十六进制整数（小写字母）   |
|    %X    |   十六进制整数（大写字母）   |
|    %e    |     索引符号（小写'e'）      |
|    %E    |     索引符号（大写“E”）      |
|    %f    |           浮点实数           |
|    %g    |       ％f和％e 的简写        |
|    %G    |        ％f和％E的简写        |



**python2版本中**

raw_input()

```python
password = raw_input("请输入密码:")
print '您刚刚输入的密码是:', password
```

**注意**:

- raw_input()的小括号中放入的是，提示信息，用来在获取数据之前给用户的一个简单提示
- raw_input()在从键盘获取了数据以后，会存放到等号右边的变量中
- raw_input()会把用户输入的任何值都作为字符串来对待



**python3版本中**

没有raw_input()函数，只有input()

并且 python3中的input与python2中的raw_input()功能一样



### 注释

注释是编程语言的一个重要组成部分，用于在源代码中解释代码的作用从而增强程序的可读性和可维护性，当然也可以将源代码中不需要参与运行的代码段通过注释来去掉，这一点在调试程序的时候经常用到。注释在随源代码进入预处理器或编译时会被移除，不会在目标代码中保留也不会影响程序的执行结果。

1. `单行注释 `- 以#和空格开头的部分
2. `多行注释 `- 三个引号开头，三个引号结尾, 三个单引号(''')或三个双引号(""")。

```python
"""
第一个Python程序 - hello, world!

Version: 0.1
"""
print('hello, world!')
# print("你好, 世界！")
```



### 运算符

Python支持多种运算符，下表大致按照优先级`从高到低`的顺序列出了所有的运算符，运算符的优先级指的是多个运算符同时出现时，先做什么运算然后再做什么运算。

| 运算符                                          | 描述                           |
| ----------------------------------------------- | ------------------------------ |
| `[]` `[:]`                                      | 下标，切片                     |
| `**`                                            | 指数                           |
| `~` `+` `-`                                     | 按位取反, 正负号               |
| `*` `/` `%` `//`                                | 乘，除，模，整除               |
| `+` `-`                                         | 加，减                         |
| `>>` `<<`                                       | 右移，左移                     |
| `&`                                             | 按位与                         |
| `^` `|`                                         | 按位异或，按位或               |
| `<=` `<` `>` `>=`                               | 小于等于，小于，大于，大于等于 |
| `==` `!=`                                       | 等于，不等于                   |
| `is` `is not`                                   | 身份运算符                     |
| `in` `not in`                                   | 成员运算符                     |
| `not` `or` `and`                                | 逻辑运算符                     |
| `=` `+=` `-=` `*=` `/=` `%=` `//=` `**=` `&=` ` | =` `^=` `>>=` `<<=`            |

> **说明：** 在实际开发中，如果搞不清楚运算符的优先级，可以使用括号来确保运算的执行顺序。



```python
"""
赋值运算符和复合赋值运算符
"""
a = 10
b = 3
a += b        # 相当于：a = a + b
a *= a + 2    # 相当于：a = a * (a + 2)
print(a)      # 算一下这里会输出什么
```

```python
"""
比较运算符和逻辑运算符的使用
"""

flag0 = 1 == 1
flag1 = 3 > 2
flag2 = 2 < 1
flag3 = flag1 and flag2
flag4 = flag1 or flag2
flag5 = not (1 != 2)
print('flag0 =', flag0)    # flag0 = True
print('flag1 =', flag1)    # flag1 = True
print('flag2 =', flag2)    # flag2 = False
print('flag3 =', flag3)    # flag3 = False
print('flag4 =', flag4)    # flag4 = True
print('flag5 =', flag5)    # flag5 = False
```

> **说明**：比较运算符的优先级高于赋值运算符，所以`flag0 = 1 == 1`先做`1 == 1`产生布尔值`True`，再将这个值赋值给变量`flag0`。`print`函数可以输出多个值，多个值之间可以用`,`进行分隔，输出的内容之间默认以空格分开。

### 等值和大小比较

#### 等值、大小比较

在python中，**只要两个对象的类型相同，且它们是内置类型(字典除外)，那么这两个对象就能进行比较**。关键词：`内置类型`、`同类型`。所以，两个对象如果类型不同，就没法比较，比如数值类型的数值不能和字符串类型的数值或字母比较。

对于python中的等值、不等值、大小比较的规则为何如此，与`Class的运算符重载`有关

其实自定义的类型(python 3.x中类Class就是类型)也可以进行比较，只不过要对类的比较操作符进行运算符重载。

比较操作符有：

```python
==  !=  <  <=  >  >=
```

例如，下面的比较全部返回True。

```python
bool(1 < 2)
bool('a' < 'c')
bool('A' < 'a')    # 字符大小：A < Z < a < z

bool([1,2,2] < [1,2,3])
bool((1,2,2) < (1,2,3))
bool({1,2,2} < {1,2,3})
```

python中同类型的内置类型对象(字典除外)，都是从左开始，一个一个元素向后比较，就算中间遇到嵌套的容器结构(如list/tuple/Set)，也会递归到嵌套的结构中去一个个比较。

```python
>>> bool([1,2,[3,3]] < [1,2,[3,4]])
True
```

注意，**`None`对象只能参与等值和不等值比较**，不能参与大小比较。

```python
>>> None == None
True
>>> None != None
False
>>> None <= None
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
TypeError: '<=' not supported between instances of 'NoneType' and 'NoneType'
```

python支持连续比较，**连续比较时等价于使用and运算**。例如：

```python
a < b < c    等价于  a < b and b < c
a < b > c    等价于  a < b and b > c
a == b < c   等价于  a == b and b < c
```

一定要注意连续比较时的逻辑。例如`1 == 2 < 3`返回False，但它等价于`1 == 2 and 2 < 3`，而不是先评估`1==2`得到False，再将比较的结果与后面的做比较，即等价于`False < 3`，这意味着`0<3`，这实际上是返回True的。

```python
>>> 1 == 2 < 3
False

>>> (1==2) < 3
True
```

连续比较是一种比较语法，它不仅限于数值的连续比较，还支持其它类型。比如：

```python
>>> "ac" > "ab" < "ad"
True
```

#### is 和 ==

有两种比较数据对象是否相等的方式："`==`"和"`is`",
它们的否定形式分别为"`!=`"和"`is not`"。

它们都是比较表达式，但却是完全不同的比较方式：

- **"=="和"!="符号比较的是`数据的值`是否相等、相同**
- **"is"比较的是两个数据对象在`内存中`是否是同一个数据对象。换句话说，比较的是`内存地址`**

等号比较很容易理解，只要值相等就为True，否则为False。

is比较的是内存中的数据对象。例如：

```python
>>> a = 1000
>>> b = 1000
>>> a == b
True

>>> a is b
False
```

a和b在数值上是相等的，所以`a == b`返回True。但它们分别指向的内存中的数据对象1000，却不是同一个数据对象，所以`a is b`返回False。如下图，内存中有两个1000。



### 变量以及类型



在程序设计中，变量是一种存储数据的载体。计算机中的变量是实际存在的数据或者说是存储器中存储数据的一块内存空间，变量的值可以被读取和修改，这是所有计算和控制的基础。计算机能处理的数据有很多种类型，除了数值之外还可以处理文本、图形、音频、视频等各种各样的数据，那么不同的数据就需要定义不同的存储类型。



#### 变量命名

对于每个变量我们需要给它取一个名字，就如同我们每个人都有属于自己的响亮的名字一样。在Python中，变量命名需要遵循以下这些必须遵守硬性规则和强烈建议遵守的非硬性规则。

- 硬性规则：
  - 变量名由字母（广义的Unicode字符，不包括特殊字符）、数字和下划线构成，数字不能开头。
  - 大小写敏感（大写的`a`和小写的`A`是两个不同的变量）。
  - 不要跟关键字（有特殊含义的单词，后面会讲到）和系统保留字（如函数、模块等的名字）冲突。
- PEP 8要求：
  - 用小写字母拼写，多个单词用下划线连接。
  - 受保护的实例属性用单个下划线开头。
  - 私有的实例属性用两个下划线开头。

- 约定俗成的命名方式：
  1. 常量以全大写字符表示
  2. 普通变量、函数名、方法名都以小写字母开头命名
  3. 模块名、包名以全小写字母命名
  4. 类名以大写字母开头



#### 变量的使用

```python
"""
使用变量保存数据并进行加减乘除运算

"""
a = 321
b = 12
print(a + b)    # 333
print(a - b)    # 309
print(a * b)    # 3852
print(a / b)    # 26.75
```

**程序就是用来处理数据的，而变量就是用来存储数据的**

#### 变量赋值

python中变量赋值的几种形式。

```python
x = "long"                  # (1).基本形式
x, y = "long", "shuai"      # (2).元组对应赋值
[x, y] = ["long", "shuai"]  # (3).列表对应赋值

#在python中，只要是序列，都可以这样赋值	
a, b, c, d = "long"         # (4).序列赋值
#a, b, c, d = ("shell","perl","php","python")
#a, b, c, d = ["shell","perl","php","python"]

#多出来的元素会全部以列表的方式赋值给最后一个变量名。
a, *b = 'long'              # (5).解包赋值   a="l"  b=["o", "n", "g"]
#a, *b = ("shell","perl","php","python")
#a, *b = ["shell","perl","php","python"]

#python赋值时，总是先计算"="右边的结果，然后将结果按照赋值方式赋值给"="左边的变量。所以，这里的过程是先将"long"赋值给变量b，再将b赋值给变量a。
a = b = "long"              # (6).多目标赋值
#等价于：
b = "long"
a = b

a += 3                      # (7).二元赋值表达式

#是将序列进行嵌套序列赋值，将'lo'赋值给元组(a, b)，'ng'赋值给c，元组又进一步赋值a='l', b='o'。
((a, b), c) = ('lo','ng')   # (8).嵌套赋值序列

#for循环使用
for (a, b, c) in [(1, 2, 3), (4, 5, 6)]:...
for ((a, b), c) in [((1, 2), 3), ((4, 5), 6)]:...
    
#和函数参数使用
def f(((a, b), c)):...
f(((1, 2), 3))
```

注意：**python的数值是不可变对象，无法在原处修改数据，所以不支持自增、自减**。

```python
a++
++a
a--
--b
```

当使用`逗号`的时候，python总会临时或永久地建立成`tuple`来保存元素，所以`x, y = "long", "shuai"`在内部完全等价于`(x, y) = ("long", "shuai")`。

实际上，列表元素也可以赋值给元组，或者元组赋值给列表，只要两边的序列元素个数能对应，无所谓左右两边的序列类型：

```python
>>> (x,y) = (1,2)
>>> (x,y) = [1,2]
>>> [x,y] = (1,2)
>>> [x,y] = [1,2]
>>> (x,y) = 'ab'
>>> [x,y] = 'ab'
```

变量和序列中的元素必须一一对应。如果变量名与元素个数不同，则会报错，除非只有一个变量名，这表示将整个序列赋值给这个变量。

如果想要将序列中的元素赋值给不等的变量，可以考虑先将序列进行切片。

```python
>>> str='long'
>>> a, b, c = list(str[:2]) + [str[2:]]
>>> a,b,c
('l', 'o', 'ng')
```



#### 练习

##### 华氏温度转换为摄氏温度

> 提示：华氏温度到摄氏温度的转换公式为：$C=(F - 32) / 1.8。

```python
"""
将华氏温度转换为摄氏温度
"""

f = float(input('请输入华氏温度: '))
c = (f - 32) / 1.8
print('%.1f华氏度 = %.1f摄氏度' % (f, c))
```

> **说明**：在使用`print`函数输出时，也可以对字符串内容进行格式化处理，上面`print`函数中的字符串`%1.f`是一个占位符，稍后会由一个`float`类型的变量值替换掉它。同理，如果字符串中有`%d`，后面可以用一个`int`类型的变量值替换掉它，而`%s`会被字符串的值替换掉。除了这种格式化字符串的方式外，还可以用下面的方式来格式化字符串，其中`{f:.1f}`和`{c:.1f}`可以先看成是`{f}`和`{c}`，表示输出时会用变量`f`和变量`c`的值替换掉这两个占位符，后面的`:.1f`表示这是一个浮点数，小数点后保留1位有效数字。
>
> ```python
> print(f'{f:.1f}华氏度 = {c:.1f}摄氏度')
> ```



##### 计算计算周长和面积

```python
"""
输入半径计算圆的周长和面积
"""
radius = float(input('请输入圆的半径: '))
perimeter = 2 * 3.1416 * radius
area = 3.1416 * radius * radius
print('周长: %.2f' % perimeter)
print('面积: %.2f' % area)
```

##### 输入年份判断是不是闰年。

```python
"""
输入年份 如果是闰年输出True 否则输出False
"""

year = int(input('请输入年份: '))

# 如果代码太长写成一行不便于阅读 可以使用\对代码进行折行
is_leap = year % 4 == 0 and year % 100 != 0 or \
          year % 400 == 0
print(is_leap)
```

> **说明**：比较运算符会产生布尔值，而逻辑运算符`and`和`or`会对这些布尔值进行组合，最终也是得到一个布尔值，闰年输出`True`，平年输出`False`。





### 条件语句

#### if语句格式

Python条件语句是通过一条或多条语句的执行结果（True或者False）来决定执行的代码块。

Python程序语言指定任何非0和非空（null）值为true，0 或者 null为false。

要构造分支结构可以使用`if`、`elif`和`else`关键字。

Python 编程中 if 语句用于控制程序的执行，基本形式为：

```python
if 判断条件：
    执行语句……
else：
    执行语句……
```

```python
if 判断条件1:
    执行语句1……
elif 判断条件2:
    执行语句2……
elif 判断条件3:
    执行语句3……
else:
    执行语句4……
```



python中没有其他语言中的`三元表达式`，不过有类似的实现方法

```python
x = int(input("please enter first integer:"))
y = int(input("please enter second integer:"))

#一般的写法
if (x == y):
    print("两数相同！")
elif(x > y):
    print("较大的数为：",x)
else:
     porint("较大的数为：",y)

# 三目运算符写法
print(x if(x>y) else y)
```



#### 实例

```python
"""
用户身份验证
"""

username = input('请输入用户名: ')
password = input('请输入口令: ')

# 用户名是admin且密码是123456则身份验证成功否则身份验证失败
if username == 'admin' and password == '123456':
    print('身份验证成功!')
else:
    print('身份验证失败!')
```



```python
"""
分段函数求值

        3x - 5  (x > 1)
f(x) =  x + 2   (-1 <= x <= 1)
        5x + 3  (x < -1)
"""

x = float(input('x = '))
if x > 1:
    y = 3 * x - 5
elif x >= -1:
    y = x + 2
else:
    y = 5 * x + 3
print('f(%.2f) = %.2f' % (x, y))



"""
分支结构是可以嵌套的
"""

x = float(input('x = '))
if x > 1:
    y = 3 * x - 5
else:
    if x >= -1:
        y = x + 2
    else:
        y = 5 * x + 3
print('f(%.2f) = %.2f' % (x, y))

```

> **说明：** 提倡代码“扁平化”是因为嵌套结构的嵌套层次多了之后会严重的影响代码的可读性，所以能使用扁平化的结构时就不要使用嵌套。



由于 python 并`不支持 switch 语句`，所以多个条件判断，只能用 elif 来实现，如果判断需要多个条件需同时判断时，可以使用 or （或），表示两个条件有一个成立时判断条件成功；使用 and （与）时，表示只有两个条件同时成立的情况下，判断条件才成功。

```python
# -*- coding: UTF-8 -*-

# 例3：if语句多个条件
 
num = 9
if num >= 0 and num <= 10:    # 判断值是否在0~10之间
    print 'hello'
# 输出结果: hello
 
num = 10
if num < 0 or num > 10:    # 判断值是否在小于0或大于10
    print 'hello'
else:
    print 'undefine'
# 输出结果: undefine
 
num = 8
# 判断值是否在0~5或者10~15之间
if (num >= 0 and num <= 5) or (num >= 10 and num <= 15):    
    print 'hello'
else:
    print 'undefine'
# 输出结果: undefine
```

> **说明：**当if有多个条件时可使用括号来区分判断的先后顺序，括号中的判断优先执行，此外 and 和 or 的优先级低于>（大于）、<（小于）等判断符号，即大于和小于在没有括号的情况下会比与或要优先判断。



简单的语句组: 在同一行的位置上使用if条件判断语句

```python
# -*- coding: UTF-8 -*-
 
var = 100 
if ( var  == 100 ) : print "变量 var 的值为100"   # 变量 var 的值为100
print "Good bye!"  # Good bye!
```

#### 练习

##### 英制单位英寸与公制单位厘米互换

```python
"""
英制单位英寸和公制单位厘米互换
"""

value = float(input('请输入长度: '))
unit = input('请输入单位: ')
if unit == 'in' or unit == '英寸':
    print('%f英寸 = %f厘米' % (value, value * 2.54))
elif unit == 'cm' or unit == '厘米':
    print('%f厘米 = %f英寸' % (value, value / 2.54))
else:
    print('请输入有效的单位')
```

##### 百分制成绩转换为等级制成绩

> **要求**：如果输入的成绩在90分以上（含90分）输出A；80分-90分（不含90分）输出B；70分-80分（不含80分）输出C；60分-70分（不含70分）输出D；60分以下输出E。

```python
"""
百分制成绩转换为等级制成绩
"""
score = float(input('请输入成绩: '))
if score >= 90:
    grade = 'A'
elif score >= 80:
    grade = 'B'
elif score >= 70:
    grade = 'C'
elif score >= 60:
    grade = 'D'
else:
    grade = 'E'
print('对应的等级是:', grade)
```

##### 输入三条边长，如果能构成三角形就计算周长和面积

```python
"""
判断输入的边长能否构成三角形，如果能则计算出三角形的周长和面积
"""

a = float(input('a = '))
b = float(input('b = '))
c = float(input('c = '))
if a + b > c and a + c > b and b + c > a:
    print('周长: %f' % (a + b + c))
    p = (a + b + c) / 2
    area = (p * (p - a) * (p - b) * (p - c)) ** 0.5
    print('面积: %f' % (area))
else:
    print('不能构成三角形')
```

> **说明：** 上面使用的通过边长计算三角形面积的公式叫做[海伦公式](https://zh.wikipedia.org/zh-hans/海伦公式)。

##### 猜拳游戏

```python
import random

player = input('请输入：剪刀(0)  石头(1)  布(2):')
player = int(player)

computer = random.randint(0,2)

# 用来进行测试
#print('player=%d,computer=%d',(player,computer))

if ((player == 0) and (computer == 2)) or ((player ==1) and (computer == 0)) or ((player == 2) and (computer == 1)):
    print('获胜，哈哈，你太厉害了'
elif player == computer:
     print('平局，要不再来一局')
else:
     print('输了，不要走，洗洗手接着来，决战到天亮')
```



### 循环语句

####  while 语句

Python 编程中 while 语句用于循环执行程序，即在某条件下，循环执行某段程序，以处理需要重复处理的相同任务。其基本形式为：

```python
while 判断条件(condition)：
    执行语句(statements)……
```

执行语句可以是单个语句或语句块。判断条件可以是任何表达式，任何非零、或非空（null）的值均为true。

当判断条件假 false 时，循环结束。

```python
"""
猜数字游戏
"""
import random

answer = random.randint(1, 100)
counter = 0
while True:
    counter += 1
    number = int(input('请输入: '))
    if number < answer:
        print('大一点')
    elif number > answer:
        print('小一点')
    else:
        print('恭喜你猜对了!')
        break
print('你总共猜了%d次' % counter)
if counter > 7:
    print('你的智商余额明显不足')
```



#### for-in循环

Python `for`循环可以遍历任何序列的项目，如一个列表或者一个字符串。

```python
for iterating_var in sequence:
   statements(s)

#############################
name = 'ixfosa'

for x in name:
    print(x)
```

```python
for 临时变量 in 列表或者字符串等:
	循环满足条件时执行的代码
else:
	循环不满足条件时执行的代码
    
###########################
name = ''

for x in name:
    print(x)
else:
    print("没有数据"
```



可以通过在循环中使用分支结构的方式来实现相同的功能

```python
"""
用for循环实现1~100之间的偶数求和
"""

sum = 0
for x in range(1, 101):
    if x % 2 == 0:
        sum += x
print(sum)
```

`range(1, 101)`可以用来构造一个从1到100的范围，当我们把这样一个范围放到`for-in`循环中，就可以通过前面的循环变量`x`依次取出从1到100的整数。当然，`range`的用法非常灵活，下面给出了一个例子：

- `range(101)`：可以用来产生0到100范围的整数，需要注意的是取不到101。
- `range(1, 101)`：可以用来产生1到100范围的整数，相当于前面是闭区间后面是开区间。
- `range(1, 101, 2)`：可以用来产生1到100的奇数，其中2是步长，即每次数值递增的值。
- `range(100, 0, -2)`：可以用来产生100到1的偶数，其中-2是步长，即每次数字递减的值。



1~100之间的偶数求和。

```python
"""
用for循环实现1~100之间的偶数求和
"""

sum = 0
for x in range(2, 101, 2):
    sum += x
print(sum)
```



------

如果明确的知道循环执行的次数或者要对一个容器进行迭代，那么我们推荐使用`for-in`循环

```python
# -*- coding: UTF-8 -*-

for letter in 'Python':    
   print '当前字母 :', letter
 
    
fruits = ['banana', 'apple',  'mango']
for fruit in fruits:        
   print '当前水果 :', fruit
```

```python
# -*- coding: UTF-8 -*-
 
fruits = ['banana', 'apple',  'mango']
for index in range(len(fruits)):         #通过序列索引迭代
   print '当前水果 :', fruits[index]
 
print "Good bye!"
```

> 以上实例我们使用了内置函数 `len()` 和 `range()`,函数 len() 返回列表的长度，即元素的个数。 range返回一个序列的数。



#### 循环嵌套

**Python for 循环嵌套语法：**

```python
for iterating_var in sequence:
   for iterating_var in sequence:
      statements(s)
   statements(s)
```

**Python while 循环嵌套语法：**

```python
while expression:
   while expression:
      statement(s)
   statement(s)
```



使用了嵌套循环输出2~100之间的素数：

```python
# -*- coding: UTF-8 -*-
 
i = 2
while(i < 100):
   j = 2
   while(j <= (i/j)):
      if not(i%j): break
      j = j + 1
   if (j > i/j) : print i, " 是素数"
   i = i + 1
```



#### 练习

##### 输入一个正整数判断是不是素数。

> **提示**：素数指的是只能被1和自身整除的大于1的整数。

```python
"""
输入一个正整数判断它是不是素数
"""
from math import sqrt

num = int(input('请输入一个正整数: '))
end = int(sqrt(num))
is_prime = True
for x in range(2, end + 1):
    if num % x == 0:
        is_prime = False
        break
if is_prime and num != 1:
    print('%d是素数' % num)
else:
    print('%d不是素数' % num)
```

##### 输入两个正整数，计算它们的最大公约数和最小公倍数。

> **提示**：两个数的最大公约数是两个数的公共因子中最大的那个数；两个数的最小公倍数则是能够同时被两个数整除的最小的那个数。

```python
"""
输入两个正整数计算它们的最大公约数和最小公倍数
"""

x = int(input('x = '))
y = int(input('y = '))
# 如果x大于y就交换x和y的值
if x > y:
    # 通过下面的操作将y的值赋给x, 将x的值赋给y
    x, y = y, x
# 从两个数中较的数开始做递减的循环
for factor in range(x, 0, -1):
    if x % factor == 0 and y % factor == 0:
        print('%d和%d的最大公约数是%d' % (x, y, factor))
        print('%d和%d的最小公倍数是%d' % (x, y, x * y // factor))
        break
```

##### 打印如下所示的三角形图案。

```
*
**
***
****
*****
    *
   **
  ***
 ****
*****
    *
   ***
  *****
 *******
*********
```

参考答案：

```python
"""
打印三角形图案
"""

row = int(input('请输入行数: '))
for i in range(row):
    for _ in range(i + 1):
        print('*', end='')
    print()


for i in range(row):
    for j in range(row):
        if j < row - i - 1:
            print(' ', end='')
        else:
            print('*', end='')
    print()

for i in range(row):
    for _ in range(row - i - 1):
        print(' ', end='')
    for _ in range(2 * i + 1):
        print('*', end='')
    print()
```

##### 九九表

```python
"""
输出乘法口诀表(九九表)
"""

for i in range(1, 10):
    for j in range(1, i + 1):
        print('%d*%d=%d' % (i, j, i * j), end='\t')
    print()
```



### break,continue,pass



- break/continue只能用在循环中，除此以外不能单独使用
- break/continue在嵌套循环中，只对`最近的一层循环`起作用



#### break



**break的作用：用来结束整个循环**



1. for循环

```python
#普通的循环示例如下：

name = 'ixfosa'
 
for x in name:
	print('----')
    print(x)
    
#带有break的循环示例如下:

name = 'ixfosa'

for x in name:
    print('----')
    if x == 'o': 
    	break
	print(x)
```



1. while循环

```python
#普通的循环示例如下：

  i = 0

  while i<10:
      i = i+1
      print('----')
      print(i)
        
#带有break的循环示例如下:

  i = 0

  while i<10:
      i = i+1
      print('----')
      if i==5:
          break
      print(i)
```

#### continue



**continue的作用：用来结束本次循环，紧接着执行下一次的循环**



1. for循环

```python
#带有continue的循环示例如下:

  name = 'ixfosa'

  for x in name:
      print('----')
      if x == 'o': 
          continue
      print(x)
```

1. while循环

```python
#带有continue的循环示例如下:

  i = 0

  while i<10:
      i = i+1
      print('----')
      if i==5:
          continue
      print(i)
```



#### pass

Python pass 是空语句，是为了保持程序结构的完整性。

**pass** 不做任何事情，一般用做占位语句

```python
# -*- coding: UTF-8 -*- 
 
# 输出 Python 的每个字母
for letter in 'Python':
   if letter == 'h':
      pass
      print '这是 pass 块'
   print '当前字母 :', letter
 
print "Good bye!"
```



python2.x：

```python
def function():
    # 空函数在Python2.x版本中pass是必须的
    pass
```

python3.x

```python
def function():
    # 在Python3.x的时候pass可以写或不写
    pass
```

#### 练习

##### 寻找**水仙花数**。

> **说明**：水仙花数也被称为超完全数字不变数、自恋数、自幂数、阿姆斯特朗数，它是一个3位数，该数字每个位上数字的立方之和正好等于它本身，例如：1^3 + 5^3+ 3^3=153。

```python
"""
找出所有水仙花数
"""

for num in range(100, 1000):
    low = num % 10
    mid = num // 10 % 10
    high = num // 100
    if num == low ** 3 + mid ** 3 + high ** 3:
        print(num)
```

在上面的代码中，我们通过整除和求模运算分别找出了一个三位数的个位、十位和百位，这种小技巧在实际开发中还是常用的。用类似的方法，我们还可以实现将一个正整数反转，例如：将12345变成54321，代码如下所示。

```python
"""
正整数的反转
"""

num = int(input('num = '))
reversed_num = 0
while num > 0:
    reversed_num = reversed_num * 10 + num % 10
    num //= 10
print(reversed_num)
```

##### 百钱百鸡问题。

> **说明**：百钱百鸡是我国古代数学家[张丘建](https://baike.baidu.com/item/张丘建/10246238)在《算经》一书中提出的数学问题：鸡翁一值钱五，鸡母一值钱三，鸡雏三值钱一。百钱买百鸡，问鸡翁、鸡母、鸡雏各几何？翻译成现代文是：公鸡5元一只，母鸡3元一只，小鸡1元三只，用100块钱买一百只鸡，问公鸡、母鸡、小鸡各有多少只？

```python
"""
《百钱百鸡》问题
"""

for x in range(0, 20):
    for y in range(0, 33):
        z = 100 - x - y
        if 5 * x + 3 * y + z / 3 == 100:
            print('公鸡: %d只, 母鸡: %d只, 小鸡: %d只' % (x, y, z))
```

上面使用的方法叫做**穷举法**，也称为**暴力搜索法**，这种方法通过一项一项的列举备选解决方案中所有可能的候选项并检查每个候选项是否符合问题的描述，最终得到问题的解。这种方法看起来比较笨拙，但对于运算能力非常强大的计算机来说，通常都是一个可行的甚至是不错的选择，而且问题的解如果存在，这种方法一定能够找到它。

##### CRAPS赌博游戏

> **说明**：CRAPS又称花旗骰，是美国拉斯维加斯非常受欢迎的一种的桌上赌博游戏。该游戏使用两粒骰子，玩家通过摇两粒骰子获得点数进行游戏。简单的规则是：玩家第一次摇骰子如果摇出了7点或11点，玩家胜；玩家第一次如果摇出2点、3点或12点，庄家胜；其他点数玩家继续摇骰子，如果玩家摇出了7点，庄家胜；如果玩家摇出了第一次摇的点数，玩家胜；其他点数，玩家继续要骰子，直到分出胜负。

```python
"""
Craps赌博游戏
我们设定玩家开始游戏时有1000元的赌注
游戏结束的条件是玩家输光所有的赌注
"""
from random import randint

money = 1000
while money > 0:
    print('你的总资产为:', money)
    needs_go_on = False
    while True:
        debt = int(input('请下注: '))
        if 0 < debt <= money:
            break
    first = randint(1, 6) + randint(1, 6)
    print('玩家摇出了%d点' % first)
    if first == 7 or first == 11:
        print('玩家胜!')
        money += debt
    elif first == 2 or first == 3 or first == 12:
        print('庄家胜!')
        money -= debt
    else:
        needs_go_on = True
    while needs_go_on:
        needs_go_on = False
        current = randint(1, 6) + randint(1, 6)
        print('玩家摇出了%d点' % current)
        if current == 7:
            print('庄家胜')
            money -= debt
        elif current == first:
            print('玩家胜')
            money += debt
        else:
            needs_go_on = True
print('你破产了, 游戏结束!')
```



## 数据类型

### 概述

Python 中的变量不需要声明。每个变量在使用前都必须赋值，变量赋值以后该变量才会被创建。

在 Python 中，变量就是变量，它没有类型，我们所说的"类型"是变量所指的内存中对象的类型。

等号（=）用来给变量赋值。

等号（=）运算符左边是一个变量名,等号（=）运算符右边是存储在变量中的值。

```python
counter = 100          # 整型变量
miles   = 1000.0       # 浮点型变量
name    = "runoob"     # 字符串

print (counter) #100
print (miles) #1000.0
print (name) #runoob


#多个变量赋值, 创建一个整型对象，值为 1，从后向前赋值，三个变量被赋予相同的数值。
a = b = c = 1

#为多个对象指定多个变量
a, b, c = 1, 2, "runoob"
```

Python3 中有六个标准的数据类型：

- Number（数字）
- String（字符串）
- List（列表）
- Tuple（元组）
- Set（集合）
- Dictionary（字典）



数据类型分为`可变`、`不可变`。可变对象表示可以原处修改该数据对象，不可变对象表示必须创建新对象来保存修改后的数据。

Python3 的六个标准数据类型中：

- **不可变数据（3 个）：**Number（数字）、String（字符串）、Tuple（元组）；
- **可变数据（3 个）：**List（列表）、Dictionary（字典）、Set（集合）。



**可变对象,不可变对象**

```python
#对于可变对象，比如有一个列表L，查看它的id以及第一个元素的id。
>>> L = ['a', 'b', 'c']
>>> id(L)
23099392
>>> id(L[0])
57027008


#可变对象(不仅仅是这里的序列、列表)意味着修改该数据对象，不会在内存中新创建另一个内存空间来存放新数据对象。例如，修改这个列表中的第一个元素为"aa"。
#发现列表的id并没有改变，也就是列表的内存地址仍然是那一块。这表示列表是可变序列。
#但是，如果查看第一个元素的id，会发现已经改变了：

>>> L[0]="aa"
>>> L
['aa', 'b', 'c']

>>> id(L)
23099392

>>> id(L[0])
61863232

#这说明，虽然列表的内存地址没有改变，但是列表中的第一个元素的地址已经改变了。
#也就是说，修改列表中的第一个元素过程中，创建了一个新的内存块来存放新的字符串，原始的那个字符串"a"因为没有被引用了，它将等待垃圾回收器的回收。不管如何，列表的地址一直没变。

#为什么修改列表中的元素需要创建新的内存块？这是因为这个元素是字符串，而字符串是不可变对象。
```

>  这意味着在内存中有一片区域，这片区域存放的数据类型是列表(每个数据对象都有自己的类型声明)，列表包含至少3个数据内存块，分别存放了3个字符串类型的数据(实际上是存放了这3个字符对象的地址)



**不可变对象意味着，不能在原始内存地址块中修改数据，必须新创建一个地址块来保存修改后的数据对象**。正如上面修改字符串"a"为"aa"的结果。

假如列表L中的第一个元素仍然是一个嵌套在L中的列表，因为列表是可变对象，现在修改L的第一个元素，这第一个元素的地址不会改变。

```python
>>> L = [['a'], 'b', 'c']

>>> id(L[0])
23099392
>>> L[0][0] = "aa"
>>> id(L[0])
23099392

#这里改变的只有内嵌的列表中第一个元素的地址。
#虽然可变对象可以原处修改数据，不会创建新对象，但并不意味着操作可变对象总是不会创建新对象，这取决于对可变对象做什么操作，比如分片操作一定会创建新对象。
```





### type,isinstance 

在Python中可以使用`type`函数和`isinstance`函数对变量的类型进行检查。

```python
"""
使用type()检查变量的类型
"""
a = 100
b = 12.345
c = 1 + 5j
d = 'hello, world'
e = True
print(type(a))    # <class 'int'>
print(type(b))    # <class 'float'>
print(type(c))    # <class 'complex'>
print(type(d))    # <class 'str'>
print(type(e))    # <class 'bool'>

#使用isinstance 检查变量的类型
>>> a = 111
>>> isinstance(a, int)
True
>>>
```

isinstance 和 type 的区别在于：

- type()不会认为子类是一种父类类型。
- isinstance()会认为子类是一种父类类型。

```python
>>> class A:
...     pass
... 
>>> class B(A):
...     pass
... 

>>> isinstance(A(), A)
True
>>> type(A()) == A 
True
>>> isinstance(B(), A)
True
>>> type(B()) == A
False
```



### 类型转换

| 函数                                                         | 描述                                                |
| :----------------------------------------------------------- | :-------------------------------------------------- |
| `int(x [,base\])`                                            | 将x转换为一个整数                                   |
| [long(x [,base\] )](https://www.runoob.com/python/python-func-long.html) | 将x转换为一个长整数                                 |
| float(x)                                                     | 将x转换到一个浮点数                                 |
| complex(real [,imag\])                                       | 创建一个复数                                        |
| `str(x)`                                                     | 将对象 x 转换为字符串                               |
| repr(x)                                                      | 将对象 x 转换为表达式字符串                         |
| eval(str)                                                    | 用来计算在字符串中的有效Python表达式,并返回一个对象 |
| `tuple(s)`                                                   | 将序列 s 转换为一个元组                             |
| `list(s)`                                                    | 将序列 s 转换为一个列表                             |
| `set(s)`                                                     | 转换为可变集合                                      |
| `dict(d)`                                                    | 创建一个字典。d 必须是一个序列 (key,value)元组。    |
| frozenset(s)                                                 | 转换为不可变集合                                    |
| `chr(x)`                                                     | 将一个整数转换为一个字符                            |
| unichr(x)                                                    | 将一个整数转换为Unicode字符                         |
| ord(x)                                                       | 将一个字符转换为它的整数值                          |
| hex(x)                                                       | 将一个整数转换为一个十六进制字符串                  |
| oct(x)                                                       | 将一个整数转换为一个八进制字符串                    |

```python
a = '100'  # 此时a的类型是一个字符串，里面存放了100这3个字符
b = int(a) # 此时b的类型是整型，里面存放的是数字100

print("a=%d"%b)
```



### Number-数字



**注意：**

- 1、Python可以同时为`多个变量赋值`，如a, b = 1, 2。
- 2、一个变量可以通过赋值指向不同类型的对象。
- 3、数值的除法包含两个运算符：**`/`** 返回一个浮点数，**`//`** 返回一个整数。
- 4、在混合计算时，Python会把整型转换成为浮点数。



Number 数据类型用于存储数值。

数据类型是不允许改变的,这就意味着如果改变 Number 数据类型的值，将重新分配内存空间。

以下实例在变量赋值时 Number 对象将被创建：

```python
var1 = 1
var2 = 10
```

```python
>>> 5 + 4  # 加法
9
>>> 4.3 - 2 # 减法
2.3
>>> 3 * 7  # 乘法
21
>>> 2 / 4  # 除法，得到一个浮点数
0.5
>>> 2 // 4 # 除法，得到一个整数
0
>>> 17 % 3 # 取余
2
>>> 2 ** 5 # 乘方
32
```

使用del语句删除一些 Number 对象引用。

`del`语句的语法是：

```python
del var1[,var2[,var3[....,varN]]]


#通过使用del语句删除单个或多个对象，例如：
del var
del var_a, var_b
```



Python 支持四种不同的数值类型：

- **整型(Int)** - 通常被称为是整型或整数，是正或负整数，不带小数点。
- **长整型(long integers)** - 无限大小的整数，整数最后是一个大写或小写的L。
- **浮点型(floating point real values)** - 浮点型由整数部分与小数部分组成，浮点型也可以使用科学计数法表示（2.5e2 = 2.5 x 102 = 250）
- **复数(complex numbers)** - 复数由实数部分和虚数部分构成，可以用a + bj,或者complex(a,b)表示， 复数的实部a和虚部b都是浮点型。



Python3 支持 **int、float、bool、complex（复数）**。

在Python 3里，只有一种整数类型 int，表示为长整型，没有 python2 中的 Long。

| int    | long                  | float      | complex    |
| :----- | :-------------------- | :--------- | :--------- |
| 10     | 51924361L             | 0.0        | 3.14j      |
| 100    | -0x19323L             | 15.20      | 45.j       |
| -786   | 0122L                 | -21.9      | 9.322e-36j |
| 080    | 0xDEFABCECBDAECBFBAEl | 32.3+e18   | .876j      |
| -0490  | 535633629843L         | -90.       | -.6545+0J  |
| -0x260 | -052318172735L        | -32.54e100 | 3e+26J     |
| 0x69   | -4721885298529L       | 70.2-E12   | 4.53e-7j   |

- 长整型也可以使用小写"L"，但是还是建议您使用大写"L"，避免与数字"1"混淆。Python使用"L"来显示长整型。
- Python还支持复数，复数由实数部分和虚数部分构成，可以用a + bj,或者complex(a,b)表示， 复数的实部a和虚部b都是浮点型



**Python数学常量**

| 常量 | 描述                                  |
| :--- | :------------------------------------ |
| pi   | 数学常量 pi（圆周率，一般以π来表示）  |
| e    | 数学常量 e，e即自然常数（自然常数）。 |

### String-字符串

**注意：**

- 1、反斜杠可以用来转义，使用r可以让反斜杠不发生转义。
- 2、字符串可以用+运算符连接在一起，用*运算符重复。
- 3、Python中的字符串有两种索引方式，从左往右以0开始，从右往左以-1开始。
- 4、Python中的字符串不能改变。



#### 字符串使用

使用引号(`'`或`"`)来创建字符串。

```python
s1 = 'Hello World!'
s2 = "Python Runoob"

# 以三个双引号或单引号开头的字符串可以折行
s3 = """
hello, 
world!
"""
print(s1, s2, s3, end='')
```



#### 字符串输入

```python
userName = input('请输入用户名:')
print("用户名为：%s"%userName)

password = input('请输入密码:')
print("密码为：%s"%password)
```

> 注意：input获取的数据，都以字符串的方式进行保存，即使输入的是数字，那么也是以字符串方式保存



#### 字符串输出

**连接输出**

```python
# -*- coding: UTF-8 -*-
 
var1 = 'Hello World!'
 
print "输出 :- ", var1[:6] + 'Runoob!' 
```



Python 支持格式化字符串的输出 。尽管这样可能会用到非常复杂的表达式，但最基本的用法是将一个值插入到一个有字符串格式符 %s 的字符串中。

```python
print "My name is %s and weight is %d kg!" % ('Zara', 21)   
#My name is Zara and weight is 21 kg!
```



```python
a, b = 5, 10
print('{0} * {1} = {2}'.format(a, b, a * b))

#Python 3.6以后，格式化字符串还有更为简洁的书写方式，就是在字符串前加上字母`f`
a, b = 5, 10
print(f'{a} * {b} = {a * b}')
```

python 字符串格式化符号:

| 符  号 | 描述                                 |
| :----- | :----------------------------------- |
| %c     | 格式化字符及其ASCII码                |
| %s     | 格式化字符串                         |
| %d     | 格式化整数                           |
| %u     | 格式化无符号整型                     |
| %o     | 格式化无符号八进制数                 |
| %x     | 格式化无符号十六进制数               |
| %X     | 格式化无符号十六进制数（大写）       |
| %f     | 格式化浮点数字，可指定小数点后的精度 |
| %e     | 用科学计数法格式化浮点数             |
| %E     | 作用同%e，用科学计数法格式化浮点数   |
| %g     | %f和%e的简写                         |
| %G     | %F 和 %E 的简写                      |
| %p     | 用十六进制数格式化变量的地址         |

格式化操作符辅助指令:

| 符号  | 功能                                                         |
| :---- | :----------------------------------------------------------- |
| *     | 定义宽度或者小数点精度                                       |
| -     | 用做左对齐                                                   |
| +     | 在正数前面显示加号( + )                                      |
| <sp>  | 在正数前面显示空格                                           |
| #     | 在八进制数前面显示零('0')，在十六进制前面显示'0x'或者'0X'(取决于用的是'x'还是'X') |
| 0     | 显示的数字前面填充'0'而不是默认的空格                        |
| %     | '%%'输出一个单一的'%'                                        |
| (var) | 映射变量(字典参数)                                           |
| m.n.  | m 是显示的最小总宽度,n 是小数点后的位数(如果可用的话)        |

Python2.6 开始，新增了一种格式化字符串的函数 [str.format()](https://www.runoob.com/python/att-string-format.html)，它增强了字符串格式化的功能。



#### 转义字符

在需要在字符中使用特殊字符时，python 用反斜杠 **\** 转义字符。如下表：

| 转义字符    | 描述                                         |
| :---------- | :------------------------------------------- |
| \(在行尾时) | 续行符                                       |
| \\          | 反斜杠符号                                   |
| \'          | 单引号                                       |
| \"          | 双引号                                       |
| \a          | 响铃                                         |
| \b          | 退格(Backspace)                              |
| \e          | 转义                                         |
| \000        | 空                                           |
| \n          | 换行                                         |
| \v          | 纵向制表符                                   |
| \t          | 横向制表符                                   |
| \r          | 回车                                         |
| \f          | 换页                                         |
| \oyy        | 八进制数，yy代表的字符，例如：\o12代表换行   |
| \xyy        | 十六进制数，yy代表的字符，例如：\x0a代表换行 |
| \other      | 其它的字符以普通格式输出                     |

#### Unicode 字符串

Python 中定义一个 Unicode 字符串和定义一个普通字符串一样简单：

```python
>>> u'Hello World !'
u'Hello World !'
```

引号前小写的"u"表示这里创建的是一个 Unicode 字符串。如果你想加入一个特殊字符，可以使用 Python 的 Unicode-Escape 编码。如下例所示：

```python
>>> u'Hello\u0020World !'
u'Hello World !'
```

被替换的 \u0020 标识表示在给定位置插入编码值为 0x0020 的 Unicode 字符（空格符）。

#### 字符串运算符

下表实例变量 a 值为字符串 "Hello"，b 变量值为 "Python"：

| 操作符 | 描述                                                         | 实例                                 |
| :----- | :----------------------------------------------------------- | :----------------------------------- |
| +      | 字符串连接                                                   | >>>a + b 'HelloPython'               |
| *      | 重复输出字符串                                               | >>>a * 2 'HelloHello'                |
| []     | 通过索引获取字符串中字符                                     | >>>a[1]      'e'                     |
| [ : ]  | 截取字符串中的一部分                                         | >>>a[1:4] 'ell'                      |
| in     | 成员运算符 - 如果字符串中包含给定的字符返回 True             | >>>"H" in a True                     |
| not in | 成员运算符 - 如果字符串中不包含给定的字符返回 True           | >>>"M" not in a True                 |
| r/R    | 原始字符串 - 原始字符串：所有的字符串都是直接按照字面的意思来使用，没有转义特殊或不能打印的字符。 原始字符串除在字符串的第一个引号前加上字母"r"（可以大小写）以外，与普通字符串有着几乎完全相同的语法。 | >>>print r'\n' \n >>> print R'\n' \n |
| %      | 格式字符串                                                   | 请看下一章节                         |

```python
# -*- coding: UTF-8 -*-
 
a = "Hello"
b = "Python"
 
print "a + b 输出结果：", a + b 
print "a * 2 输出结果：", a * 2 
print "a[1] 输出结果：", a[1] 
print "a[1:4] 输出结果：", a[1:4] 
 
if( "H" in a) :
    print "H 在变量 a 中" 
else :
    print "H 不在变量 a 中" 
 
if( "M" not in a) :
    print "M 不在变量 a 中" 
else :
    print "M 在变量 a 中"
 
print r'\n'
print R'\n'


"""
a + b 输出结果： HelloPython
a * 2 输出结果： HelloHello
a[1] 输出结果： e
a[1:4] 输出结果： ell
H 在变量 a 中
M 不在变量 a 中
\n
\n
"""
```



#### 下标和切片

**下标索引**

字符串实际上就是字符的数组，所以也支持下标索引。

注意python中下标从 `0` 开始

```python

name = 'abcdef'

print(name[0]) #a
print(name[1]) #b
print(name[2]) #c
```

Python `字符串不能被改变`。向一个索引位置赋值，比如name[0] = 'm'会导致错误。



**切片**

切片是指对操作的对象截取其中一部分的操作。**字符串、列表、元组**都支持切片操作。

`切片的语法：[起始:结束:步长]`

**注意：选取的区间属于左闭右开型，即从"起始"位开始，到"结束"位的前一位结束（不包含结束位本身)。**

如果取出一部分，则可以在中括号`[]`中，使用`:`

```python
name = 'abcdef'

print(name[0:3]) # 取 下标0~2 的字符  abc

print(name[0:5]) # 取 下标为0~4 的字符  abcde

print(name[2:])  # 取 下标为2开始到最后的字符   cdef

 print(name[1:-1]) # 取 下标为1开始到最后第2个之间的字符 bcde
```



```python
>>> a = "abcdef"

>>> a[:3]
'abc'

>>> a[::2]
'ace'

>>> a[5:1:2] 
''

>>> a[1:5:2]
'bd'

>>> a[::-2]
'fdb' 

>>> a[5:1:-2]
'fd'
 
>>> a[5:1:-1]
'fedc'
```



如果第三个参数为负数表示逆向读取，以下实例用于翻转字符串：

```python
def reverseWords(input):
     
    # 通过空格将字符串分隔符，把各个单词分隔为列表
    inputWords = input.split(" ")
 
    # 翻转字符串
    # 假设列表 list = [1,2,3,4],  
    # list[0]=1, list[1]=2 ，而 -1 表示最后一个元素 list[-1]=4 ( 与 list[3]=4 一样)
    # inputWords[-1::-1] 有三个参数
    # 第一个参数 -1 表示最后一个元素
    # 第二个参数为空，表示移动到列表末尾
    # 第三个参数为步长，-1 表示逆向
    inputWords=inputWords[-1::-1]
 
    # 重新组合字符串
    output = ' '.join(inputWords)
     
    return output
 
if __name__ == "__main__":
    input = 'I like runoob'
    rw = reverseWords(input)
    print(rw)
```



#### 字符串常见操作

```python
str1 = 'hello, world!'

# 通过内置函数len计算字符串的长度
print(len(str1)) # 13

# 获得字符串首字母大写的拷贝
print(str1.capitalize()) # Hello, world!

# 获得字符串每个单词首字母大写的拷贝
print(str1.title()) # Hello, World!

# 获得字符串变大写后的拷贝
print(str1.upper()) # HELLO, WORLD!

# 从字符串中查找子串所在位置
print(str1.find('or')) # 8
print(str1.find('shit')) # -1

# 与find类似但找不到子串时会引发异常
# print(str1.index('or'))
# print(str1.index('shit'))
# 检查字符串是否以指定的字符串开头
print(str1.startswith('He')) # False
print(str1.startswith('hel')) # True

# 检查字符串是否以指定的字符串结尾
print(str1.endswith('!')) # True

# 将字符串以指定的宽度居中并在两侧填充指定的字符
print(str1.center(50, '*'))
# 将字符串以指定的宽度靠右放置左侧填充指定的字符
print(str1.rjust(50, ' '))
str2 = 'abc123456'

# 检查字符串是否由数字构成
print(str2.isdigit())  # False
# 检查字符串是否以字母构成
print(str2.isalpha())  # False

# 检查字符串是否以数字和字母构成
print(str2.isalnum())  # True
str3 = '  jackfrued@126.com '
print(str3)
# 获得字符串修剪左右两侧空格之后的拷贝
print(str3.strip())
```

##### find,rfind

`find`: 检测 str 是否包含在 mystr中，如果是返回`开始的索引值`，否则返回`1`

```python
mystr.find(str, start=0, end=len(mystr))
```

`rfind`: 类似于 find()函数，不过是从右边开始查找.

```python
mystr.rfind(str, start=0,end=len(mystr) )
```

##### index,rindex

`index`: 跟find()方法一样，只不过如果str不在 mystr中会报一个异常.

```python
mystr.index(str, start=0, end=len(mystr)) 
```

`rindex`: 类似于 index()，不过是从右边开始.

```python
mystr.rindex( str, start=0,end=len(mystr))
```

##### count

`count`: 返回 str在start和end之间 在 mystr里面出现的次数

```python
mystr.count(str, start=0, end=len(mystr))
```

##### replace

`replace`:把 mystr 中的 str1 替换成 str2,如果 count 指定，则替换不超过 count 次.

```python
mystr.replace(str1, str2,  mystr.count(str1))
```

##### split,join

`split`: 以 str 为分隔符切片 mystr，如果 maxsplit有指定值，则仅分隔 maxsplit 个子字符串

```python
mystr.split(str=" ", 2)   
```

`join`: mystr 中每个字符后面插入str,构造出一个新的字符串

```python
mystr.join(str)
```

##### capitalize,title

`capitalize`: 把字符串的第一个字符大写

```python
mystr.capitalize()
```

`title`: 把字符串的每个单词首字母大写

```python
>>> a = "hello ixfosa"
>>> a.title()
'Hello Ixfosa'
```

##### startswith, endswith

`startswith`: 检查字符串是否是以 obj 开头, 是则返回 True，否则返回 False

```python
mystr.startswith(obj)
```

 `endswith`: 检查字符串是否以obj结束，如果是返回True,否则返回 False.

```python
mystr.endswith(obj)
```

##### lower,upper

`lower`: 转换 mystr 中所有大写字符为小写

```python
mystr.lower()   
```

`upper`: 转换 mystr 中的小写字母为大写

```python
mystr.upper()  
```

##### ljust, rjust,center

`ljust`: 返回一个原字符串左对齐,并使用空格填充至长度 width 的新字符串

```python
mystr.ljust(width) 
```

`rjust`: 返回一个原字符串右对齐,并使用空格填充至长度 width 的新字符串

```python
mystr.rjust(width)    
```

`center`: 返回一个原字符串居中,并使用空格填充至长度 width 的新字符串

```python
mystr.center(width)   
```

##### lstrip,rstrip,strip

`lstrip`: 删除 mystr 左边的空白字符

```python
mystr.lstrip()
```

`rstrip`: 删除 mystr 字符串末尾的空白字符

```python
mystr.rstrip()    
```

`strip`: 删除mystr字符串两端的空白字符

```python
>>> a = "\n\t ixfosa \t\n"
>>> a.strip()
'ixfosa'
```

##### partition,rpartition

`partition`: 把mystr以str分割成三部分,str前，str和str后

```python
mystr.partition(str)
```

`rpartition`:类似于 partition()函数,不过是从右边开始.

```python
mystr.rpartition(str)
```

##### splitlines

`splitlines`:按照行分隔，返回一个包含各行作为元素的列表

```python
mystr.splitlines()  

str = "hello\nworld"
print str   #hello
			#world
			
mystr.splitlines()  #['hello', 'world']
```

##### isalpha,isdigit,isalnum,isspace

`isalpha`: 如果 mystr 所有字符都是字母 则返回 True,否则返回 False

```python
mystr.isalpha() 
```

`isdigit`: 如果 mystr 只包含数字则返回 True 否则返回 False.

```python
mystr.isdigit() 
```

`isalnum`: 如果 mystr 所有字符都是字母或数字则返回 True,否则返回 False

```python
mystr.isalnum()  
```

`isspace`: 如果 mystr 中只包含空格，则返回 True，否则返回 False.

```python
mystr.isspace()  
```



### List-列表

列表（`list`），是一种结构化的、非标量类型，它是值的有序序列，每个值都可以通过索引进行标识，定义列表可以将列表的元素放在`[]`中，多个元素用`,`进行分隔，可以使用`for`循环对列表元素进行遍历，也可以使用`[]`或`[:]`运算符取出列表中的一个或多个元素。

**注意：**

- 1、List写在方括号之间，元素用逗号隔开。
- 2、和字符串一样，list可以被索引和切片。
- 3、List可以使用+操作符进行拼接。
- 4、List中的元素是可以改变的。



#### 使用列表

建一个列表，只要把逗号分隔的不同的数据项使用`方括号括`起来即可

列表的数据项不`需要具有相同的类型`

```python
list1 = ['Google', 'Runoob', 1997, 2000]

list1 = [1, 3, 5, 7, 100]
print(list1) # [1, 3, 5, 7, 100]

# 乘号表示列表元素的重复
list2 = ['hello'] * 3
print(list2) # ['hello', 'hello', 'hello']

# 计算列表长度(元素个数)
print(len(list1)) # 5

# 下标(索引)运算
print(list1[0]) # 1
print(list1[4]) # 100
# print(list1[5])  # IndexError: list index out of range
print(list1[-1]) # 100
print(list1[-3]) # 5

#修改
list1[2] = 300
print(list1) # [1, 3, 300, 7, 100]
```

#### 遍历列表

```python
list1 = [1, 3, 5, 7, 100]

# 通过循环用下标遍历列表元素
for index in range(len(list1)):
    print(list1[index])
    
# 通过for循环遍历列表元素
for elem in list1:
    print(elem)
    
#使用while循环
length = len(list1)

i = 0

while i<length:
    print(list1[i])
	i+=1
    
# 通过enumerate函数处理列表之后再遍历可以同时获得元素索引和值
for index, elem in enumerate(list1):
    print(index, elem) 
```



#### 列表脚本操作符

列表对 + 和 * 的操作符与字符串相似。+ 号用于组合列表，* 号用于重复列表。

| Python 表达式                         | 结果                         | 描述                 |
| :------------------------------------ | :--------------------------- | :------------------- |
| len([1, 2, 3])                        | 3                            | 长度                 |
| [1, 2, 3] + [4, 5, 6]                 | [1, 2, 3, 4, 5, 6]           | 组合                 |
| ['Hi!'] * 4                           | ['Hi!', 'Hi!', 'Hi!', 'Hi!'] | 重复                 |
| 3 in [1, 2, 3]                        | True                         | 元素是否存在于列表中 |
| for x in [1, 2, 3]: print(x, end=" ") | 1 2 3                        | 迭代                 |



#### 列表嵌套

```python
>>>a = ['a', 'b', 'c']
>>> n = [1, 2, 3]
>>> x = [a, n]
>>> x
[['a', 'b', 'c'], [1, 2, 3]]

>>> x[0]
['a', 'b', 'c']
>>> x[0][1]
'b'
```

一个学校，有3个办公室，现在有8位老师等待工位的分配，请编写程序，完成随机的分配

```python
#encoding=utf-8

import random

# 定义一个列表用来保存3个办公室
offices = [[],[],[]]

# 定义一个列表用来存储8位老师的名字
names = ['A','B','C','D','E','F','G','H']

i = 0
for name in names:
    index = random.randint(0,2)    
    offices[index].append(name)

i = 1
for tempNames in offices:
    print('办公室%d的人数为:%d'%(i,len(tempNames)))
    i+=1
    for name in tempNames:
        print("%s"%name,end='')
    print("\n")
    print("-"*20)
```



#### 生成式和生成器

我们还可以使用列表的生成式语法来创建列表，代码如下所示。

```python
f = [x for x in range(1, 10)]
print(f)

f = [x + y for x in 'ABCDE' for y in '1234567']
print(f)

# 用列表的生成表达式语法创建列表容器
# 用这种语法创建列表之后元素已经准备就绪所以需要耗费较多的内存空间
f = [x ** 2 for x in range(1, 1000)]
print(sys.getsizeof(f))  # 查看对象占用内存的字节数
print(f)

# 请注意下面的代码创建的不是一个列表而是一个生成器对象
# 通过生成器可以获取到数据但它不占用额外的空间存储数据
# 每次需要数据的时候就通过内部的运算得到数据(需要花费额外的时间)
f = (x ** 2 for x in range(1, 1000))
print(sys.getsizeof(f))  # 相比生成式生成器不占用存储数据的空间
print(f)
for val in f:
    print(val)
```

除了上面提到的生成器语法，Python中还有另外一种定义生成器的方式，就是通过`yield`关键字将一个普通函数改造成生成器函数。下面的代码演示了如何实现一个生成斐波拉切数列的生成器。所谓斐波拉切数列可以通过下面递归的方法来进行定义：

```python
def fib(n):
    a, b = 0, 1
    for _ in range(n):
        a, b = b, a + b
        yield a


def main():
    for val in fib(20):
        print(val)


if __name__ == '__main__':
    main()
```

#### 列表的相关操作

##### 列表截取

和字符串一样，列表也可以做切片操作，通过切片操作我们可以实现对列表的复制或者将列表中的一部分取出来创建出新的列表，代码如下所示。

```python
fruits = ['grape', 'apple', 'strawberry', 'waxberry']
fruits += ['pitaya', 'pear', 'mango']

# 列表切片
fruits2 = fruits[1:4]
print(fruits2) # apple strawberry waxberry

# 可以通过完整切片操作来复制列表
fruits3 = fruits[:]
print(fruits3) # ['grape', 'apple', 'strawberry', 'waxberry', 'pitaya', 'pear', 'mango']

fruits4 = fruits[-3:-1]
print(fruits4) # ['pitaya', 'pear']

# 可以通过反向切片操作来获得倒转后的列表的拷贝
fruits5 = fruits[::-1]
print(fruits5) # ['mango', 'pear', 'pitaya', 'waxberry', 'strawberry', 'apple', 'grape']
```

##### 添加元素-append,extend,insert

`append`: 在列表末尾添加新的对象

`extend`: 列表末尾一次性追加另一个序列中的多个值（用新列表扩展原来的列表）

`insert`: 将对象插入列表

```python
list1 = [1, 3, 5, 7, 100]

# 添加元素
list1.append(200)
list1.insert(1, 400)

# 合并两个列表
# list1.extend([1000, 2000])
list1 += [1000, 2000]
print(list1) # [1, 400, 3, 5, 7, 100, 200, 1000, 2000]

print(len(list1)) # 9
```

##### 移除元素-del,pop,remove,clear

`del`：根据下标进行删除

`pop`：移除列表中的一个元素（默认最后一个元素），并且返回该元素的值

`remove`：根据元素的值进行删除

`clear`: 清空列表元素

```python
list1 = [1, 3, 5, 7, 100]

# 先通过成员运算判断元素是否在列表中，如果存在就删除该元素
if 3 in list1:
	list1.remove(3)
if 1234 in list1:
    list1.remove(1234)
print(list1) # [1, 400, 5, 7, 100, 200, 1000, 2000]

# 从指定的位置删除元素
#list1.pop()
list1.pop(0)
list1.pop(len(list1) - 1)
print(list1) # [400, 5, 7, 100, 200, 1000]

# del 语句来删除列表的元素
del list1[2]

# 清空列表元素
list1.clear()
print(list1) # []
```

##### 查找元素-index,count

python中查找的常用方法为：

- `in`（存在）,如果存在那么结果为true，否则为false
- `not in`（不存在），如果不存在那么结果为true，否则false

`index`: 从列表中找出某个值第一个匹配项的索引位置

`count`:  统计某个元素在列表中出现的次数

```python
 #待查找的列表
nameList = ['xiaoWang','xiaoZhang','xiaoHua']

#获取用户要查找的名字
findName = input('请输入要查找的姓名:')

#查找是否存在
if findName in nameList:
    print('在字典中找到了相同的名字')
else:
    print('没有找到')
```

```python
>>> a = ['a', 'b', 'c', 'a', 'b']
>>> a.index('a', 1, 3) # 注意是左闭右开区间
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
ValueError: 'a' is not in list
    
>>> a.index('a', 1, 4)
3
>>> a.count('b')
2
>>> a.count('d')
0
```

##### 排序-sort, sorted,reverse

`sort`: 将list按特定顺序重新排列，默认为由小到大，参数reverse=True可改为倒序，由大到小。

`sorted`: 函数返回列表排序后的拷贝不会修改传入的列表

`reverse`: 将list逆置。

```python
>>> a = [1, 4, 2, 3]
>>> a
[1, 4, 2, 3]

#将list逆置。
>>> a.reverse()
>>> a
[3, 2, 4, 1]

#将list按特定顺序重新排列，默认为由小到大
>>> a.sort()
>>> a
[1, 2, 3, 4]

>>> a.sort(reverse=True)
>>> a
[4, 3, 2, 1]
```

```python
list1 = ['orange', 'apple', 'zoo', 'internationalization', 'blueberry']

# sorted函数返回列表排序后的拷贝不会修改传入的列表
list2 = sorted(list1)

# 函数的设计就应该像sorted函数一样尽可能不产生副作用
list3 = sorted(list1, reverse=True)

# 通过key关键字参数指定根据字符串长度进行排序而不是默认的字母表顺序
list4 = sorted(list1, key=len)
print(list1)
print(list2)
print(list3)
print(list4)
```

##### cmp,len,max.min,list

`cmp(list1, list2)`: 比较两个列表的元素

`len(list)`: 列表元素个数

`max(list)`: 返回列表元素最大值

`min(list)`: 返回列表元素最小值

`list(seq)`: 将元组转换为列表

### Tuple-元组

Python的元组与列表类似，不同之处在于元组的`元素不能修改`。

元组使用`小括号`，列表使用方括号。

这里有一个非常值得探讨的问题，我们已经有了列表这种数据结构，为什么还需要元组这样的类型呢？

1. 元组中的元素是无法修改的，事实上我们在项目中尤其是多线程多线程)环境中可能更喜欢使用的是那些不变对象（一方面因为对象状态不能修改，所以可以避免由此引起的不必要的程序错误，简单的说就是一个不变的对象要比可变的对象更加容易维护；另一方面因为没有任何一个线程能够修改不变对象的内部状态，一个不变对象自动就是线程安全的，这样就可以省掉处理同步化的开销。一个不变对象可以方便的被共享访问）。所以结论就是：如果不需要对元素进行添加、删除、修改的时候，可以考虑使用元组，当然如果一个方法要返回多个值，使用元组也是不错的选择。
2. 元组在创建时间和占用的空间上面都优于列表。我们可以使用sys模块的getsizeof函数来检查存储同样的元素的元组和列表各自占用了多少内存空间

**注意：**

- 1、与字符串一样，元组的元素不能修改。
- 2、元组也可以被索引和切片，方法一样。
- 3、注意构造包含 0 或 1 个元素的元组的特殊语法规则。
- 4、元组也可以使用+操作符进行拼接。



#### 创建元组

元组创建很简单，只需要在括号中添加元素，并使用逗号隔开即可。

```python
>>>tup1 = ('Google', 'Runoob', 1997, 2000)
>>> tup2 = (1, 2, 3, 4, 5 )
>>> tup3 = "a", "b", "c", "d"   #  不需要括号也可以
>>> type(tup3)
<class 'tuple'>

#创建空元组
tup4 = ()

#元组中只包含一个元素时，需要在元素后面添加逗号，否则括号会被当作运算符使用：
>>>tup1 = (50)
>>> type(tup1)     # 不加逗号，类型为整型
<class 'int'>
 
>>> tup1 = (50,)
>>> type(tup1)     # 加上逗号，类型为元组
<class 'tuple'>
```

#### 访问元组

元组可以使用下标索引来访问元组中的值

```python
tup1 = ('Google', 'Runoob', 1997, 2000)
tup2 = (1, 2, 3, 4, 5, 6, 7 )
 
print ("tup1[0]: ", tup1[0])
print ("tup2[1:5]: ", tup2[1:5])

# 遍历元组中的值
for member in tup2:
    print(member)
```

#### 修改元组

元组中的元素值是不允许修改的，但我们可以对元组进行连接组合

```python
tup1 = (12, 34.56)
tup2 = ('abc', 'xyz')
 
# 以下修改元组元素操作是非法的。
# tup1[0] = 100
 
# 创建一个新的元组
tup3 = tup1 + tup2
print (tup3)



# 将元组转换成列表
tup4 = list(tup2)
print(tup4)

# 列表是可以修改它的元素的
tup4[0] = 'long'
tup4[1] = 25
print(tup4)

# 将列表转换成元组
fruits_list = ['apple', 'banana', 'orange']
fruits_tuple = tuple(fruits_list)
print(fruits_tuple)
```

**关于元组是不可变的**

所谓元组的不可变指的是`元组所指向的内存中的内容不可变`。

```python
>>> tup = ('r', 'u', 'n', 'o', 'o', 'b')
>>> tup[0] = 'g'     # 不支持修改元素
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
TypeError: 'tuple' object does not support item assignment
    
>>> id(tup)     # 查看内存地址
4440687904
>>> tup = (1,2,3)
>>> id(tup)
4441088800    # 内存地址不一样了
```

从以上实例可以看出，重新赋值的元组 tup，**绑定到新的对象了，不是修改了原来的对象。**

#### 删除元组

元组中的元素值是不允许删除的，但我们可以使用del语句来删除整个元组

```python
tup = ('Google', 'Runoob', 1997, 2000)
 
print (tup)
del tup
print ("删除后的元组 tup : ")
print (tup)

#元组被删除后，输出变量会有异常信息，输出如下所示：
删除后的元组 tup : 
Traceback (most recent call last):
  File "test.py", line 8, in <module>
    print (tup)
NameError: name 'tup' is not defined
```

#### 元组运算符

与字符串一样，元组之间可以使用 + 号和 * 号进行运算。这就意味着他们可以组合和复制，运算后会生成一个新的元组。

| Python 表达式                  | 结果                         | 描述         |
| :----------------------------- | :--------------------------- | :----------- |
| len((1, 2, 3))                 | 3                            | 计算元素个数 |
| (1, 2, 3) + (4, 5, 6)          | (1, 2, 3, 4, 5, 6)           | 连接         |
| ('Hi!',) * 4                   | ('Hi!', 'Hi!', 'Hi!', 'Hi!') | 复制         |
| 3 in (1, 2, 3)                 | True                         | 元素是否存在 |
| for x in (1, 2, 3): print (x,) | 1 2 3                        | 迭代         |

#### 元组的内置函数

Python元组包含了以下内置函数

| 序号 | 方法及描述                               | 实例                                                         |
| :--- | :--------------------------------------- | :----------------------------------------------------------- |
| 1    | len(tuple) 计算元组元素个数。            | `>>> tuple1 = ('Google', 'Runoob', 'Taobao') >>> len(tuple1) 3 >>> ` |
| 2    | max(tuple) 返回元组中元素最大值。        | `>>> tuple2 = ('5', '4', '8') >>> max(tuple2) '8' >>> `      |
| 3    | min(tuple) 返回元组中元素最小值。        | `>>> tuple2 = ('5', '4', '8') >>> min(tuple2) '4' >>> `      |
| 4    | tuple(iterable) 将可迭代系列转换为元组。 | `>>> list1= ['Google', 'Taobao', 'Runoob', 'Baidu'] >>> tuple1=tuple(list1) >>> tuple1 ('Google', 'Taobao', 'Runoob', 'Baidu')` |

`count`,`index`字符串和列表中的用法相同

```python
>>> a = ('a', 'b', 'c', 'a', 'b')
>>> a.index('a', 1, 3) # 注意是左闭右开区间
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
ValueError: tuple.index(x): x not in tuple

>>> a.index('a', 1, 4)
3
>>> a.count('b')
2
>>> a.count('d')
0
```





### Set-集合

集合（set）是由一个或数个形态各异的大小整体组成的，构成集合的事物或对象称作元素或是成员。

基本功能是进行成员`关系测试`和`删除重复元素`。

可以使用大括号` { } `或者 `set()` 函数创建集合
注意：创建一个空集合必须用`set()`而不是`{ }`，因为 `{ }`是用来创建一个`空字典`。

#### 创建集合

```python
parame = {value01,value02,...}
或者
set(value)

# 创建集合的字面量语法
set1 = {1, 2, 3, 3, 3, 2}
print(set1)
print('Length =', len(set1))

# 创建集合的构造器语法(面向对象部分会进行详细讲解)
set2 = set(range(1, 10))
set3 = set((1, 2, 3, 3, 2, 1))
print(set2, set3)

# 创建集合的推导式语法(推导式也可以用于推导集合)
set4 = {num for num in range(1, 100) if num % 3 == 0 or num % 5 == 0}
print(set4)
```



#### 集合运算

`difference()`: 返回多个集合的差集

`difference_update()`:移除集合中的元素，该元素在指定的集合也存在。

`intersection()`:返回集合的交集

`intersection_update()`: 返回集合的交集。

`issubset()`: 判断指定集合是否为该方法参数集合的子集。

`issuperset()`: 判断该方法的参数集合是否为指定集合的子集

`symmetric_difference()`: 返回两个集合中不重复的元素集合。	

`symmetric_difference_update`: 移除当前集合中在另外一个指定集合相同的元素，并将另外一个指定集合中不同的元素插入到当前集合中。

`union()`: 返回两个集合的并集

##### 差集

```python
#difference() 方法用于返回集合的差集，即返回的集合元素包含在第一个集合中，但不包含在第二个集合(方法的参数)中。
#difference() 方法语法：
set.difference(set) 
#set1 - set2

'''
参数
set -- 必需，用于计算差集的集合
返回值
返回一个新的集合
'''

#返回一个集合，元素包含在集合 x ，但不在集合 y ：
x = {"apple", "banana", "cherry"}
y = {"google", "microsoft", "apple"}
z = x.difference(y) 
print(z) #{'cherry', 'banana'}


#difference_update() 方法用于移除两个集合中都存在的元素。
#difference_update() 方法与 difference() 方法的区别在于 difference() 方法返回一个移除相同元素的新集合，而 difference_update() 方法是直接在原来的集合中移除元素，没有返回值。
#difference_update() 方法语法：
set.difference_update(set)

'''
参数
set -- 必需，用于计算差集的集合
返回值
无。
'''

#移除两个集合都包含的元素：
x = {"apple", "banana", "cherry"}
y = {"google", "microsoft", "apple"}
x.difference_update(y) 
print(x) #{'cherry', 'banana'}
```

##### 交集(多个集合中相同元素)

```python
#intersection() 方法用于返回两个或更多集合中都包含的元素，即交集。
#intersection() 方法语法：
set.intersection(set1, set2 ... etc)
# set1 & set2

'''
参数
set1 -- 必需，要查找相同元素的集合
set2 -- 可选，其他要查找相同元素的集合，可以多个，多个使用逗号 , 隔开
返回值
返回一个新的集合。
'''

#返回一个新集合，该集合的元素既包含在集合 x 又包含在集合 y 中：
x = {"apple", "banana", "cherry"}
y = {"google", "runoob", "apple"}
z = x.intersection(y) 
print(z) #{'apple'}

计算多个集合的交集：
x = {"a", "b", "c"}
y = {"c", "d", "e"}
z = {"f", "g", "c"}
result = x.intersection(y, z)
print(result) #{'c'}


#intersection_update() 方法用于获取两个或更多集合中都重叠的元素，即计算交集。
#intersection_update() 方法不同于 intersection() 方法，因为 intersection() 方法是返回一个新的集合，而 intersection_update() 方法是在原始的集合上移除不重叠的元素。

#intersection_update() 方法语法：
set.intersection_update(set1, set2 ... etc)

'''
参数
set1 -- 必需，要查找相同元素的集合
set2 -- 可选，其他要查找相同元素的集合，可以多个，多个使用逗号 , 隔开
返回值
无。
'''


#返回一个新集合，该集合的元素既包含在集合 x 又包含在集合 y 中：
x = {"apple", "banana", "cherry"}
y = {"google", "runoob", "apple"}
x.intersection_update(y) 
print(x) #{'apple'}

#计算多个集合的并集：
x = {"a", "b", "c"}
y = {"c", "d", "e"}
z = {"f", "g", "c"}
x.intersection_update(y, z)
print(x) #{'c'}
```

##### 并集(重复元素只出现一次)

```python
#union() 方法返回两个集合的并集，即包含了所有集合的元素，重复的元素只会出现一次。
#union() 方法语法：
set.union(set1, set2...)
# set1 | set2

'''
参数
set1 -- 必需，合并的目标集合
set2 -- 可选，其他要合并的集合，可以多个，多个使用逗号 , 隔开。
返回值
返回一个新集合。
'''

#合并两个集合，重复元素只会出现一次：
x = {"apple", "banana", "cherry"}
y = {"google", "runoob", "apple"}
z = x.union(y) 
print(z) #{'cherry', 'runoob', 'google', 'banana', 'apple'}

#合并多个集合：
x = {"a", "b", "c"}
y = {"f", "d", "a"}
z = {"c", "d", "e"}
result = x.union(y, z) 
print(result) #{'c', 'd', 'f', 'e', 'b', 'a'}
```

##### 子集超集

```python
#issubset() 方法用于判断集合的所有元素是否都包含在指定集合中，如果是则返回 True，否则返回 False。
#issubset() 方法语法：
set.issubset(set)
# set2 <= set1
'''
参数
set -- 必需，要比查找的集合
返回值
返回布尔值，如果都包含返回 True，否则返回 False。
'''

#判断集合 x 的所有元素是否都包含在集合 y 中：
x = {"a", "b", "c"}
y = {"f", "e", "d", "c", "b", "a"}
z = x.issubset(y) 
print(z) #True

#如果没有全部包含返回 False：
x = {"a", "b", "c"}
y = {"f", "e", "d", "c", "b"}
z = x.issubset(y) 
print(z) #False


#issuperset() 方法用于判断指定集合的所有元素是否都包含在原始的集合中，如果是则返回 True，否则返回 False。
#issuperset() 方法语法：
set.issuperset(set)
# set1 >= set2
'''
参数
set -- 必需，要比查找的集合
返回值
返回布尔值，如果都包含返回 True，否则返回 False。
'''

#判断集合 y 的所有元素是否都包含在集合 x 中：
x = {"f", "e", "d", "c", "b", "a"}
y = {"a", "b", "c"}
z = x.issuperset(y) 
print(z) #True


#如果没有全部包含返回 False：
x = {"f", "e", "d", "c", "b"}
y = {"a", "b", "c"}
z = x.issuperset(y) 
print(z) #False
```

##### 并集去重(重复元素不出现)

```python
#symmetric_difference() 方法返回两个集合中不重复的元素集合，即会移除两个集合中都存在的元素。
#symmetric_difference() 方法语法：
set.symmetric_difference(set)
# set1 ^ set2

'''
参数
set -- 集合
返回值
返回一个新的集合。
'''

#返回两个集合组成的新集合，但会移除两个集合的重复元素：
x = {"apple", "banana", "cherry"}
y = {"google", "runoob", "apple"}
z = x.symmetric_difference(y) 
print(z) #{'google', 'cherry', 'banana', 'runoob'}


#symmetric_difference_update() 方法移除当前集合中在另外一个指定集合相同的元素，并将另外一个指定集合中不同的元素插入到当前集合中。
#symmetric_difference_update() 方法语法：
set.symmetric_difference_update(set)

'''
参数
set -- 要检测的集合
返回值
无。
'''

#在原始集合 x 中移除与 y 集合中的重复元素，并将不重复的元素插入到集合 x 中：
x = {"apple", "banana", "cherry"}
y = {"google", "runoob", "apple"}
x.symmetric_difference_update(y) 
print(x) #{'google', 'cherry', 'banana', 'runoob'}
```



##### 通过-, |, &, ^运算

```python
>>> basket = {'apple', 'orange', 'apple', 'pear', 'orange', 'banana'}
>>> print(basket)                      # 这里演示的是去重功能


# 下面展示两个集合间的运算.
>>> a = set('abracadabra')
>>> b = set('alacazam')
>>> a                                  
{'a', 'r', 'b', 'c', 'd'}
>>> a - b                              # 集合a中包含而集合b中不包含的元素 差集
{'r', 'd', 'b'}
>>> a | b                              # 集合a或b中包含的所有元素  并集
{'a', 'c', 'r', 'd', 'b', 'm', 'z', 'l'}
>>> a & b                              # 集合a和b中都包含了的元素 交集
{'a', 'c'}
>>> a ^ b                              # 不同时包含于a和b的元素 并集
{'r', 'd', 'b', 'm', 'z', 'l'}
```

> **说明：** Python中允许通过一些特殊的方法来为某种类型或数据结构自定义运算符，上面的代码中我们对集合进行运算的时候可以调用集合对象的方法，也可以直接使用对应的运算符，例如`&`运算符跟`intersectio`方法的作用就是一样的，但是使用运算符让代码更加直观。

#### 集合的基本操作

##### 添加元素-add,update

```python
#语法格式如下：
s.add( x )

#将元素 x 添加到集合 s 中，如果元素已存在，则不进行任何操作。
>>> thisset = set(("Google", "Runoob", "Taobao"))
>>> thisset.add("Facebook")
>>> print(thisset)
{'Taobao', 'Facebook', 'Google', 'Runoob'}



#update也可以添加元素，且参数可以是列表，元组，字典等，语法格式如下：
s.update( x )

#x 可以有多个，用逗号分开。
>>> thisset = set(("Google", "Runoob", "Taobao"))
>>> thisset.update({1,3})
>>> print(thisset)
{1, 3, 'Google', 'Taobao', 'Runoob'}

>>> thisset.update([1,4],[5,6])  
>>> print(thisset)
{1, 3, 4, 5, 6, 'Google', 'Taobao', 'Runoob'}
```

##### 移除元素-remove，discard，pop

```python
#语法格式如下：
s.remove( x )


#将元素 x 从集合 s 中移除，如果元素不存在，则会发生错误。
>>> thisset = set(("Google", "Runoob", "Taobao"))
>>> thisset.remove("Taobao")
>>> print(thisset)
{'Google', 'Runoob'}

>>> thisset.remove("Facebook")   # 不存在会发生错误
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
KeyError: 'Facebook'
>>>


#discard也是移除集合中的元素，且如果元素不存在，不会发生错误。格式如下所示：
s.discard( x )
>>> thisset = set(("Google", "Runoob", "Taobao"))
>>> thisset.discard("Facebook")  # 不存在不会发生错误
>>> print(thisset)
{'Taobao', 'Google', 'Runoob'}

#设置随机删除集合中的一个元素，语法格式如下：
#set 集合的 pop 方法会对集合进行无序的排列，然后将这个无序排列集合的左面第一个元素进行删除。
s.pop() 
thisset = set(("Google", "Runoob", "Taobao", "Facebook"))
x = thisset.pop()
print(x)  #Runoob  多次执行测试结果都不一样。
```

##### 计算元素个数-len

```python
#语法格式如下：
len(s)

#计算集合 s 元素个数。
>>> thisset = set(("Google", "Runoob", "Taobao"))
>>> len(thisset)
3
```

##### 清空集合

```python
@语法格式如下：
s.clear()

#清空集合 s。
>>> thisset = set(("Google", "Runoob", "Taobao"))
>>> thisset.clear()
>>> print(thisset)
set()
```

##### 元素是否在集合中-in,isdisjoint

```python
#语法格式如下：
x in s

#判断元素 x 是否在集合 s 中，存在返回 True，不存在返回 False。
>>> thisset = set(("Google", "Runoob", "Taobao"))
>>> "Runoob" in thisset
True
>>> "Facebook" in thisset
False
>>>
```

```python
#isdisjoint() 方法用于判断两个集合是否包含相同的元素，如果没有返回 True，否则返回 False。。

#isdisjoint() 方法语法：
set.isdisjoint(set)

'''
参数
set -- 必需，要比较的集合
返回值
返回布尔值，如果不包含返回 True，否则返回 False。
'''

#判断集合 y 中是否有包含 集合 x 的元素：
x = {"apple", "banana", "cherry"}
y = {"google", "runoob", "facebook"}
z = x.isdisjoint(y) 
print(z) #True


#如果包含返回 False：
x = {"apple", "banana", "cherry"}
y = {"google", "runoob", "apple"}
z = x.isdisjoint(y) 
print(z) #False
```



##### 拷贝集合

```python
#copy() 方法用于拷贝一个集合。
set.copy()

#拷贝 fruits 集合：
fruits = {"apple", "banana", "cherry"}
x = fruits.copy()
print(x) #{'cherry', 'banana', 'apple'}
```



### Dictionary-字典

列表是有序的对象集合，字典是`无序`的对象集合。
两者之间的区别在于：字典当中的元素是通过键来存取的，而不是通过偏移存取。

字典是另一种可变容器模型，且`可存储任意类型对象`。
字典的每个键值 key=>value对用冒号 **:** 分割，每个对之间用逗号(**,**)分割，整个字典包括在花括号 **{}** 中

```python
d = {key1 : value1, key2 : value2 }
```

**注意：**

- 1、字典是一种映射类型，它的元素是键值对。
- 2、字典的关键字必须为`不可变类型`，且`不能重复`。
- 3、创建空字典使用 **{ }**。



#### 创建字典

键必须是`唯一`的，但值则不必。

值可以取任何数据类型，但键必须是不可变的，如字符串，数字。

```python
# 创建字典的字面量语法
dict0 = {'Alice': '2341', 'Beth': '9102', 'Cecil': '3258'}
dict1 = { 'abc': 456 }
dict2 = { 'abc': 123, 98.6: 37 }
print(dict0)

# 创建字典的构造器语法
items1 = dict(one=1, two=2, three=3, four=4)

# 通过zip函数将两个序列压成字典
items2 = dict(zip(['a', 'b', 'c'], '123'))

#构造函数 dict() 可以直接从键值对序列中构建字典如下：
>>> dict([('Runoob', 1), ('Google', 2), ('Taobao', 3)])
{'Runoob': 1, 'Google': 2, 'Taobao': 3}

# 创建字典的推导式语法
>>> {x: x**2 for x in (2, 4, 6)}
{2: 4, 4: 16, 6: 36}


######################################################

dict = {}
dict['one'] = "1 - 菜鸟教程"
dict[2]     = "2 - 菜鸟工具"

tinydict = {'name': 'runoob','code':1, 'site': 'www.runoob.com'}

print (dict['one'])       # 输出键为 'one' 的值
print (dict[2])           # 输出键为 2 的值
print (tinydict)          # 输出完整的字典
print (tinydict.keys())   # 输出所有键
print (tinydict.values()) # 输出所有值

############################################################

#字典值可以是任何的 python 对象，既可以是标准的对象，也可以是用户定义的，但键不行。
#两个重要的点需要记住：

#1）不允许同一个键出现两次。创建时如果同一个键被赋值两次，后一个值会被记住，如下实例：
dict = {'Name': 'Runoob', 'Age': 7, 'Name': '小菜鸟'}
print ("dict['Name']: ", dict['Name']) #dict['Name']:  小菜鸟

#2）键必须不可变，所以可以用数字，字符串或元组充当，而用列表就不行，如下实例：
dict = {['Name']: 'Runoob', 'Age': 7}
print ("dict['Name']: ", dict['Name'])
# 以上实例输出结果：
Traceback (most recent call last):
  File "test.py", line 3, in <module>
    dict = {['Name']: 'Runoob', 'Age': 7}
TypeError: unhashable type: 'list'
```

#### 访问字典

```python
#把相应的键放入到方括号中，如下实例:
dict = {'Name': 'Runoob', 'Age': 7, 'Class': 'First'}
print ("dict['Name']: ", dict['Name']) #dict['Name']:  Runoob
print ("dict['Age']: ", dict['Age']) #dict['Age']:  7


#如果用字典里没有的键访问数据，会输出错误如下：
dict = {'Name': 'Runoob', 'Age': 7, 'Class': 'First'}
print ("dict['Alice']: ", dict['Alice'])
#以上实例输出结果：
Traceback (most recent call last):
  File "test.py", line 5, in <module>
    print ("dict['Alice']: ", dict['Alice'])
KeyError: 'Alice'
    
    
# 对字典中所有键值对进行遍历
dict = {'Name': 'Runoob', 'Age': 7, 'Class': 'First'}
for key in dict:
    print(f'{key}: {dict[key]}')

    
if 'Name' in dict:
    print(scores['Name'])
```

#### 修改字典

```python
#向字典添加新内容的方法是增加新的键/值对，修改或删除已有键/值对如下实例:
dict = {'Name': 'Runoob', 'Age': 7, 'Class': 'First'}
dict['Age'] = 8               # 更新 Age
dict['School'] = "菜鸟教程"  # 添加信息
 
print ("dict['Age']: ", dict['Age']) #dict['Age']:  8
print ("dict['School']: ", dict['School']) #dict['School']:  菜鸟教程
```

#### 删除字典元素

```python
#能删单一的元素也能清空字典，清空只需一项操作。

#显示删除一个字典用del命令，如下实例：
dict = {'Name': 'Runoob', 'Age': 7, 'Class': 'First'}
del dict['Name'] # 删除键 'Name'
dict.clear()     # 清空字典
del dict         # 删除字典


print ("dict['Age']: ", dict['Age'])
print ("dict['School']: ", dict['School'])
#但这会引发一个异常，因为用执行 del 操作后字典不再存在：
Traceback (most recent call last):
  File "test.py", line 9, in <module>
    print ("dict['Age']: ", dict['Age'])
TypeError: 'type' object is not subscriptable
```

#### 函数&方法

Python字典包含了以下内置函数：

| 函数及描述                                                   | 实例                                                         |
| :----------------------------------------------------------- | :----------------------------------------------------------- |
| len(dict) 计算字典元素个数，即键的总数。                     | >>> dict = {'Name': 'Runoob', 'Age': 7, 'Class': 'First'} <br >>> len(dict)   #3 |
| str(dict) 输出字典，以可打印的字符串表示。                   | >>> dict = {'Name': 'Runoob', 'Age': 7, 'Class': 'First'}<br /> >>> str(dict) <br />"{'Name': 'Runoob', 'Class': 'First', 'Age': 7}" |
| type(variable) 返回输入的变量类型，如果变量是字典就返回字典类型。 | >>> dict = {'Name': 'Runoob', 'Age': 7, 'Class': 'First'} <br />>>> type(dict) <br /><class 'dict'> |



Python字典包含了以下内置方法：

| 函数及描述                                                   |
| :----------------------------------------------------------- |
| `clear()` 删除字典内所有元素                                 |
| `copy()`]返回一个字典的浅复制                                |
| `fromkeys()`创建一个新字典，以序列seq中元素做字典的键，val为字典所有键对应的初始值 |
| `get(key, default=None)`返回指定键的值，如果键不在字典中返回 default 设置的默认值 |
| `key in dict`如果键在字典dict里返回true，否则返回false       |
| `items()`以列表返回可遍历的(键, 值) 元组数组                 |
| `keys()` 返回一个迭代器，可以使用 list() 来转换为列表        |
| .`setdefault(key, default=None)` 和get()类似, 但如果键不存在于字典中，将会添加键并将值设为default |
| `update(dict2)`把字典dict2的键/值对更新到dict里              |
| `values()`返回一个迭代器，可以使用 list() 来转换为列表       |
| `pop(key[,default\])` 删除字典给定键 key 所对应的值，返回值为被删除的值。key值必须给出。 否则，返回default值。 |
| `popitem()` 随机返回并删除字典中的最后一对键和值。           |

##### clear

```python
#Python 字典 clear() 函数用于删除字典内所有元素。
#clear()方法语法：
dict.clear()

···
参数
NA。
返回值
该函数没有任何返回值。
···

dict = {'Name': 'Zara', 'Age': 7}
print ("字典长度 : %d" %  len(dict)) #字典长度 : 2
dict.clear()
print ("字典删除后长度 : %d" % len(dict)) 字典删除后长度 : 0
```



##### copy

```python
#Python 字典 copy() 函数返回一个字典的浅复制。
#copy()方法语法：
dict.copy()

'''
参数
NA。
返回值
返回一个字典的浅复制。
'''

#以下实例展示了 copy()函数的使用方法：
dict1 = {'Name': 'Runoob', 'Age': 7, 'Class': 'First'}
dict2 = dict1.copy()
print ("新复制的字典为 : ",dict2)
#新复制的字典为 :  {'Age': 7, 'Name': 'Runoob', 'Class': 'First'}

#############################################

#直接赋值和 copy 的区别
# -*- coding: UTF-8 -*-
 
dict1 =  {'user':'runoob','num':[1,2,3]}
 
dict2 = dict1          # 浅拷贝: 引用对象
dict3 = dict1.copy()   # 浅拷贝：深拷贝父对象（一级目录），子对象（二级目录）不拷贝，还是引用
 
# 修改 data 数据
dict1['user']='root'
dict1['num'].remove(1)
 
# 输出结果
print(dict1) #{'user': 'root', 'num': [2, 3]}
print(dict2) #{'user': 'root', 'num': [2, 3]}
print(dict3) #{'user': 'runoob', 'num': [2, 3]}

#dict2 其实是 dict1 的引用（别名），所以输出结果都是一致的，dict3 父对象进行了深拷贝，不会随dict1 修改而修改，子对象是浅拷贝所以随 dict1 的修改而修改。
```

##### fromkeys

~~~python
#Python 字典 fromkeys() 函数用于创建一个新字典，以序列 seq 中元素做字典的键，value 为字典所有键对应的初始值。
#fromkeys() 方法语法：
dict.fromkeys(seq[, value])

```
参数
seq -- 字典键值列表。
value -- 可选参数, 设置键序列（seq）对应的值，默认为 None。
返回值
该方法返回一个新字典。
```

seq = ('name', 'age', 'sex')
dict = dict.fromkeys(seq)
print ("新的字典为 : %s" %  str(dict)) 
#新的字典为 : {'age': None, 'name': None, 'sex': None}
 
dict = dict.fromkeys(seq, 10)
print ("新的字典为 : %s" %  str(dict)) #新的字典为 : {'age': 10, 'name': 10, 'sex': 10}


#不指定值：
x = ('key1', 'key2', 'key3')
thisdict = dict.fromkeys(x)
print(thisdict) #{'key1': None, 'key2': None, 'key3': None}
~~~



##### get

~~~python
#Python 字典 get() 函数返回指定键的值，如果键不在字典中返回默认值。
#get()方法语法：
dict.get(key, default=None)

```
参数
key -- 字典中要查找的键。
default -- 如果指定的键不存在时，返回该默认值值。
返回值
返回指定键的值，如果键不在字典中返回默认值 None。
```

dict = {'Name': 'Runoob', 'Age': 27}
print ("Age 值为 : %s" %  dict.get('Age')) #Age 值为 : 27
print ("Sex 值为 : %s" %  dict.get('Sex', "NA")) #Sex 值为 : NA
~~~



##### key in dict

```python
#Python 字典 in 操作符用于判断键是否存在于字典中，如果键在字典 dict 里返回 true，否则返回 false。
而 not in 操作符刚好相反，如果键在字典 dict 里返回 false，否则返回 true。

#in 操作符语法：
key in dict

'''
参数
key -- 要在字典中查找的键。
返回值
如果键在字典里返回true，否则返回false。
'''

dict = {'Name': 'Runoob', 'Age': 7}

# 检测键 Age 是否存在
if  'Age' in dict:
    print("键 Age 存在")  #键 Age 存在
else :
    print("键 Age 不存在")
 
# 检测键 Sex 是否存在
if  'Sex' in dict:
    print("键 Sex 存在")
else :
    print("键 Sex 不存在") #键 Sex 不存在
 
 
# not in
# 检测键 Age 是否存在
dict = {'Name': 'Runoob', 'Age': 7}
if  'Age' not in dict:
    print("键 Age 不存在") 
else :
    print("键 Age 存在") 键 Age 存在
```



##### items

```python
#Python 字典 items() 方法以列表返回可遍历的(键, 值) 元组数组。
#items()方法语法：
dict.items()

'''
参数
NA。
返回值
返回可遍历的(键, 值) 元组数组。
'''
 
dict = {'Name': 'Runoob', 'Age': 7}
print ("Value : %s" %  dict.items()) 
#Value : dict_items([('Age', 7), ('Name', 'Runoob')])



#将字典的 key 和 value 组成一个新的列表：
d={1:"a",2:"b",3:"c"}
result=[]
for k,v in d.items():
    result.append(k)
    result.append(v)
print(result) #[1, 'a', 2, 'b', 3, 'c']
```



##### keys

```python
#Python3 字典 keys() 方法返回一个可迭代对象，可以使用 list() 来转换为列表。
#注意：Python2.x 是直接返回列表

#keys()方法语法：
dict.keys()

,,,
参数
NA。
返回值
返回一个迭代器。
,,,

#在使用中如果直接使用dict.keys()，那么返回值为dict_keys，并非直接的列表，若要返回列表值还需调用list函数。
>>> dict = {'Name': 'Runoob', 'Age': 7}
>>> dict.keys()
dict_keys(['Name', 'Age'])
>>> list(dict.keys())          # 转换为列表
['Name', 'Age']

#以上实例输出结果为：
#字典所有的键为 : dict_keys(['Age', 'Name'])
```



##### setdefault

```python
#Python 字典 setdefault() 方法和 get()方法 类似, 如果键不已经存在于字典中，将会添加键并将值设为默认值。

setdefault()方法语法：
dict.setdefault(key, default=None)

'''
参数
key -- 查找的键值。
default -- 键不存在时，设置的默认键值。
返回值
如果 key 在 字典中，返回对应的值。如果不在字典中，则插入 key 及设置的默认值 default，并返回 default ，default 默认值为 None。
'''


dict = {'Name': 'Runoob', 'Age': 7}
print ("Age 键的值为 : %s" %  dict.setdefault('Age', None))
print ("Sex 键的值为 : %s" %  dict.setdefault('Sex', None))
print ("新字典为：", dict)

#以上实例输出结果为：
#Age 键的值为 : 7
#Sex 键的值为 : None
#新字典为： {'Age': 7, 'Name': 'Runoob', 'Sex': None}
```



##### update

```python
#Python 字典 update() 函数把字典参数 dict2 的 key/value(键/值) 对更新到字典 dict 里。

#update() 方法语法：
dict.update(dict2)

'''
参数
dict2 -- 添加到指定字典dict里的字典。
返回值
该方法没有任何返回值。
'''

dict = {'Name': 'Runoob', 'Age': 7}
dict2 = {'Sex': 'female' }
 
dict.update(dict2)	
print ("更新字典 dict : ", dict)
#更新字典 dict :  {'Name': 'Runoob', 'Age': 7, 'Sex': 'female'}
```



##### values

```python
#Python 字典 values() 方法返回一个迭代器，可以使用 list() 来转换为列表，列表为字典中的所有值。

#values()方法语法：
dict.values()

'''
参数
NA。
返回值
返回迭代器。
'''

dict = {'Sex': 'female', 'Age': 7, 'Name': 'Zara'}
print ("字典所有值为 : ",  list(dict.values()))
#字典所有值为 :  ['female', 7, 'Zara']
```



##### pop

```python
#Python 字典 pop() 方法删除字典给定键 key 所对应的值，返回值为被删除的值。key值必须给出。 否则，返回default值。

#pop()方法语法：
pop(key[,default])

'''
参数
key: 要删除的键值
default: 如果没有 key，返回 default 值
返回值
返回被删除的值。
'''

>>> site= {'name': '菜鸟教程', 'alexa': 10000, 'url': 'www.runoob.com'}
>>> pop_obj=site.pop('name')
>>> print(pop_obj)
菜鸟教程
>>>pop_obj1=site.pop() #括号里没有参数，表示删除list数组中最后一个元素
>>>pop_obj2=site.pop(0) #0参数表示删除数组中的第一个元素
```



##### popitem

```python
#Python 字典 popitem() 方法随机返回并删除字典中的最后一对键和值。
#如果字典已经为空，却调用了此方法，就报出KeyError异常。

#popitem()方法语法：
popitem()

'''
参数
无
返回值
返回一个键值对(key,value)形式，按照 LIFO（Last In First Out 后进先出法） 顺序规则，即最末尾的键值对。
'''

site= {'name': '菜鸟教程', 'alexa': 10000, 'url': 'www.runoob.com'}
pop_obj=site.popitem()
print(pop_obj)   #('url', 'www.runoob.com')
print(site) #{'name': '菜鸟教程', 'alexa': 10000}
```

### 序列

#### 序列简介

序列是指按照位置顺序来存储数据的数据结构，也就是说能通过数值索引进行操作。实际上，python对序列的解释是：只要类型对象中重载了`__len__()`和`__getitem__()`，且它们的整数参数从0开始，就表示这个类型满足序列协议，是一个序列类型。

python有三种基本的序列类型：`列表`、`元组`和`range对象`。当然，还有特别定制的序列类型：`str`和`binary data`。

序列类型又分为可变序列和不可变序列。可变序列表示可以原处修改的序列，不可变序列意味着不允许原处修改。例如，列表是可变序列，字符串是不可变序列。

#### 序列的通用操作

下面这些操作是序列通用的，无论是可变、不可变序列。但通用并不意味着所有序列都支持这些操作，有些特殊的序列因为某些原因不支持某些操作也是合理的。

注意：python中序列操作在索引越界的时候都会报错。

##### 测试元素是否存在

`x in S`和`x not in S`，返回True或False。例如：

```python
>>> 'a' in "abcd"
True
>>> 'aa' in "abcd"
False
>>> 'ab' in "abcd"
True
>>> 3 in [1,2,3,4]
True
```

##### 加法和乘法符号

`S1 + S2`或`S * N`或`N * S`，其中S1和S2是同一种序列类型，N表示序列的重复次数。

**使用二元赋值表达式通常可以作为可变对象赋值的一种优化手段**。

例如：

```python
>>> [1,2] + [3,4]
[1, 2, 3, 4]

>>> [1,2] * 3
[1, 2, 1, 2, 1, 2]
>>> 3 * [1, 2]
[1, 2, 1, 2, 1, 2]
```

注意，序列中保存的是元素的引用地址，所以对于序列中的可变元素，`+ *`时需要注意修改的影响范围：

```python
>>> L = [1,2,3,4]
>>> L1 = [['a'],['b']]

>>> L0 = L + L1
>>> L0
[1, 2, 3, 4, ['a'], ['b']]

>>> L1[0][0] = "aa"
>>> L0
[1, 2, 3, 4, ['aa'], ['b']]
```

上面修改"a"为"aa"也会影响到`+`的结果L0，因为`['a']`是一个可变对象。同样对于`*`的重复操作，也是拷贝引用：

```python
>>> L = []
>>> L1 = [L] * 3
>>> L1
[[], [], []]

>>> L.append(3)
>>> L1
[[3], [3], [3]]
```

##### len()、max()和min()函数

len()返回序列的元素个数，也就是序列的长度。min()和max()分别返回序列中最小、最大的元素。

```python
>>> len(L), min(L), max(L)
```

##### 元素在序列中出现的次数count()

```python
>>> s="hello world"
>>> s.count("h"),s.count("o")
(1, 2)
```

##### 索引取元素

`S[i]`，i为从0开始的数值，可以取负数表示从尾部开始取。

例如：

```python
>>> L = ['a', 'b', 'c', 'd']
>>> L[0]
'a'
>>> L[1]
'b'
>>> L[-1]
'd'
```

负数的i等价于`len(S)+i`作为索引。例如，`len(S) = 3, i = -1`，表示取最后一个元素，也就是index=2的元素。

##### 分片

分片操作用于从序列中取出子序列，**它会创建新的内存块来保存取出来的序列对象**。

- `S[i:j]`：从索引位i取到索引位j，不包括j
- `S[i:]`：从索引位i开始取到最结尾
- `S[:j]`：从最开头取到索引位j，不包括j
- `S[:]`：从头取到尾，相当于拷贝了序列，但得到的是新序列
- `S[i:j:k]`：k表示取元素时的步进间隔，默认为1，表示每个元素都取，如果为2，则表示取一个跳过一个

分片的区间是左闭右开的，所以不会包括j的索引位。i和j可以是负数，负数表示从尾部开始计算索引位。例如，-1表示最后一个元素，-2表示倒数第二个元素。

特别地，如果`i = j`，则表示找到序列中的这个位置，但因为切片长度位0，所以返回空。

例如：

```python
>>> s = "hello world"
>>> len(s)
11

>>> s[0:6]
'hello '
>>> s[:6]
'hello '

>>> s[6:10]   # 不包括index=10
'worl'
>>> s[6:11]   # 所以用大于10的结束位
'world'
>>> s[6:]
'world'
>>> s[6:-1]
'worl'

>>> s[:]      # 拷贝序列得到副本
'hello world'

>>> s[::1]     # 步进为1，默认的
'hello world'
>>> s[::2]     # 每次跳过一个元素
'hlowrd'

>>> s[1:1]    # 找到index=1的位置
''
```

##### 找出第一个元素的位置index()

`index(x,i,j)`表示从序列中搜索元素x并返回第一次出现的x的位置，如果给定了i，则表示从索引位i开始搜索，给定了j则表示最多搜索到索引位为j的位置。

如果找不到元素，将报错。i和j可以是负数，但无论它们是正数还是负数，都是搜索的开始和结束位。

```python
>>> s="hello world"
>>> s.index("o")
4
>>> s.index("o",1,-1)
4
>>> s.index("o",-5)    # 从倒数第5个元素开始搜索
7
>>> s.index("a")       # 搜索不到时报错

Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
ValueError: substring not found
```

#### 不可变序列的操作

相比可变序列，不可变序列的唯一操作是可以支持内置的`hash()`操作。可变序列无法hash()。

```python
>>> hash("asd")
-2014632507

>>> hash((1,23))
1320437575

>>> hash([1,23])
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
TypeError: unhashable type: 'list'
```

能够hash的不可变序列，意味着能作为dict的key，能保存到set或frozenset中。

#### 可变序列的操作

1. `s[i] = x`、`s[i:j] = t`将序列中的元素替换成x或可迭代对象t
2. `s[i:j:K] = t`将序列中的元素替换成可迭代对象t，t的长度必须和`s[i:j:k]`的长度一样
3. `del s[i]`、`del s[i:j]`删除序列中的元素，等价于`s[i] = []`、`s[i:j] = []`
4. `del s[i:j:k]`删除序列中的某些元素，k为步进值
5. `s.remove(x)`：移除第一次出现的元素x
6. `s.clear()`表示清空序列中的所有元素，等价于`del s[:]`
7. `s.pop([i])`表示移除序列s中的第i个元素并返回这个元素，中括号表示可选，如果没有参数，默认移除最后一个元素
8. `s.append(x)`向序列的尾部追加元素x，等价于`s[len(s):len(s)] = [x]`
9. `s.extend(t)`或`s += t`表示将t扩展到序列s的尾部，等价于`s[len(s):len(s)] = t`
10. `s.insert(i,x)`表示将x插入到序列中的i索引位置处，等价于`s[i:i] = [x]`
11. `s *= n`表示将序列n的元素重复n次追加到s的尾部
12. `s.copy()`表示拷贝序列得到一个新的序列副本，等价于`s[:]`
13. `s.reverse()`原地反转序列s，为了节约内存空间，所以是原地反转，不会返回反转后的序列

对于序列，还有一个内置函数`reversed(SEQ)`。与之对应的，还有一个内置函数sorted()，但它操作的对象是可迭代对象，并不一定总是序列。

##### 序列元素赋值

```python
>>> L = ['aa','bb','cc','dd','ee','ff']
>>> L1 = [1,2,3,4]

>>> L[0] = "a"
>>> L
['a', 'bb', 'cc', 'dd', 'ee', 'ff']

>>> L[1:2] = L1
>>> L
['a', 1, 2, 3, 4, 'cc', 'dd', 'ee', 'ff']

>>> L[::2] = [1,2,3,4,5]
>>> L
[1, 1, 2, 3, 3, 'cc', 4, 'ee', 5]
```

##### 删除元素

删除相关操作有del、remove()、pop()、clear()。

```python
>>> L = ['aa','bb','cc','dd','ee','ff']
>>> del L[1]
>>> L
['aa', 'cc', 'dd', 'ee', 'ff']
>>> del L[1:2]
>>> L
['aa', 'dd', 'ee', 'ff']
>>> del L[::2]
>>> L
['dd', 'ff']

>>> L = ['aa','bb','cc','dd','ee','ff']
>>> L.remove('aa')
>>> L
['bb', 'cc', 'dd', 'ee', 'ff']

>>> L.pop()
'ff'
>>> L
['bb', 'cc', 'dd', 'ee']

>>> L.pop(2)
'dd'
>>> L
['bb', 'cc', 'ee']

>>> L.clear()
>>> L
[]
```

##### 添加元素

相关操作有append()、extend()、insert()、`s *= n`。

```python
>>> L = ['aa', 'bb', 'cc', 'dd', 'ee']
>>> L1 = [1,2,3,4]

>>> L.append("ff")
>>> L
['aa', 'bb', 'cc', 'dd', 'ee', 'ff']

>>> L.insert(1,"a")
>>> L
['aa', 'a', 'bb', 'cc', 'dd', 'ee', 'ff']

>>> L.extend(L1)
>>> L
['aa', 'a', 'bb', 'cc', 'dd', 'ee', 'ff', 1, 2, 3, 4]

>>> L1 * 2
[1, 2, 3, 4, 1, 2, 3, 4]
```

##### 其它操作

拷贝序列copy()、反转序列reverse()。

```python
>>> L = ['aa', 'bb', 'cc', 'dd', 'ee']

>>> L1 = L.copy()
>>> L1
['aa', 'bb', 'cc', 'dd', 'ee']

>>> L.reverse()
>>> L
['ee', 'dd', 'cc', 'bb', 'aa']
```

还有一个可用于序列的内置函数reversed()，它反转序列，并返回可迭代对象。所以，如果要将它展现出来，需要构建容器。例如:

```python
>>> L = ['aa', 'bb', 'cc', 'dd', 'ee']

>>> list(reversed(L))
['ee', 'dd', 'cc', 'bb', 'aa']

>>> set(reversed(L))
{'aa', 'bb', 'ee', 'cc', 'dd'}
```

#### 序列解包

```python
a, *b = 'long'
```

当使用一个`*`前缀变量的时候，表示将**序列**中**对应的元素**全部收集到一个**列表**中(注意，总是一个列表)，这个列表名为`*`开头的那个变量名。`*`号可以出现在任意位置处，只要赋值的时候能前后对应位置关系即可。

注意其中的几个关键字：序列、对应的元素、列表

- 序列意味着可以是列表、元组、字符串等等
- 列表意味着只要收集不报错，赋值给解包变量的一定是一个列表
- 对应的元素意味着可能收集到0或任意个元素到列表。

不管如何，收集的结果总是列表，只不过可能是空列表或者只有一个元素的列表。

例如：

```python
L = ['aa','bb','cc','dd']
a, *b = L           # a='aa',b=['bb','cc','dd']
a, b, *c = L        # a='aa',b='bb',c=['cc','dd']
a,*b,d = L          # a='aa',d='dd',b=['bb','cc']
*a,d = L            # a=['aa','bb','cc'],d='dd'
a,b,c,*d = L        # a='aa',b='bb',c='cc',d=['dd']
a,b,c,d,*e = L      # a='aa',b='bb',c='cc',d='dd',e=[]
```

两个注意事项：

1. 因为序列解包是根据元素位置来进行赋值的，所以不能出现多个解包变量
2. 如果将序列直接赋值给`单个解包变量`时(即没有普通变量)，这个解包变量必须放在`列表`或`元组`中

```python
a,*b,c,*d = L     # 错误
*a = L            # 错误
[*a] = L          # 正确
(*a) = L          # 正确
```

之所以单个解包变量时必须放在元组或变量中，看下面两个等价的例子就很容易理解了：

```python
a, *b = L
(a, *b) = L
```

序列解包是切片的便捷替代方式。能用序列解包的，都能用切片来实现，但切片要输入额外的各种字符。例如：

```python
a,b,c = L[0],L[1],L[2:]
a,b,*c = L
```

需要注意，`解包`返回的一定是`列表`，但**序列切片返回的内容则取决于序列的类型**。例如下面元组的切片返回的是元组，而不是列表：

```python
>>> T=('aa','bb','cc','dd')
>>> a,b,c = T[0],T[1],T[2:]
>>> a,b,c
('aa', 'bb', ('cc', 'dd'))
```

### 解析-生成式

Python支持各种解析(comprehension)操作，比如`列表解析`、`集合解析`、`元组解析`、`字典解析`。它们根据某些元素来创建(推导)出一个新的列表、集合、元组、字典等。所以有的地方也称为推导，比如列表推导、集合推导等。

```python
#列表解析的示例：
>>> [ i*2 for i in range(10) if i % 2 == 0 ]
[0, 4, 8, 12, 16]

#这里是列表解析，因为使用的中括号[ xxxx ]，它表示根据条件推导出一个新的列表。
```

Python中几种内置类型的解析规则为：

- 如果使用的是`中括号`，表示列表解析
- 如果使用的是`大括号`，表示集合解析
- 如果使用的是`大括号，且里面的元素是key:value`模式，表示字典解析

**注意：如果使用的是`括号`，表示的是`生成器表达式`，而不是解析。**

```python
# 集合解析
>>> { i*2 for i in "abcd"}
{'aa', 'cc', 'dd', 'bb'}

# 字典解析
>>> { k:v for k,v in zip(("one","two","three"),(1,2,3)) }
{'one': 1, 'two': 2, 'three': 3}

>>> { k: k*2 for k in "abcd" }
{'a': 'aa', 'b': 'bb', 'c': 'cc', 'd': 'dd'}
```



与解析操作等价的普通循环

python中的解析行为由`for`这个迭代工具来迭代，它和普通的for循环逻辑一样，但用法稍有不同。从前面的示例中也可以看出解析操作的外部表达式部分在for关键字的前面，而普通for循环的表达式则是在for关键字后面。

解析操作也能由普通的循环来生成。例如：

```python
# for循环实现列表解析操作
L1 = []
for i in range(10):
  if i % 2 == 0 :
    L1.append(i * 2)


# 列表解析
L2 = [ i * 2 for i in range(10) if i % 2 == 0 ]

print(L1) #[0, 4, 8, 12, 16]
print(L2) #
```

而且，解析操作比普通的for循环运行速度更快，解析操作在Python解释器中是完全使用C来运行的，而普通for循环则是在python VM中通过步进的方式运行的。一般来说，解析操作和map函数速度差不多(解释器中都是C的运行方式)，它们都要比普通for快上1-2倍。特别是要生成的元素较多时，解析操作往往要比等价的普通循环快上一倍多。



**嵌套的解析**

解析操作可以变得更加复杂，比如可以进行for嵌套。

```python
>>> [x + y for x in "abcd" for y in "ABCD"]
['aA', 'aB', 'aC', 'aD', 'bA', 'bB', 'bC', 'bD', 'cA', 'cB', 'cC', 'cD', 'dA', 'dB', 'dC', 'dD']
```

它等价于：

```python
L = []
for x in "abcd":
  for y in "ABCD":
    L.append(x + y)
```

for嵌套的时候，每一个for中用于筛选元素的if语句都是可选的。

例如，下面的嵌套for解析中，使用偶数和奇数的组合：

```python
>>> [ (x,y) for x in range(5) if x % 2 == 0 for y in range(5) if y % 2 ==1 ]
[(0, 1), (0, 3), (2, 1), (2, 3), (4, 1), (4, 3)]
```

这个解析表达式等价于：

```python
>>> L = []
>>> for x in range(5):
...     if x % 2 == 0:
...         for y in range(5):
...             if y % 2 == 1:
...                 L.append((x, y))

[(0, 1), (0, 3), (2, 1), (2, 3), (4, 1), (4, 3)]
```



### 练习

#### 在屏幕上显示跑马灯文字。

```python
import os
import time


def main():
    content = '北京欢迎你为你开天辟地…………'
    while True:
        # 清理屏幕上的输出
        os.system('cls')  # os.system('clear')
        print(content)
        # 休眠200毫秒
        time.sleep(0.2)
        content = content[1:] + content[0]


if __name__ == '__main__':
    main()
```

#### 设计一个函数产生指定长度的验证码

```python
import random


def generate_code(code_len=4):
    """
    生成指定长度的验证码

    :param code_len: 验证码的长度(默认4个字符)

    :return: 由大小写英文字母和数字构成的随机验证码
    """
    all_chars = '0123456789abcdefghijklmnopqrstuvwxyzABCDEFGHIJKLMNOPQRSTUVWXYZ'
    last_pos = len(all_chars) - 1
    code = ''
    for _ in range(code_len):
        index = random.randint(0, last_pos)
        code += all_chars[index]
    return code
```

#### 设计一个函数返回给定文件名的后缀名。

```python
def get_suffix(filename, has_dot=False):
    """
    获取文件名的后缀名

    :param filename: 文件名
    :param has_dot: 返回的后缀名是否需要带点
    :return: 文件的后缀名
    """
    pos = filename.rfind('.')
    if 0 < pos < len(filename) - 1:
        index = pos if has_dot else pos + 1
        return filename[index:]
    else:
        return ''
```

#### 设计一个函数返回传入的列表中最大和第二大的元素的值。

```python
def max2(x):
    m1, m2 = (x[0], x[1]) if x[0] > x[1] else (x[1], x[0])
    for index in range(2, len(x)):
        if x[index] > m1:
            m2 = m1
            m1 = x[index]
        elif x[index] > m2:
            m2 = x[index]
    return m1, m2
```

#### 计算指定的年月日是这一年的第几天。

```python
def is_leap_year(year):
    """
    判断指定的年份是不是闰年

    :param year: 年份
    :return: 闰年返回True平年返回False
    """
    return year % 4 == 0 and year % 100 != 0 or year % 400 == 0


def which_day(year, month, date):
    """
    计算传入的日期是这一年的第几天

    :param year: 年
    :param month: 月
    :param date: 日
    :return: 第几天
    """
    days_of_month = [
        [31, 28, 31, 30, 31, 30, 31, 31, 30, 31, 30, 31],
        [31, 29, 31, 30, 31, 30, 31, 31, 30, 31, 30, 31]
    ][is_leap_year(year)]
    total = 0
    for index in range(month - 1):
        total += days_of_month[index]
    return total + date


def main():
    print(which_day(1980, 11, 28))
    print(which_day(1981, 12, 31))
    print(which_day(2018, 1, 1))
    print(which_day(2016, 3, 1))


if __name__ == '__main__':
    main()
```

#### 打印[杨辉三角](https://zh.wikipedia.org/wiki/杨辉三角形)。

参考答案：

```python
def main():
    num = int(input('Number of rows: '))
    yh = [[]] * num
    for row in range(len(yh)):
        yh[row] = [None] * (row + 1)
        for col in range(len(yh[row])):
            if col == 0 or col == row:
                yh[row][col] = 1
            else:
                yh[row][col] = yh[row - 1][col] + yh[row - 1][col - 1]
            print(yh[row][col], end='\t')
        print()


if __name__ == '__main__':
    main()
```

#### 双色球选号。

```python
from random import randrange, randint, sample


def display(balls):
    """
    输出列表中的双色球号码
    """
    for index, ball in enumerate(balls):
        if index == len(balls) - 1:
            print('|', end=' ')
        print('%02d' % ball, end=' ')
    print()


def random_select():
    """
    随机选择一组号码
    """
    red_balls = [x for x in range(1, 34)]
    selected_balls = []
    selected_balls = sample(red_balls, 6)
    selected_balls.sort()
    selected_balls.append(randint(1, 16))
    return selected_balls


def main():
    n = int(input('机选几注: '))
    for _ in range(n):
        display(random_select())


if __name__ == '__main__':
    main()
```

> **说明：** 上面使用random模块的sample函数来实现从列表中选择不重复的n个元素。

#### 约瑟夫环问题

```python
"""
《幸运的基督徒》
有15个基督徒和15个非基督徒在海上遇险，为了能让一部分人活下来不得不将其中15个人扔到海里面去，有个人想了个办法就是大家围成一个圈，由某个人开始从1报数，报到9的人就扔到海里面，他后面的人接着从1开始报数，报到9的人继续扔到海里面，直到扔掉15个人。由于上帝的保佑，15个基督徒都幸免于难，问这些人最开始是怎么站的，哪些位置是基督徒哪些位置是非基督徒。
"""


def main():
    persons = [True] * 30
    counter, index, number = 0, 0, 0
    while counter < 15:
        if persons[index]:
            number += 1
            if number == 9:
                persons[index] = False
                counter += 1
                number = 0
        index += 1
        index %= 30
    for person in persons:
        print('基' if person else '非', end='')


if __name__ == '__main__':
    main()
```

#### 井字棋游戏。

```python
import os


def print_board(board):
    print(board['TL'] + '|' + board['TM'] + '|' + board['TR'])
    print('-+-+-')
    print(board['ML'] + '|' + board['MM'] + '|' + board['MR'])
    print('-+-+-')
    print(board['BL'] + '|' + board['BM'] + '|' + board['BR'])


def main():
    init_board = {
        'TL': ' ', 'TM': ' ', 'TR': ' ',
        'ML': ' ', 'MM': ' ', 'MR': ' ',
        'BL': ' ', 'BM': ' ', 'BR': ' '
    }
    begin = True
    while begin:
        curr_board = init_board.copy()
        begin = False
        turn = 'x'
        counter = 0
        os.system('clear')
        print_board(curr_board)
        while counter < 9:
            move = input('轮到%s走棋, 请输入位置: ' % turn)
            if curr_board[move] == ' ':
                counter += 1
                curr_board[move] = turn
                if turn == 'x':
                    turn = 'o'
                else:
                    turn = 'x'
            os.system('clear')
            print_board(curr_board)
        choice = input('再玩一局?(yes|no)')
        begin = choice == 'yes'


if __name__ == '__main__':
    main()
```

## 函数

函数是组织好的，可重复使用的，用来实现单一，或相关联功能的代码段。

函数能提高应用的模块性，和代码的重复利用率。

### 定义函数

规则：

- 函数代码块以 `def` 关键词开头，后接函数标识符名称和圆括号` ()`。
- 任何传入参数和自变量必须放在圆括号中间，圆括号之间可以用于定义参数。
- 函数的第一行语句可以选择性地使用文档字符串—用于存放函数说明。
- 函数内容以`冒号`起始，并且缩进。
- `return [表达式]`结束函数，选择性地返回一个值给调用方。不带表达式的return相当于返回 `None`。

```python
Python 定义函数使用 def 关键字，一般格式如下：

def 函数名（参数列表）:
    函数体
    


#让我们使用函数来输出"Hello World！"：
>>>def hello() :
   print("Hello World!")
>>> hello()
Hello World!
>>>


#默认情况下，参数值和参数名称是按函数声明中定义的顺序匹配起来的。
# 计算面积函数
def area(width, height):
    return width * height

w = 4
h = 5
print("width =", w, " height =", h, " area =", area(w, h)) 
#width = 4  height = 5  area = 20
```



### 函数调用

定义了函数之后，就相当于有了一个具有某些功能的代码，想要让这些代码能够执行，需要调用它

调用函数很简单的，通过 **函数名()** 即可完成调用

```python
# 定义函数
def printme( str ):
   # 打印任何传入的字符串
   print (str)
   return
 
# 调用函数
printme("我要调用用户自定义函数!") #我要调用用户自定义函数! 
printme("再次调用同一函数") #再次调用同一函数
```

### 参数传递

在 python 中，`类型属于对象`，变量是没有类型的：

```python
a=[1,2,3]
a="Runoob"
```


以上代码中，[1,2,3] 是 List 类型，"Runoob" 是 String 类型，而变量 a 是没有类型，她仅仅是一个对象的`引用`（一个指针），可以是指向 List 类型对象，也可以是指向 String 类型对象。



#### 可更改(mutable)与不可更改(immutable)对象

在 python 中，`strings`, `tuples`, 和 `numbers` 是`不可更改`的对象，而 `list`,`dict `等则是可以`修改的对象`。

- **`不可变类型`：**变量赋值 **a=5** 后再赋值 **a=10**，这里实际是新生成一个 int 值对象 10，再让 a 指向它，而 5 被丢弃，不是改变 a 的值，相当于新生成了 a。
- **`可变类型`：**变量赋值 **la=[1,2,3,4]** 后再赋值 **la[2]=5** 则是将 list la 的第三个元素值更改，本身la没有动，只是其内部的一部分值被修改了。

python 函数的参数传递：

- **不可变类型：**`值传递`，如 整数、字符串、元组。如 fun(a)，传递的只是 a 的值，没有影响 a 对象本身。如果在 fun(a)）内部修改 a 的值，则是新生成来一个 a。
- **可变类型：**`引用传递`，如 `列表`，`字典`。如 fun(la)，则是将 la 真正的传过去，修改后 fun 外部的 la 也会受影响

python 中`一切都是对象`，严格意义我们`不能说值传递还是引用传递`，我们应该说传不可变对象和传可变对象。

#### python 传不可变对象实例

通过` id()`函数来查看内存地址变化：

```python
def change(a):
    print(id(a))   # 指向的是同一个对象 4379369136
    a=10
    print(id(a))   # 一个新对象
 
a=1
print(id(a)) #4379369136
change(a) #4379369424
```

#### 传可变对象实例

```python

#可变对象在函数里修改了参数，那么在调用这个函数的函数里，原始的参数也被改变了。例如：
def changeme( mylist ):
   "修改传入的列表"
   mylist.append([1,2,3,4])
   print ("函数内取值: ", mylist)
   return

# 调用changeme函数
mylist = [10,20,30]
changeme( mylist ) #函数内取值:  [10, 20, 30, [1, 2, 3, 4]]
print ("函数外取值: ", mylist) #函数外取值:  [10, 20, 30, [1, 2, 3, 4]]
```

### 参数

以下是调用函数时可使用的正式参数类型：

- 必需参数
- 关键字参数
- 默认参数
- 不定长参数

#### 必需参数

`必需参数`须以正确的顺序传入函数。调用时的数量必须和声明时的一样。

```python
#调用 printme() 函数，你必须传入一个参数，不然会出现语法错误：

def printme( str ):
   "打印任何传入的字符串"
   print (str)
   return
 
# 调用 printme 函数，不加参数会报错
printme()

#以上实例输出结果：
Traceback (most recent call last):
  File "test.py", line 10, in <module>
    printme()
TypeError: printme() missing 1 required positional argument: 'str'
```

#### 关键字参数

```python

#关键字参数和函数调用关系紧密，函数调用使用关键字参数来确定传入的参数值。
#使用关键字参数允许函数调用时参数的顺序与声明时不一致，因为 Python 解释器能够用参数名匹配参数值。

 
def printme( str ):
   "打印任何传入的字符串"
   print (str)
   return
 
#调用printme函数
printme( str = "菜鸟教程") #菜鸟教程



#函数参数的使用不需要使用指定顺序：
def printinfo( name, age ):
   "打印任何传入的字符串"
   print ("名字: ", name) #名字:  runoob
   print ("年龄: ", age) #
   return
 
#调用printinfo函数
printinfo( age=50, name="runoob" )
```

#### 默认参数

```python

#调用函数时，如果没有传递参数，则会使用默认参数。以下实例中如果没有传入 age 参数，则使用默认值：
def printinfo( name, age = 35 ):
   "打印任何传入的字符串"
   print ("名字: ", name)
   print ("年龄: ", age)
   return
 
#调用printinfo函数
printinfo( age=50, name="runoob" )
print ("------------------------")
printinfo( name="runoob" )

#以上实例输出结果：
名字:  runoob
年龄:  50
------------------------
名字:  runoob
年龄:  35
    
    
#默认参数必须放在最后面，否则会报：
#SyntaxError: non-default argument follows default argument
def printinfo( age=35,name):   # 默认参数不在最后，会报错
    "打印任何传入的字符串"
    print("名字: ", name)
    print("年龄: ", age)
    return
```

#### 不定长参数

```python

#当函数参数不确定时。这些参数叫做不定长参数，声明时不会命名。

#基本语法如下：
def functionname([formal_args,] *var_args_tuple ):
   "函数_文档字符串"
   function_suite
   return [expression]

#加了星号 * 的参数会以元组(tuple)的形式导入，存放所有未命名的变量参数。
def printinfo( arg1, *vartuple ):
   "打印任何传入的参数"
   print ("输出: ")
   print (arg1)
   print (vartuple)
 
# 调用printinfo 函数
printinfo( 70, 60, 50 )

#以上实例输出结果：
输出: 
70
(60, 50)


#如果在函数调用时没有指定参数，它就是一个空元组。我们也可以不向函数传递未命名的变量。如下实例：
def printinfo( arg1, *vartuple ):
   "打印任何传入的参数"
   print ("输出: ")
   print (arg1)
   for var in vartuple:
      print (var)
   return
 
# 调用printinfo 函数
printinfo( 10 )
printinfo( 70, 60, 50 )

#以上实例输出结果：
输出:
10
输出:
70
60
50

# 在参数名前面的*表示args是一个可变参数
def add(*args):
    total = 0
    for val in args:
        total += val
    return total

# 在调用add函数时可以传入0个或多个参数
print(add())
print(add(1))
print(add(1, 2))
print(add(1, 2, 3))
print(add(1, 3, 5, 7, 9))

#############################################################
#还有一种就是参数带两个星号 **基本语法如下：
def functionname([formal_args,] **var_args_dict ):
   "函数_文档字符串"
   function_suite
   return [expression]

#加了两个星号 ** 的参数会以字典的形式导入。
def printinfo( arg1, **vardict ):
   "打印任何传入的参数"
   print ("输出: ")
   print (arg1)
   print (vardict)
 
# 调用printinfo 函数
printinfo(1, a=2,b=3)

#以上实例输出结果：
输出: 
1
{'a': 2, 'b': 3}


##################################################################
#声明函数时，参数中星号 * 可以单独出现，例如:
def f(a,b,*,c):
    return a+b+c

#如果单独出现星号 * 后的参数必须用关键字传入。
f(1,2,3)   # 报错
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
TypeError: f() takes 2 positional arguments but 3 were given
    
f(1,2,c=3) # 正常 6
```

### 匿名函数

python 使用 `lambda` 来创建匿名函数。

所谓匿名，意即不再使用 `def` 语句这样标准的形式定义一个函数。

lambda 只是一个`表达式`，函数体比 def 简单很多。
lambda的主体是一个表达式，而不是一个代码块。仅仅能在lambda表达式中封装有限的逻辑进去。
lambda 函数拥有自己的`命名空间`，且不能访问自己参数列表之外或全局命名空间里的参数。
虽然lambda函数看起来只能写一行，却不等同于C或C++的内联函数，后者的目的是调用小函数时不占用栈内存从而增加运行效率。

```python
#lambda 函数的语法只包含一个语句，如下：
lambda [arg1 [,arg2,.....argn]]:expression

 
sum = lambda arg1, arg2: arg1 + arg2
 
# 调用sum函数
print ("相加后的值为 : ", sum( 10, 20 )) #相加后的值为 :  30
print ("相加后的值为 : ", sum( 20, 20 )) #相加后的值为 :  40


#lambda 匿名函数也是可以使用"关键字参数"进行参数传递
>>> g= lambda x,y : x**2+y**2
>>> g(2,3)
13
>>> g(y=3,x=2)
13

#同样地，lambda 匿名函数也可以设定默认值
>>> g= lambda x=0,y=0 : x**2+y**2
>>> g(2,3)
13
>>> g(2)
4
>>> g(y=3)
9
#注意：如果只打算给其中一部分参数设定默认值，那么应当将其放在靠后的位置（和定义函数时一样，避免歧义），否则会报错。
```

### return语句

`return [表达式]` 语句用于`退出函数`，选择性地向调用方返回一个表达式。不带参数值的return语句返回`None`。

```python
def sum( arg1, arg2 ):
   # 返回2个参数的和."
   total = arg1 + arg2
   print ("函数内 : ", total)
   return total
 
# 调用sum函数
total = sum( 10, 20 ) #函数内 :  30
print ("函数外 : ", total) #函数外 :  30
```

### 函数多返回值

python的函数支持返回多个值。**返回多个值时，默认以`tuple`的方式返回**。

例如，下面两个函数的定义是完全等价的。

```python
def f():
    return 1,2

def f():
    return (1,2)


#如果将函数调用的返回值赋值给对应个数的变量，它会一一对应的赋值，这很容易理解。下面是等价的：
a, b = f()     # a=1, b=2
(a, b) = f()


#如果赋值给一个变量，将会把整个元组赋值给变量。下面是等价的，a表示整个元组(1,2)：
1a = f()
(a) = f()
```

### 丢弃返回值

很多时候，多个返回值并非全都是所需的，这时候需要丢弃某些返回值。python有几种方式只获取部分返回值：



```python
#1. 直接放在空上下文，不进行任何赋值，将丢弃所有返回值
# f()的返回值全丢弃
def f():
    return 1,2
f()

#2. 因为返回值是元组，所以可以通过索引取得某个或某几个返回值
a = f()[0]
b = f()[1]

#3. 使用下划线`_`
# 丢弃第二个返回值
a, _ = f()

#4. 使用双下划线`__`或更多下划线`___________`
# 丢弃第二个返回值
a, __ = f()
```

其中第三种方式"使用下划线"不是很安全，因为下划线`_`在python中有多种意义。而且正好有两种意义在某些情况下可能会产生冲突。所以，建议使用第四种方式。



### 强制位置参数

Python3.8 新增了一个函数形参语法 `/ `用来指明函数形参必须使用指定位置参数，不能使用关键字参数的形式。

```python
#在以下的例子中，形参 a 和 b 必须使用指定位置参数，c 或 d 可以是位置形参或关键字形参，而 e 或 f 要求为关键字形参:
def f(a, b, /, c, d, *, e, f):
    print(a, b, c, d, e, f)
    
#以下使用方法是正确的:
f(10, 20, 30, d=40, e=50, f=60)

#以下使用方法会发生错误:
f(10, b=20, c=30, d=40, e=50, f=60)   # b 不能使用关键字参数的形式
f(10, 20, 30, 40, 50, f=60)           # e 必须使用关键字参数的形式
```

### 练习

#### 实现计算求最大公约数和最小公倍数的函数。

```python
def gcd(x, y):
    """求最大公约数"""
    (x, y) = (y, x) if x > y else (x, y)
    for factor in range(x, 0, -1):
        if x % factor == 0 and y % factor == 0:
            return factor


def lcm(x, y):
    """求最小公倍数"""
    return x * y // gcd(x, y)
```

#### 实现判断一个数是不是回文数的函数。

```python
def is_palindrome(num):
    """判断一个数是不是回文数"""
    temp = num
    total = 0
    while temp > 0:
        total = total * 10 + temp % 10
        temp //= 10
    return total == num
```

#### 实现判断一个数是不是素数的函数。

```python
def is_prime(num):
    """判断一个数是不是素数"""
    for factor in range(2, int(num ** 0.5) + 1):
        if num % factor == 0:
            return False
    return True if num != 1 else False
```

#### 写一个程序判断输入的正整数是不是回文素数。

```python
if __name__ == '__main__':
    num = int(input('请输入正整数: '))
    if is_palindrome(num) and is_prime(num):
        print('%d是回文素数' % num)
```

> **注意**：通过上面的程序可以看出，当我们**将代码中重复出现的和相对独立的功能抽取成函数**后，我们可以**组合使用这些函数**来解决更为复杂的问题，这也是我们为什么要定义和使用函数的一个非常重要的原因。



## 模块

### 引入

```python
def foo():
    print('hello, world!')


def foo():
    print('goodbye, world!')


# 下面的代码会输出什么呢？
foo()

#################################################

#module1.py
def foo():
    print('hello, world!')
    
#module2.py
def foo():
    print('goodbye, world!')
    
#test.py
from module1 import foo
# 输出hello, world!
foo()

#test2.py
from module2 import foo
# 输出goodbye, world!
foo()

###############################################################

#也可以按照如下所示的方式来区分到底要使用哪一个foo函数。
#test.py
import module1 as m1
import module2 as m2

m1.foo()
m2.foo()

###############################################################

#但是如果将代码写成了下面的样子，那么程序中调用的是最后导入的那个foo，因为后导入的foo覆盖了之前导入的foo。
#test.py
from module1 import foo
from module2 import foo
# 输出goodbye, world!
foo()


#test2.py
from module2 import foo
from module1 import foo
# 输出hello, world!
foo()
```



模块是一个包含所有你定义的函数和变量的文件，其后缀名是`.py`。模块可以被别的程序引入，以使用该模块中的函数等功能。这也是使用 python 标准库的方法。

```python
#使用 python 标准库中模块的例子。

#!/usr/bin/python3
# 文件名: using_sys.py
import sys
 
print('命令行参数如下:')
for i in sys.argv:
   print(i)
 
print('\n\nPython 路径为：', sys.path, '\n')

#执行结果如下所示：
$ python using_sys.py 参数1 参数2
命令行参数如下:
using_sys.py
参数1
参数2
```

1. import sys 引入 python 标准库中的 sys.py 模块；这是引入某一模块的方法。
2. sys.argv 是一个包含命令行参数的列表。
3. sys.path 包含了一个 Python 解释器自动查找所需模块的路径的列表。

### import 语句

`modname.itemname` 这样的表示法来访问模块内的函数。

```python
#想使用 Python 源文件，只需在另一个源文件里执行 import 语句，语法如下：
import module1[, module2[,... moduleN]
```

```python
#当解释器遇到 import 语句，如果模块在当前的搜索路径就会被导入。

#搜索路径是一个解释器会先进行搜索的所有目录的列表。如想要导入模块 support，需要把命令放在脚本的顶端：
#support.py 文件代码
def print_func( par ):
    print ("Hello : ", par)
    return
    
#test.py 引入 support 模块：
#test.py 文件代码

# 导入模块
import support
 
# 现在可以调用模块里包含的函数了
support.print_func("Runoob") #Hello :  Runoob
```

一个模块只会被导入一次，不管你执行了多少次`import`。这样可以防止导入模块被一遍又一遍地执行。

当我们使用import语句的时候，Python解释器是怎样找到对应的文件的呢？

这就涉及到Python的搜索路径，搜索路径是由一系列目录名组成的，Python解释器就依次从这些目录中去寻找所引入的模块。

这看起来很像环境变量，事实上，也可以通过`定义环境变量`的方式来确定搜索路径。

`搜索路径`是在Python编译或安装的时候确定的，安装新的库应该也会修改。搜索路径被存储在`sys`模块中的`path`变量，做一个简单的实验，在交互式解释器中，输入以下代码：

```python
>>> import sys
>>> sys.path
['', 'D:\\env\\Python\\Python37\\python37.zip', 'D:\\env\\Python\\Python37\\DLLs', 'D:\\env\\Python\\Python37\\lib', 'D:\\env\\Python\\Python37', 'C:\\Users\\86138\\AppData\\Roaming\\Python\\Python37\\site-packages', 'D:\\env\\Python\\Python37\\lib\\site-packages']


>>> import sys
>>> sys.path
['', '/usr/lib/python3.4', '/usr/lib/python3.4/plat-x86_64-linux-gnu', '/usr/lib/python3.4/lib-dynload', '/usr/local/lib/python3.4/dist-packages', '/usr/lib/python3/dist-packages']
```

`sys.path `输出是一个`列表`，其中第一项是`空串`''，代表`当前目录`（若是从一个脚本中打印出来的话，可以更清楚地看出是哪个目录），亦即我们执行python解释器的目录（对于脚本的话就是运行的脚本所在的目录）。

因此若像我一样在当前目录下存在与要引入模块同名的文件，就会把要引入的模块屏蔽掉。

了解了搜索路径的概念，就可以在脚本中修改`sys.path`来引入一些不在搜索路径中的模块。

现在，在解释器的当前目录或者 sys.path 中的一个目录里面来创建一个fibo.py的文件，代码如下：

```python
# 斐波那契(fibonacci)数列模块
 
def fib(n):    # 定义到 n 的斐波那契数列
    a, b = 0, 1
    while b < n:
        print(b, end=' ')
        a, b = b, a+b
    print()
 
def fib2(n): # 返回到 n 的斐波那契数列
    result = []
    a, b = 0, 1
    while b < n:
        result.append(b)
        a, b = b, a+b
    return result
```

然后进入Python解释器，使用下面的命令导入这个模块：

```python
>>> import fibo
```

这样做并没有把直接定义在fibo中的函数名称写入到当前符号表里，只是把模块fibo的名字写到了那里。

可以使用模块名称来访问函数：

```python
>>>fibo.fib(1000)
1 1 2 3 5 8 13 21 34 55 89 144 233 377 610 987
>>> fibo.fib2(100)
[1, 1, 2, 3, 5, 8, 13, 21, 34, 55, 89]
>>> fibo.__name__
'fibo'
```

如果你打算经常使用一个函数，你可以把它赋给一个本地的名称：

```python
>>> fib = fibo.fib
>>> fib(500)
1 1 2 3 5 8 13 21 34 55 89 144 233 377
```

### from … import 语句

这种导入的方法不会把被导入的模块的名称放在当前的字符表中（所以在这个例子里面，fibo 这个名称是没有定义的）

```python
#Python 的 from 语句让你从模块中导入一个指定的部分到当前命名空间中，语法如下：
from modname import name1[, name2[, ... nameN]]

#例如，要导入模块 fibo 的 fib 函数，使用如下语句：
>>> from fibo import fib, fib2
>>> fib(500)
1 1 2 3 5 8 13 21 34 55 89 144 233 377

#这个声明不会把整个fibo模块导入到当前的命名空间中，它只会将fibo里的fib函数引入进来。
```

### from … import * 语句

`from … import * `语句把所有的名字都导入进来，但是那些由单一下划线（`_`）开头的名字不在此例。

```python
#把一个模块的所有内容全都导入到当前的命名空间也是可行的，只需使用如下声明：
from modname import *

#这提供了一个简单的方法来导入一个模块中的所有项目。然而这种声明不该被过多地使用。
```

### \__name__属性

模块除了方法定义，还可以包括可执行的代码。这些代码一般用来初始化这个模块。这些代码只有在第一次被导入时才会被执行。

一个模块被另一个程序第一次引入时，其主程序将运行。如果我们想在模块被引入时，模块中的某一程序块不执行，我们可以用`__name__`属性来使该程序块仅在该模块自身运行时执行。

```python
def main():
    # Todo: Add your code here
    pass


if __name__ == '__main__':
    main()
```



```python
# Filename: using_name.py

if __name__ == '__main__':
   print('程序自身在运行')
else:
   print('我来自另一模块')

#运行输出如下：
$ python using_name.py
程序自身在运行

$ python
>>> import using_name
我来自另一模块
```

**说明：** 每个模块都有一个`__name__`属性，当其值是'`__main__`'时，表明该模块自身在运行，否则是被引入。

说明：**`__name__`** 与 `__main__`底下是`双下划线`

### \__all__属性

### dir() 函数

内置的函数` dir() `可以找到模块内定义的所有名称。以一个字符串列表的形式返回:

```python
>>> import fibo, sys
>>> dir(fibo)
['__name__', 'fib', 'fib2']
>>> dir(sys)  
['__displayhook__', '__doc__', '__excepthook__', '__loader__', '__name__',
 '__package__', '__stderr__', '__stdin__', '__stdout__',
 '_clear_type_cache', '_current_frames', '_debugmallocstats', '_getframe',
 '_home', '_mercurial', '_xoptions', 'abiflags', 'api_version', 'argv',
 'base_exec_prefix', 'base_prefix', 'builtin_module_names', 'byteorder',
 'call_tracing', 'callstats', 'copyright', 'displayhook',
 'dont_write_bytecode', 'exc_info', 'excepthook', 'exec_prefix',
 'executable', 'exit', 'flags', 'float_info', 'float_repr_style',
 'getcheckinterval', 'getdefaultencoding', 'getdlopenflags',
 'getfilesystemencoding', 'getobjects', 'getprofile', 'getrecursionlimit',
 'getrefcount', 'getsizeof', 'getswitchinterval', 'gettotalrefcount',
 'gettrace', 'hash_info', 'hexversion', 'implementation', 'int_info',
 'intern', 'maxsize', 'maxunicode', 'meta_path', 'modules', 'path',
 'path_hooks', 'path_importer_cache', 'platform', 'prefix', 'ps1',
 'setcheckinterval', 'setdlopenflags', 'setprofile', 'setrecursionlimit',
 'setswitchinterval', 'settrace', 'stderr', 'stdin', 'stdout',
 'thread_info', 'version', 'version_info', 'warnoptions']
```

每个模块有各自独立的符号表，在模块内部为所有的函数当作全局符号表来使用。

被导入的模块的名称将被放入当前操作的模块的`符号表`中。

```python
#如果没有给定参数，那么 dir() 函数会罗列出当前定义的所有名称:
>>> a = [1, 2, 3, 4, 5]
>>> import fibo
>>> fib = fibo.fib
>>> dir() # 得到一个当前模块中定义的属性列表
['__builtins__', '__name__', 'a', 'fib', 'fibo', 'sys']
>>> a = 5 # 建立一个新的变量 'a'
>>> dir()
['__builtins__', '__doc__', '__name__', 'a', 'sys']
>>>
>>> del a # 删除变量名a
>>>
>>> dir()
['__builtins__', '__doc__', '__name__', 'sys']
>>>
```



### 模块发布、安装、使用

#### 模块发布

1. mymodule目录结构体如下：

```python
.
├── setup.py
├── suba
│   ├── aa.py
│   ├── bb.py
│   └── __init__.py
└── subb
    ├── cc.py
    ├── dd.py
    └── __init__.py
```

2. 编辑setup.py文件

`py_modules`需指明所需包含的py文件

```python
from distutils.core import setup

setup(name="ixfosa", version="1.0", description="ixfosa's module", author="ixfosa", py_modules=['suba.aa', 'suba.bb', 'subb.cc', 'subb.dd'])
```

3. 构建模块

`python setup.py build`

构建后目录结构

```python
.
├── build
│   └── lib.linux-i686-2.7
│       ├── suba
│       │   ├── aa.py
│       │   ├── bb.py
│       │   └── __init__.py
│       └── subb
│           ├── cc.py
│           ├── dd.py
│           └── __init__.py
├── setup.py
├── suba
│   ├── aa.py
│   ├── bb.py
│   └── __init__.py
└── subb
    ├── cc.py
    ├── dd.py
    └── __init__.py
```

4. 生成发布压缩包

`python setup.py sdist`

打包后,生成最终发布压缩包`ixfosa-1.0.tar.gz` , 目录结构

```python
.
├── build
│   └── lib.linux-i686-2.7
│       ├── suba
│       │   ├── aa.py
│       │   ├── bb.py
│       │   └── __init__.py
│       └── subb
│           ├── cc.py
│           ├── dd.py
│           └── __init__.py
├── dist
│   └── ixfosa-1.0.tar.gz
├── MANIFEST
├── setup.py
├── suba
│   ├── aa.py
│   ├── bb.py
│   └── __init__.py
└── subb
    ├── cc.py
    ├── dd.py
    └── __init__.py
```

#### 模块安装

1. 找到模块的压缩包
2. 解压
3. 进入文件夹
4. 执行命令`python setup.py install`

注意：

- 如果在install的时候，执行目录安装，可以使用`python setup.py install --prefix=安装路径`



#### 模块使用

在程序中，使用`from import` 即可完成对安装的模块使用

```python
from 模块名 import 模块名或者*
```

### 包

包是一种管理 Python `模块命名空间`的形式，采用"`点模块名称`"。

比如一个模块的名称是 `A.B`， 那么他表示`一个包 A中的子模块 B` 。

这里给出了一种可能的包结构（在分层的文件系统中）:

```python
sound/                          顶层包
      __init__.py               初始化 sound 包
      formats/                  文件格式转换子包
              __init__.py
              wavread.py
              wavwrite.py
              aiffread.py
              aiffwrite.py
              auread.py
              auwrite.py
              ...
      effects/                  声音效果子包
              __init__.py
              echo.py
              surround.py
              reverse.py
              ...
      filters/                  filters 子包
              __init__.py
              equalizer.py
              vocoder.py
              karaoke.py
              ...
```

在导入一个包的时候，Python 会根据 sys.path 中的目录来寻找这个包中包含的子目录。

目录只有包含一个叫做 `__init__.py` 的文件才会被认作是一个包，主要是为了避免一些滥俗的名字（比如叫做 string）不小心的影响搜索路径中的有效模块。

最简单的情况，放一个空的 :file:__init__.py就可以了。当然这个文件中也可以包含一些初始化代码或者为（ `__all__`变量赋值。

用户可以每次只导入一个包里面的特定模块，比如:

```python
import sound.effects.echo
```

这将会导入子模块:sound.effects.echo。 必须使用全名去访问:

```python
sound.effects.echo.echofilter(input, output, delay=0.7, atten=4)
```

还有一种导入子模块的方法是:

```python
from sound.effects import echo
```

这同样会导入子模块: echo，并且他不需要那些冗长的前缀，所以他可以这样使用:

```python
echo.echofilter(input, output, delay=0.7, atten=4)
```

还有一种变化就是直接导入一个函数或者变量:

```python
from sound.effects.echo import echofilter
```

同样的，这种方法会导入子模块: echo，并且可以直接使用他的 echofilter() 函数:

```python
echofilter(input, output, delay=0.7, atten=4)
```

注意当使用 `from package import item` 这种形式的时候，对应的 item 既可以是包里面的子模块（子包），或者包里面定义的其他名称，比如函数，类或者变量。

`import `语法会首先把` item` 当作一个包定义的名称，如果没找到，再试图按照一个模块去导入。如果还没找到，抛出一个` :exc:ImportError` 异常。

反之，如果使用形如` import item.subitem.subsubitem` 这种导入形式，除了最后一项，都必须是包，而最后一项则可以是模块或者是包，但是不可以是类，函数或者变量的名字。



**从一个包中导入**

设想一下，如果我们使用 from sound.effects import *会发生什么？

Python 会进入文件系统，找到这个包里面所有的子模块，一个一个的把它们都导入进来。

但是很不幸，这个方法在 Windows平台上工作的就不是非常好，因为Windows是一个大小写不区分的系统。



导入语句遵循如下规则：如果包定义文件 `__init__.py `存在一个叫做` __all__ `的列表变量，那么在使用 `from package import *` 的时候就把这个列表中的所有名字作为包内容导入。



作为包的作者，可别忘了在更新包之后保证 `__all__ `也更新了啊。你说我就不这么做，我就不使用导入`*`这种用法，好吧，没问题，谁让你是老板呢。这里有一个例子，在:file:sounds/effects/`__init__.py`中包含如下代码:

```python
__all__ = ["echo", "surround", "reverse"]
```

这表示当你使用`from sound.effects import *`这种用法时，你只会导入包里面这三个子模块。

如果 `__all__` 真的没有定义，那么使用**from sound.effects import \***这种语法的时候，就不会导入包 `sound.effects` 里的任何子模块。他只是把包sound.effects和它里面定义的所有内容导入进来（可能运行`__init__.py`里定义的初始化代码）。

这会把 `__init__.py `里面定义的所有名字导入进来。并且他不会破坏掉我们在这句话之前导入的所有明确指定的模块。看下这部分代码:

```python
import sound.effects.echo
import sound.effects.surround
from sound.effects import *
```

这个例子中，在执行 `from...import` 前，包 sound.effects 中的 echo 和 surround 模块都被导入到当前的命名空间中了。（当然如果定义了 `__all__ `就更没问题了）

通常我们并不主张使用` * `这种方法来导入模块，因为这种方法经常会导致代码的可读性降低。不过这样倒的确是可以省去不少敲键的功夫，而且一些模块都设计成了只能通过特定的方法导入。

记住，使用` **from Package import specific_submodule** `这种方法永远不会有错。事实上，这也是推荐的方法。除非是你要导入的子模块有可能和其他包的子模块重名。

如果在结构中包是一个子包（比如这个例子中对于包sound来说），而你又想导入兄弟包（同级别的包）你就得使用导入`绝对的路径`来导入。比如，如果模块`sound.filters.vocoder` 要使用包 `sound.effects` 中的模块 `echo`，你就要写成 `from sound.effects import echo`。

```python
from . import echo
from .. import formats
from ..filters import equalizer
```

无论是隐式的还是显式的相对导入都是从当前模块开始的。主模块的名字永远是"`__main__`"，一个Python应用程序的主模块，应当总是使用`绝对路径`引用。

包还提供一个额外的属性`__path__`。这是一个目录列表，里面每一个包含的目录都有为这个包服务的`__init__.py`，你得在其他`__init__.py`被执行前定义。可以修改这个变量，用来影响包含在包里面的模块和子包。

一般用来扩展包里面的模块。

## 命名空间和作用域

### 命名空间

`命名空间`(Namespace)是从`名称到对象的映射`，大部分的命名空间都是通过 Python `字典`来实现的。

命名空间提供了在项目中`避免名字冲突`的一种方法。各个命名空间是独立的，没有任何关系的，所以一个命名空间中不能有重名，但不同的命名空间是可以重名而没有任何影响。

一般有三种命名空间：

- `内置名称`（built-in names）， Python `语言内置的名称`，比如函数名 abs、char 和异常名称 BaseException、Exception 等等。
- `全局名称`（global names），`模块中定义的名称`，记录了模块的变量，包括函数、类、其它导入的模块、模块级的变量和常量。
- `局部名称`（local names），`函数中定义的名称`，记录了函数的变量，包括函数的参数和局部定义的变量。（类中定义的也是）



命名空间查找顺序:
假设我们要使用变量 runoob，则 Python 的查找顺序为：`局部的命名空间` -> `全局命名空间` -> `内置命名空间`。

如果找不到变量 runoob，它将放弃查找并引发一个 `NameError` 异常:

```python
NameError: name 'runoob' is not defined。
```

命名空间的`生命周期`：
命名空间的生命周期取决于`对象的作用域`，如果对象执行完成，则该命名空间的生命周期就结束。

因此，我们无法从外部命名空间访问内部命名空间的对象。

```python
# var1 是全局名称
var1 = 5
def some_func():
 
    # var2 是局部名称
    var2 = 6
    def some_inner_func():
 
        # var3 是内嵌的局部名称
        var3 = 7
```

### 作用域

`作用域`就是一个 Python 程序可以`直接访问命名空间的正文区域`。

在一个 python 程序中，直接访问一个变量，会从内到外依次访问所有的作用域直到找到，否则会报未定义的错误。

Python 中，程序的变量并不是在哪个位置都可以访问的，访问权限决定于这个变量是在哪里赋值的。

变量的作用域决定了在哪一部分程序可以访问哪个特定的变量名称。Python的作用域一共有4种，分别是：

有四种作用域：

- `L（Local)`：最内层，包含`局部变量`，比如一个函数/方法内部。
- **`E（Enclosing）`：包含了非局部(non-local)也非全局(non-global)的变量。比如两个嵌套函数，一个函数（或类） A 里面又包含了一个函数 B ，那么对于 B 中的名称来说 A 中的作用域就为 nonlocal。
- **`G（Global）`**：当前脚本的最外层，比如当前模块的`全局变量`。
- **`B（Built-in）`**： 包含了内建的变量/关键字等。，最后被搜索

规则顺序： `L –> E –> G –> B`。

在局部找不到，便会去局部外的局部找（例如闭包），再找不到就会去全局找，再者去内置中找。

```python
g_count = 0  # 全局作用域
def outer():
    o_count = 1  # 闭包函数外的函数中
    def inner():
        i_count = 2  # 局部作用域
```

`内置作用域`是通过一个名为 `builtin` 的标准模块来实现的，但是这个变量名自身并没有放入内置作用域内，所以必须导入这个文件才能够使用它。在Python3.0中，可以使用以下的代码来查看到底预定义了哪些变量:

```python
>>> import builtins
>>> dir(builtins)
```

Python 中只有`模块`（module），`类`（class）以及`函数`（def、lambda）才会引入新的作用域，其它的代码块（如 if/elif/else/、try/except、for/while等）是不会引入新的作用域的，也就是说这些语句内定义的变量，外部也可以访问，如下代码：

```python
>>> if True:
...  msg = 'I am from Runoob'
... 
>>> msg
'I am from Runoob'
>>> 


#实例中 msg 变量定义在 if 语句块中，但外部还是可以访问的。
#如果将 msg 定义在函数中，则它就是局部变量，外部不能访问：
>>> def test():
...     msg_inner = 'I am from Runoob'
... 
>>> msg_inner
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
NameError: name 'msg_inner' is not defined
>>> 
#从报错的信息上看，说明了 msg_inner 未定义，无法使用，因为它是局部变量，只有在函数内可以使用。
```

#### 全局变量和局部变量

定义在`函数内部`的变量拥有一个局部作用域，定义在`函数外`的拥有全局作用域。

局部变量只能在其被声明的函数内部访问，而全局变量可以在整个程序范围内访问。调用函数时，所有在函数内声明的变量名称都将被加入到作用域中。如下实例：

```python
total = 0 # 这是一个全局变量

def sum( arg1, arg2 ):
    #返回2个参数的和."
    total = arg1 + arg2 # total在这里是局部变量.
    print ("函数内是局部变量 : ", total)
    return total
 
#调用sum函数
sum( 10, 20 ) #函数内是局部变量 :  30
print ("函数外是全局变量 : ", total) #函数外是全局变量 :  0
```



```python
var_global='global_var'#这个var_global就是全局作用域

def globalFunc():
  var_local='local_var' #这个就是局部变量

class demo():
  class_demo_local_var='class member' #这里也是局部变量
  def localFunc(self):
    var_locals='local_func_var'#这里也是局部变量

    
#变量查找顺序为：当前域 -> 外部域(如果有) -> 全局域 -> 内置域。    
global_var='this  var  on  global space' 
'''
申明global_var这个位置就是全局域，也就是教程中所说的全局作用域，
同时它也是直接声明在文件中的，而不是声明在函数中或者类中的变量
'''
class demo():
  class_demo_local_var='class member' 
  '''
  虽然class_demo_local_var在这里是局部变量，这个局部变量的域相对于var_locals是外部域，
  所以可以直接被var_locals所在的更小的局部域访问
  '''
  def localFunc(self):
    var_locals='local_func_var'
    '''
    这里也是局部变量，但是相对于class_demo_local_var变量，却是更小的域，
    因此class_demo_local_var所在的那个域无法访问到当前域来
    '''
    print(self.class_demo_local_var)#到这里会查找当前域中有没有class_demo_local_var这个变量，然后再到相对于当前域的外部域去查找变量
```



#### global 和 nonlocal关键字

当内部作用域想修改外部作用域的变量时，就要用到`global`和`nonlocal`关键字了。

```python
#以下实例修改全局变量 num：
num = 1
def fun1():
    global num  # 需要使用 global 关键字声明
    print(num) 
    num = 123
    print(num)
fun1()
print(num)

'''
1
123
123
'''
```

如果要修改`嵌套作用域`（`enclosing` 作用域，外层非全局作用域）中的变量则需要 nonlocal 关键字了，如下实例：

```python
def outer():
    num = 10
    def inner():
        nonlocal num   # nonlocal关键字声明
        num = 100
        print(num)
    inner()
    print(num)
outer()

'''
100
100
'''

#另外有一种特殊情况，假设下面这段代码被运行：
a = 10
def test():
    a = a + 1
    print(a)
test()

#以上程序执行，报错信息如下：
Traceback (most recent call last):
  File "test.py", line 7, in <module>
    test()
  File "test.py", line 5, in test
    a = a + 1
UnboundLocalError: local variable 'a' referenced before assignment
  

#错误信息为局部作用域引用错误，因为 test 函数中的 a 使用的是局部，未定义，无法修改。
#修改 a 为全局变量，通过函数参数传递，可以正常执行输出结果为：
a = 10
def test(a):
    a = a + 1
    print(a)
test(a)  #11
```



## 面向对象

### 面向对象技术简介

- **类(Class):** 用来描述具有相同的属性和方法的对象的集合。它定义了该集合中每个对象所共有的属性和方法。对象是类的实例。
- **方法：**类中定义的函数。
- **类变量：**类变量在整个实例化的对象中是公用的。类变量定义在类中且在函数体之外。类变量通常不作为实例变量使用。
- **数据成员：**类变量或者实例变量用于处理类及其实例对象的相关的数据。
- **方法重写：**如果从父类继承的方法不能满足子类的需求，可以对其进行改写，这个过程叫方法的覆盖（override），也称为方法的重写。
- **局部变量：**定义在方法中的变量，只作用于当前实例的类。
- **实例变量：**在类的声明中，属性是用变量来表示的，这种变量就称为实例变量，实例变量就是一个用 self 修饰的变量。
- **继承：**即一个派生类（derived class）继承基类（base class）的字段和方法。继承也允许把一个派生类的对象作为一个基类对象对待。例如，有这样一个设计：一个Dog类型的对象派生自Animal类，这是模拟"是一个（is-a）"关系（例图，Dog是一个Animal）。
- **实例化：**创建一个类的实例，类的具体对象。
- **对象：**通过类定义的数据结构实例。对象包括两个数据成员（类变量和实例变量）和方法。

和其它编程语言相比，Python 在尽可能不增加新的语法和语义的情况下加入了类机制。

Python中的类提供了面向对象编程的所有基本功能：类的继承机制允许多个基类，派生类可以覆盖基类中的任何方法，方法中可以调用基类中的同名方法。

对象可以包含任意数量和类型的数据。

### 类定义

在Python中可以使用`class`关键字定义类

类实例化后，可以使用其属性，实际上，创建一个类之后，可以通过`类名`访问其属性。

语法格式如下：

```python
class ClassName:
    <statement-1>
    .
    .
    <statement-N>
```

​	

```python
class Student(object):

    # __init__是一个特殊方法用于在创建对象时进行初始化操作
    # 通过这个方法我们可以为学生对象绑定name和age两个属性
    def __init__(self, name, age):
        self.name = name
        self.age = age

    def study(self, course_name):
        print('%s正在学习%s.' % (self.name, course_name))

    # PEP 8要求标识符的名字用全小写多个单词用下划线连接
    # 但是部分程序员和公司更倾向于使用驼峰命名法(驼峰标识)
    def watch_movie(self):
        if self.age < 18:
            print('%s只能观看《熊出没》.' % self.name)
        else:
            print('%s正在观看岛国爱情大电影.' % self.name)
            

#创建和使用对象
def main():
    # 创建学生对象并指定姓名和年龄
    stu1 = Student('ixfosa', 22)
    
    # 给对象发study消息
    stu1.study('Python程序设计')
    
    # 给对象发watch_av消息
    stu1.watch_movie()
    stu2 = Student('王大锤', 15)
    stu2.study('思想品德')
    stu2.watch_movie()

if __name__ == '__main__':
    main()            
```

> **说明：** 写在类中的函数，我们通常称之为（对象的）方法，这些方法就是对象可以接收的消息。



### 类对象

类对象支持两种操作：属性引用和实例化。

属性引用使用和 Python 中所有的属性引用一样的标准语法：**`obj.name`**。

类对象创建后，类命名空间中所有的命名都是有效属性名。所以如果类定义是这样:

```python
class MyClass:
    """一个简单的类实例"""
    i = 12345
    def f(self):
        return 'hello world'
 
# 实例化类
x = MyClass()
 
# 访问类的属性和方法
print("MyClass 类的属性 i 为：", x.i) #MyClass 类的属性 i 为： 12345
print("MyClass 类的方法 f 输出为：", x.f()) #MyClass 类的方法 f 输出为： hello world

#以上创建了一个新的类实例并将该对象赋给局部变量 x，x 为空的对象。
```

#### \__init__() 构造方法

类有一个名为` __init__() `的特殊方法（**`构造方法`**），该方法在类实例化时会自动调用，像下面这样：

```python
class MyClass:
    """一个简单的类实例"""
    i = 12345
    def __init__(self):
    	self.data = []
    
    def f(self):
        return 'hello world'


#类定义了 __init__() 方法，类的实例化操作会自动调用 __init__() 方法。如下实例化类 MyClass，对应的 __init__() 方法就会被调用:
x = MyClass()
```

`__init__() `方法可以有参数，参数通过 __init__() 传递到类的实例化操作上。

```python
class Complex:
    def __init__(self, realpart, imagpart):
        self.r = realpart
        self.i = imagpart
x = Complex(3.0, -4.5)
print(x.r, x.i)   # 输出结果：3.0 -4.5
```

最新的 Python3.7 中(2018.07.13)，对类的构造函数进行了精简。

注意： 实际上，对于类 A， 实例化时不需要参数；而对于类 B，实例化时需要输入 (x, y) 参数，这才是两者的核心区别。定义类时，若需要输入参数，则一般必须使用 __init__()方法；若不需要输入参数，是否使用 __init__() 方法都可以。

```python
from dataclasses import dataclass

@dataclass
class A:
  x:int
  y:int
  def add(self):
    return self.x + self.y

#相当于以前的：
class A:
  def __init__(self,x,y):
    self.x = x
    self.y = y
  def add(self):
    return self.x + self.y
```



#### \__str__ ()打印类对象

`__str__` 是一个类的方法，在打印类对象，获取其属性信息时调用。打印一个实例化对象时，默认打印的其实时一个对象的地址，但是我们可以对其进行重载，打印我们想要的信息。



```python
class people:
    def __init__(self,name,age):
        self.name=name
        self.age=age

    def __str__(self):
        return '这个人的名字是%s,已经有%d岁了！'%(self.name,self.age)

a=people('孙悟空',999)
print(a)

'''
这个人的名字是孙悟空,已经有999岁了！
如果没有重载函数的话输出的就是一串看不懂的字符串：
<__main__.people object at 0x00000272A730D278>
'''
```

- 在python中方法名如果是`__xxxx__()`的，那么就有特殊的功能，因此叫做`“魔法”方法`
- 当使用print输出对象的时候，只要自己定义了`__str__(self)`方法，那么就会打印从在这个方法中return的数据



#### \__slots__()

Python是一门`动态语言`。通常，动态语言允许我们**在程序运行时给对象绑定新的属性或方法**，当然也可以对已经绑定的属性和方法进行解绑定。但是如果我们需要限定自定义类型的对象只能绑定某些属性，可以通过在类中定义`__slots__`变量来进行限定。需要注意的是`__slots__`的限定只对当前类的对象生效，对子类并不起任何作用。

```python
class Person(object):

    # 限定Person对象只能绑定_name, _age和_gender属性
    __slots__ = ('_name', '_age', '_gender')

    def __init__(self, name, age):
        self._name = name
        self._age = age

    @property
    def name(self):
        return self._name

    @property
    def age(self):
        return self._age

    @age.setter
    def age(self, age):
        self._age = age

    def play(self):
        if self._age <= 16:
            print('%s正在玩飞行棋.' % self._name)
        else:
            print('%s正在玩斗地主.' % self._name)


def main():
    person = Person('王大锤', 22)
    person.play()
    person._gender = '男'
    # AttributeError: 'Person' object has no attribute '_is_gay'
    # person._is_gay = True
```



#### self代表类的实例，而非类

`self`代表类的`实例`，而非类

类的方法与普通的函数只有一个特别的区别——它们必须有一个额外的**第一个参数名称**, 按照惯例它的名称是 self。

```python
class Test:
    def prt(self):
        print(self)
        print(self.__class__)
 
t = Test()
t.prt()  
'''
<__main__.Test instance at 0x100771878>
__main__.Test
'''
```

self 代表的是类的实例，代表当前对象的地址，而 `self.class` 则指向类。

`self 不是 python 关键字`，我们把他换成` ixfosa`也是可以正常执行的:

```python
class Test:
    def prt(ixfosa):
        print(ixfosa)
        print(ixfosa.__class__)
 
t = Test()
t.prt()

'''
<__main__.Test instance at 0x100771878>
__main__.Test
'''
```

在类的方法中直接修改 self 是无效操作，即使 self 变量的地址与实例地址相同：

```python
class C:
  def __init__(self, a):
    self.a = a
  def construct(self, a):
    c = C(a)
    self = c
  def getid(self):
    return id(self)

if __name__ == '__main__':
  c1 = C(2)
  c1.construct(3) # c1.a == 2
  print(id(c1) == c1.getid()) # True
```



### 访问可见性

在Python中，属性和方法的访问权限只有两种，也就是`公开`的和`私有`的，如果希望属性是私有的，在给属性命名时可以用`两个下划线作为开头`

```python
class Test:

    def __init__(self, foo):
        self.__foo = foo

    def __bar(self):
        print(self.__foo)
        print('__bar')


def main():
    test = Test('hello')
    # AttributeError: 'Test' object has no attribute '__bar'
    test.__bar()
    # AttributeError: 'Test' object has no attribute '__foo'
    print(test.__foo)


if __name__ == "__main__":
    main()
```

但是，Python并没有从语法上严格保证私有属性或方法的私密性，它只是给私有的属性和方法换了一个名字来妨碍对它们的访问，事实上如果你知道更换名字的规则仍然可以访问到它们，下面的代码就可以验证这一点。之所以这样设定，可以用这样一句名言加以解释，就是"**We are all consenting adults here**"。因为绝大多数程序员都认为开放比封闭要好，而且程序员要自己为自己的行为负责。

```python
class Test:

    def __init__(self, foo):
        self.__foo = foo

    def __bar(self):
        print(self.__foo)
        print('__bar')


def main():
    test = Test('hello')
    dir(test)
    test._Test__bar() #重命名之后的名字
    print(test._Test__foo)


if __name__ == "__main__":
    main()
```

在实际开发中，我们并不建议将属性设置为私有的，因为这会导致子类无法访问。所以大多数Python程序员会遵循一种命名惯例就是让属性名以单下划线开头来表示属性是受保护的，本类之外的代码在访问这样的属性时应该要保持慎重。这种做法并不是语法上的规则，单下划线开头的属性和方法外界仍然是可以访问的，所以更多的时候它是一种暗示或隐喻

### @property装饰器

之前我们讨论过Python中属性和方法访问权限的问题，虽然我们不建议将属性设置为私有的，但是如果直接将属性暴露给外界也是有问题的，比如我们没有办法检查赋给属性的值是否有效。我们之前的建议是将属性命名以单下划线开头，通过这种方式来暗示属性是受保护的，不建议外界直接访问，那么如果想访问属性可以通过属性的`getter`（访问器）和`setter`（修改器）方法进行对应的操作。如果要做到这点，就可以考虑使用`@property`包装器来包装`getter`和`setter`方法，使得对属性的访问既安全又方便，代码如下所示。

```python
class Person(object):

    def __init__(self, name, age):
        self._name = name
        self._age = age

    # 访问器 - getter方法
    @property
    def name(self):
        return self._name

    # 访问器 - getter方法
    @property
    def age(self):
        return self._age

    # 修改器 - setter方法
    @age.setter
    def age(self, age):
        self._age = age

    def play(self):
        if self._age <= 16:
            print('%s正在玩飞行棋.' % self._name)
        else:
            print('%s正在玩斗地主.' % self._name)


def main():
    person = Person('王大锤', 12)
    person.play()
    person.age = 22
    person.play()
    # person.name = '白元芳'  # AttributeError: can't set attribute


if __name__ == '__main__':
    main()
```



### 类的方法

```python
class Classname:
    @staticmethod
    def fun():
        print('静态方法')

    @classmethod
    def a(cls):
        print('类方法')

    # 普通方法
    def b(self):
        print('普通方法')



Classname.fun()
Classname.a()

C = Classname()
C.fun()
C.a()
C.b()
```



#### 普通方法

在类的内部，使用 `def`关键字来定义一个方法，与一般函数定义不同，类方法必须包含参数 `self`, 且为`第一个参数`，self 代表的是`类的实例`。

**`普通方法`**: 默认有个self参数，且只能被对象调用。也可以叫实例方法

```python
#类定义
class People:
    #定义基本属性
    name = ''
    age = 0
    #定义私有属性,私有属性在类外部无法直接进行访问
    __weight = 0
    #定义构造方法
    def __init__(self,n,a,w):
        self.name = n
        self.age = a
        self.__weight = w
    def speak(self):
        print("%s 说: 我 %d 岁。" %(self.name,self.age))
 
# 实例化类
p = People('runoob',10,30)
p.speak() #runoob 说: 我 10 岁。
```

#### 静态方法

**`静态方法`**: 用 `@staticmethod` 装饰的`不带 self` 参数的方法叫做静态方法，类的静态方法可以没有参数，可以直接使用`类名调用`。

之前，我们在类中定义的方法都是对象方法，也就是说这些方法都是发送给对象的消息。实际上，我们写在类中的方法并不需要都是对象方法，例如我们定义一个“三角形”类，通过传入三条边长来构造三角形，并提供计算周长和面积的方法，但是传入的三条边长未必能构造出三角形对象，因此我们可以先写一个方法来验证三条边长是否可以构成三角形，这个方法很显然就不是对象方法，因为在调用这个方法时三角形对象尚未创建出来（因为都不知道三条边能不能构成三角形），所以这个方法是属于三角形类而并不属于三角形对象的。我们可以使用静态方法来解决这类问题，代码如下所示。

```python
from math import sqrt


class Triangle(object):

    def __init__(self, a, b, c):
        self._a = a
        self._b = b
        self._c = c

    @staticmethod
    def is_valid(a, b, c):
        return a + b > c and b + c > a and a + c > b

    def perimeter(self):
        return self._a + self._b + self._c

    def area(self):
        half = self.perimeter() / 2
        return sqrt(half * (half - self._a) *
                    (half - self._b) * (half - self._c))


def main():
    a, b, c = 3, 4, 5
    # 静态方法和类方法都是通过给类发消息来调用的
    if Triangle.is_valid(a, b, c):
        t = Triangle(a, b, c)
        print(t.perimeter())
        # 也可以通过给类发消息来调用对象方法但是要传入接收消息的对象作为参数
        # print(Triangle.perimeter(t))
        print(t.area())
        # print(Triangle.area(t))
    else:
        print('无法构成三角形.')


if __name__ == '__main__':
    main()
```

#### 类方法

**`类方法`**: 默认有个 cls 参数，可以被`类`和`对象`调用，需要加上 `@classmethod` 装饰器。

和静态方法比较类似，Python还可以在类中定义类方法，类方法的第一个参数约定名为cls，它代表的是当前类相关的信息的对象（类本身也是一个对象，有的地方也称之为类的元数据对象），通过这个参数我们可以获取和类相关的信息并且可以创建出类的对象，代码如下所示。

```python
from time import time, localtime, sleep


class Clock(object):
    """数字时钟"""

    def __init__(self, hour=0, minute=0, second=0):
        self._hour = hour
        self._minute = minute
        self._second = second

    @classmethod
    def now(cls):
        ctime = localtime(time())
        return cls(ctime.tm_hour, ctime.tm_min, ctime.tm_sec)

    def run(self):
        """走字"""
        self._second += 1
        if self._second == 60:
            self._second = 0
            self._minute += 1
            if self._minute == 60:
                self._minute = 0
                self._hour += 1
                if self._hour == 24:
                    self._hour = 0

    def show(self):
        """显示时间"""
        return '%02d:%02d:%02d' % \
               (self._hour, self._minute, self._second)


def main():
    # 通过类方法创建对象并获取系统时间
    clock = Clock.now()
    while True:
        print(clock.show())
        sleep(1)
        clock.run()


if __name__ == '__main__':
    main()
```



#### 区别

实例方法、类方法、静态方法。三者区别看代码如下：

```python
class Test(object):
    
    def InstanceFun(self):
        print("InstanceFun");
        print(self);
        
    @classmethod
    def ClassFun(cls):
        print("ClassFun");
        print(cls);
        
    @staticmethod
    def StaticFun():
        print("StaticFun");

t = Test();　

t.InstanceFun();　　　# 输出InstanceFun，打印对象内存地址“<__main__.Test object at 0x0293DCF0>”
Test.InstanceFun();     # 错误，TypeError: unbound method instanceFun() must be called with Test instance as first argument
Test.InstanceFun(t);    # 输出InstanceFun，打印对象内存地址“<__main__.Test object at 0x0293DCF0>”

Test.ClassFun();     # 输出ClassFun，打印类位置 <class '__main__.Test'>
t.ClassFun();        # 输出ClassFun，打印类位置 <class '__main__.Test'>
t.ClassFun(Test);       # 错误   classFun() takes exactly 1 argument (2 given) 

Test.StaticFun();    # 输出StaticFun
t.StaticFun();       # 输出StaticFun
  
```

可以看到，在 Python 中，两种方法的主要区别在于参数。实例方法隐含的参数为`类实例self`，而类方法隐含的参数为类本身 `cls`。

静态方法`无隐含参数`，主要为了类实例也可以直接调用静态方法。

所以逻辑上类方法应当只被类调用，实例方法实例调用，静态方法两者都能调用。主要区别在于参数传递上的区别，实例方法悄悄传递的是self引用作为参数，而类方法悄悄传递的是 cls 引用作为参数。



### 类的专有方法：

- **\__init__ :** 构造函数，在生成对象时调用
- **\__del__ :** 析构函数，释放对象时使用
- **\__repr__ :** 打印，转换
- **\__setitem__ :** 按照索引赋值
- **\__getitem__:** 按照索引获取值
- **\__len__:** 获得长度
- **\__cmp__:** 比较运算
- **\__call__:** 函数调用
- **\__add__:** 加运算
- **\__sub__:** 减运算
- **\__mul__:** 乘运算
- **\__truediv__:** 除运算
- **\__mod__:** 求余运算
- **\__pow__:** 乘方



### 类之间的关系

简单的说，类和类之间的关系有三种：`is-a`、`has-a`和`use-a`关系。

- is-a关系也叫`继承`或`泛化`，比如学生和人的关系、手机和电子产品的关系都属于继承关系。
- has-a关系通常称之为`关联`，比如部门和员工的关系，汽车和引擎的关系都属于关联关系；关联关系如果是整体和部分的关联，那么我们称之为聚合关系；如果整体进一步负责了部分的生命周期（整体和部分是不可分割的，同时同在也同时消亡），那么这种就是最强的关联关系，我们称之为`合成关系`。
- use-a关系通常称之为`依赖`，比如司机有一个驾驶的行为（方法），其中（的参数）使用到了汽车，那么司机和汽车的关系就是依赖关系。



### 继承和多态

#### 继承

Python 同样支持类的继承，如果一种语言不支持继承，类就没有什么意义。派生类的定义如下所示:

```python
class DerivedClassName(BaseClassName1):
    <statement-1>
    .
    .
    .
    <statement-N>
```

`BaseClassName`（示例中的基类名）必须与派生类定义在一个作用域内。除了类，还可以用表达式，基类定义在另一个模块中时这一点非常有用:

```python
class DerivedClassName(modname.BaseClassName):
```

```python
#类定义
class people:
    #定义基本属性
    name = ''
    age = 0
    #定义私有属性,私有属性在类外部无法直接进行访问
    __weight = 0
    #定义构造方法
    def __init__(self,n,a,w):
        self.name = n
        self.age = a
        self.__weight = w
    def speak(self):
        print("%s 说: 我 %d 岁。" %(self.name,self.age))
 
#单继承示例
class student(people):
    grade = ''
    def __init__(self,n,a,w,g):
        #调用父类的构函
        people.__init__(self,n,a,w)
        self.grade = g
    #覆写父类的方法
    def speak(self):
        print("%s 说: 我 %d 岁了，我在读 %d 年级"%(self.name,self.age,self.grade))
 
 
s = student('ken',10,60,3)
s.speak() #ken 说: 我 10 岁了，我在读 3 年级
```

#### 多继承

Python同样有限的支持多继承形式。多继承的类定义形如下例:

```python
class DerivedClassName(Base1, Base2, Base3):
    <statement-1>
    .
    .
    .
    <statement-N>
```

需要注意圆括号中父类的顺序，若是父类中有`相同的方法名`，而在子类使用时未指定，python`从左至右`搜索 即方法在子类中未找到时，从左到右查找父类中是否包含方法。

```python
#类定义
class people:
    #定义基本属性
    name = ''
    age = 0
    #定义私有属性,私有属性在类外部无法直接进行访问
    __weight = 0
    #定义构造方法
    def __init__(self,n,a,w):
        self.name = n
        self.age = a
        self.__weight = w
    def speak(self):
        print("%s 说: 我 %d 岁。" %(self.name,self.age))
 
#单继承示例
class student(people):
    grade = ''
    def __init__(self,n,a,w,g):
        #调用父类的构函
        people.__init__(self,n,a,w)
        self.grade = g
    #覆写父类的方法
    def speak(self):
        print("%s 说: 我 %d 岁了，我在读 %d 年级"%(self.name,self.age,self.grade))
 
#另一个类，多重继承之前的准备
class speaker():
    topic = ''
    name = ''
    def __init__(self,n,t):
        self.name = n
        self.topic = t
    def speak(self):
        print("我叫 %s，我是一个演说家，我演讲的主题是 %s"%(self.name,self.topic))
 
#多重继承
class sample(speaker,student):
    a =''
    def __init__(self,n,a,w,g,t):
        student.__init__(self,n,a,w,g)
        speaker.__init__(self,n,t)
 
test = sample("Tim",25,80,4,"Python")
test.speak()   #方法名同，默认调用的是在括号中排前地父类的方法
#我叫 Tim，我是一个演说家，我演讲的主题是 Python
```

#### 子类继承父类构造函数

情况一：**子类需要自动调用父类的方法：**子类`不重写__init__()`方法，实例化子类后，会自动调用父类的__init__()的方法。

情况二：**子类不需要自动调用父类的方法：**子类`重写__init__()`方法，实例化子类后，将不会自动调用父类的`__init__()`的方法。

情况三：**子类重写__init__()方法又需要调用父类的方法：**使用`super`关键词：



如果在子类中需要父类的构造方法就需要`显式地调用`父类的构造方法，或者`不重写`父类的构造方法。

子类不重写 **`__init__`**，实例化子类时，会自动调用父类定义的 **`__init__`**。

```python
class Father(object):
    def __init__(self, name):
        self.name=name
        print ( "name: %s" %( self.name) )
    def getName(self):
        return 'Father ' + self.name
 
class Son(Father):
    def getName(self):
        return 'Son '+self.name
 
if __name__=='__main__':
    son=Son('runoob') #name: runoob
    print ( son.getName() ) #Son runoob
```

如果重写了**`__init__`** 时，实例化子类，就不会调用父类已经定义的 **`__init__`**，语法格式如下：

```python
class Father(object):
    def __init__(self, name):
        self.name=name
        print ( "name: %s" %( self.name) )
    def getName(self):
        return 'Father ' + self.name
 
class Son(Father):
    def __init__(self, name):
        print ( "hi" )
        self.name =  name
    def getName(self):
        return 'Son '+self.name
 
if __name__=='__main__':
    son=Son('runoob') #hi
    print ( son.getName() ) #Son runoob
```

如果重写了**`__init__`** 时，要继承父类的构造方法，可以使用 **`super`** 关键字：

```python
super(子类，self).__init__(参数1，参数2，....)
```

还有一种经典写法：

```python
父类名称.__init__(self,参数1，参数2，...)
```

```python
class Father(object):
    def __init__(self, name):
        self.name=name
        print ( "name: %s" %( self.name))
    def getName(self):
        return 'Father ' + self.name
 
class Son(Father):
    def __init__(self, name):
        super(Son, self).__init__(name)
        print ("hi")
        self.name =  name
    def getName(self):
        return 'Son '+self.name
 
if __name__=='__main__':
    son=Son('runoob')
    print ( son.getName() )
    
'''
name: runoob
hi
Son runoob    
'''
```

#### 多态

可以在已有类的基础上创建新类，这其中的一种做法就是让一个类从另一个类那里将属性和方法直接继承下来，从而减少重复代码的编写。提供继承信息的我们称之为父类，也叫超类或基类；得到继承信息的我们称之为子类，也叫派生类或衍生类。子类除了继承父类提供的属性和方法，还可以定义自己特有的属性和方法，所以子类比父类拥有的更多的能力，在实际开发中，我们经常会用子类对象去替换掉一个父类对象，这是面向对象编程中一个常见的行为，对应的原则称之为`里氏替换原则`

```python
class Person(object):
    """人"""

    def __init__(self, name, age):
        self._name = name
        self._age = age

    @property
    def name(self):
        return self._name

    @property
    def age(self):
        return self._age

    @age.setter
    def age(self, age):
        self._age = age

    def play(self):
        print('%s正在愉快的玩耍.' % self._name)

    def watch_av(self):
        if self._age >= 18:
            print('%s正在观看爱情动作片.' % self._name)
        else:
            print('%s只能观看《熊出没》.' % self._name)


class Student(Person):
    """学生"""

    def __init__(self, name, age, grade):
        super().__init__(name, age)
        self._grade = grade

    @property
    def grade(self):
        return self._grade

    @grade.setter
    def grade(self, grade):
        self._grade = grade

    def study(self, course):
        print('%s的%s正在学习%s.' % (self._grade, self._name, course))


class Teacher(Person):
    """老师"""

    def __init__(self, name, age, title):
        super().__init__(name, age)
        self._title = title

    @property
    def title(self):
        return self._title

    @title.setter
    def title(self, title):
        self._title = title

    def teach(self, course):
        print('%s%s正在讲%s.' % (self._name, self._title, course))


def main():
    stu = Student('王大锤', 15, '初三')
    stu.study('数学')
    stu.watch_av()
    t = Teacher('骆昊', 38, '砖家')
    t.teach('Python程序设计')
    t.watch_av()


if __name__ == '__main__':
    main()
```

子类在继承了父类的方法后，可以对父类已有的方法给出新的实现版本，这个动作称之为`方法重写`（`override`）。**通过方法重写我们可以让父类的同一个行为在子类中拥有不同的实现版本，当我们调用这个经过子类重写的方法时，不同的子类对象会表现出不同的行为**，这个就是`多态`（poly-morphism）。

```python
from abc import ABCMeta, abstractmethod


class Pet(object, metaclass=ABCMeta):
    """宠物"""

    def __init__(self, nickname):
        self._nickname = nickname

    @abstractmethod
    def make_voice(self):
        """发出声音"""
        pass


class Dog(Pet):
    """狗"""

    def make_voice(self):
        print('%s: 汪汪汪...' % self._nickname)


class Cat(Pet):
    """猫"""

    def make_voice(self):
        print('%s: 喵...喵...' % self._nickname)


def main():
    pets = [Dog('旺财'), Cat('凯蒂'), Dog('大黄')]
    for pet in pets:
        pet.make_voice()


if __name__ == '__main__':
    main()
```

在上面的代码中，我们将`Pet`类处理成了一个抽象类，所谓`抽象类`就是`不能够创建对象的类`，这种类的存在就是专门为了让其他类去继承它。Python从语法层面并没有像Java或C#那样提供对抽象类的支持，但是我们可以通过`abc`模块的`ABCMeta`元类和`abstractmethod`包装器来达到抽象类的效果，如果一个类中存在抽象方法那么这个类就不能够实例化（创建对象）。上面的代码中，`Dog`和`Cat`两个子类分别对`Pet`类中的`make_voice`抽象方法进行了重写并给出了不同的实现版本，当我们在`main`函数中调用该方法时，这个方法就表现出了多态行为（同样的方法做了不同的事情）。

### 方法重写

如果你的父类方法的功能不能满足你的需求，你可以在子类重写你父类的方法，实例如下：

```python
class Parent:        # 定义父类
   def myMethod(self):
      print ('调用父类方法')
 

class Child(Parent): # 定义子类
   def myMethod(self):
      print ('调用子类方法')
 
c = Child()          # 子类实例
c.myMethod()         # 子类调用重写方法 调用子类方法
super(Child,c).myMethod() #用子类对象调用父类已被覆盖的方法 调用父类方法
```

`super() 函数`是用于调用父类(超类)的一个方法。

### 练习

#### 定义一个类描述数字时钟。

参考答案：

```python
from time import sleep


class Clock(object):
    """数字时钟"""

    def __init__(self, hour=0, minute=0, second=0):
        """初始化方法

        :param hour: 时
        :param minute: 分
        :param second: 秒
        """
        self._hour = hour
        self._minute = minute
        self._second = second

    def run(self):
        """走字"""
        self._second += 1
        if self._second == 60:
            self._second = 0
            self._minute += 1
            if self._minute == 60:
                self._minute = 0
                self._hour += 1
                if self._hour == 24:
                    self._hour = 0

    def show(self):
        """显示时间"""
        return '%02d:%02d:%02d' % \
               (self._hour, self._minute, self._second)


def main():
    clock = Clock(23, 59, 58)
    while True:
        print(clock.show())
        sleep(1)
        clock.run()


if __name__ == '__main__':
    main()
```

#### 定义一个类描述平面上的点并提供移动点和计算到另一个点距离的方法。

```python
from math import sqrt


class Point(object):

    def __init__(self, x=0, y=0):
        """初始化方法
        
        :param x: 横坐标
        :param y: 纵坐标
        """
        self.x = x
        self.y = y

    def move_to(self, x, y):
        """移动到指定位置
        
        :param x: 新的横坐标
        "param y: 新的纵坐标
        """
        self.x = x
        self.y = y

    def move_by(self, dx, dy):
        """移动指定的增量
        
        :param dx: 横坐标的增量
        "param dy: 纵坐标的增量
        """
        self.x += dx
        self.y += dy

    def distance_to(self, other):
        """计算与另一个点的距离
        
        :param other: 另一个点
        """
        dx = self.x - other.x
        dy = self.y - other.y
        return sqrt(dx ** 2 + dy ** 2)

    def __str__(self):
        return '(%s, %s)' % (str(self.x), str(self.y))


def main():
    p1 = Point(3, 5)
    p2 = Point()
    print(p1)
    print(p2)
    p2.move_by(-1, 2)
    print(p2)
    print(p1.distance_to(p2))


if __name__ == '__main__':
    main()
```

#### 奥特曼打小怪兽。

```python
from abc import ABCMeta, abstractmethod
from random import randint, randrange


class Fighter(object, metaclass=ABCMeta):
    """战斗者"""

    # 通过__slots__魔法限定对象可以绑定的成员变量
    __slots__ = ('_name', '_hp')

    def __init__(self, name, hp):
        """初始化方法

        :param name: 名字
        :param hp: 生命值
        """
        self._name = name
        self._hp = hp

    @property
    def name(self):
        return self._name

    @property
    def hp(self):
        return self._hp

    @hp.setter
    def hp(self, hp):
        self._hp = hp if hp >= 0 else 0

    @property
    def alive(self):
        return self._hp > 0

    @abstractmethod
    def attack(self, other):
        """攻击

        :param other: 被攻击的对象
        """
        pass


class Ultraman(Fighter):
    """奥特曼"""

    __slots__ = ('_name', '_hp', '_mp')

    def __init__(self, name, hp, mp):
        """初始化方法

        :param name: 名字
        :param hp: 生命值
        :param mp: 魔法值
        """
        super().__init__(name, hp)
        self._mp = mp

    def attack(self, other):
        other.hp -= randint(15, 25)

    def huge_attack(self, other):
        """究极必杀技(打掉对方至少50点或四分之三的血)

        :param other: 被攻击的对象

        :return: 使用成功返回True否则返回False
        """
        if self._mp >= 50:
            self._mp -= 50
            injury = other.hp * 3 // 4
            injury = injury if injury >= 50 else 50
            other.hp -= injury
            return True
        else:
            self.attack(other)
            return False

    def magic_attack(self, others):
        """魔法攻击

        :param others: 被攻击的群体

        :return: 使用魔法成功返回True否则返回False
        """
        if self._mp >= 20:
            self._mp -= 20
            for temp in others:
                if temp.alive:
                    temp.hp -= randint(10, 15)
            return True
        else:
            return False

    def resume(self):
        """恢复魔法值"""
        incr_point = randint(1, 10)
        self._mp += incr_point
        return incr_point

    def __str__(self):
        return '~~~%s奥特曼~~~\n' % self._name + \
            '生命值: %d\n' % self._hp + \
            '魔法值: %d\n' % self._mp


class Monster(Fighter):
    """小怪兽"""

    __slots__ = ('_name', '_hp')

    def attack(self, other):
        other.hp -= randint(10, 20)

    def __str__(self):
        return '~~~%s小怪兽~~~\n' % self._name + \
            '生命值: %d\n' % self._hp


def is_any_alive(monsters):
    """判断有没有小怪兽是活着的"""
    for monster in monsters:
        if monster.alive > 0:
            return True
    return False


def select_alive_one(monsters):
    """选中一只活着的小怪兽"""
    monsters_len = len(monsters)
    while True:
        index = randrange(monsters_len)
        monster = monsters[index]
        if monster.alive > 0:
            return monster


def display_info(ultraman, monsters):
    """显示奥特曼和小怪兽的信息"""
    print(ultraman)
    for monster in monsters:
        print(monster, end='')


def main():
    u = Ultraman('骆昊', 1000, 120)
    m1 = Monster('狄仁杰', 250)
    m2 = Monster('白元芳', 500)
    m3 = Monster('王大锤', 750)
    ms = [m1, m2, m3]
    fight_round = 1
    while u.alive and is_any_alive(ms):
        print('========第%02d回合========' % fight_round)
        m = select_alive_one(ms)  # 选中一只小怪兽
        skill = randint(1, 10)   # 通过随机数选择使用哪种技能
        if skill <= 6:  # 60%的概率使用普通攻击
            print('%s使用普通攻击打了%s.' % (u.name, m.name))
            u.attack(m)
            print('%s的魔法值恢复了%d点.' % (u.name, u.resume()))
        elif skill <= 9:  # 30%的概率使用魔法攻击(可能因魔法值不足而失败)
            if u.magic_attack(ms):
                print('%s使用了魔法攻击.' % u.name)
            else:
                print('%s使用魔法失败.' % u.name)
        else:  # 10%的概率使用究极必杀技(如果魔法值不足则使用普通攻击)
            if u.huge_attack(m):
                print('%s使用究极必杀技虐了%s.' % (u.name, m.name))
            else:
                print('%s使用普通攻击打了%s.' % (u.name, m.name))
                print('%s的魔法值恢复了%d点.' % (u.name, u.resume()))
        if m.alive > 0:  # 如果选中的小怪兽没有死就回击奥特曼
            print('%s回击了%s.' % (m.name, u.name))
            m.attack(u)
        display_info(u, ms)  # 每个回合结束后显示奥特曼和小怪兽的信息
        fight_round += 1
    print('\n========战斗结束!========\n')
    if u.alive > 0:
        print('%s奥特曼胜利!' % u.name)
    else:
        print('小怪兽胜利!')


if __name__ == '__main__':
    main()
```

#### 扑克游戏。

```python
import random


class Card(object):
    """一张牌"""

    def __init__(self, suite, face):
        self._suite = suite
        self._face = face

    @property
    def face(self):
        return self._face

    @property
    def suite(self):
        return self._suite

    def __str__(self):
        if self._face == 1:
            face_str = 'A'
        elif self._face == 11:
            face_str = 'J'
        elif self._face == 12:
            face_str = 'Q'
        elif self._face == 13:
            face_str = 'K'
        else:
            face_str = str(self._face)
        return '%s%s' % (self._suite, face_str)
    
    def __repr__(self):
        return self.__str__()


class Poker(object):
    """一副牌"""

    def __init__(self):
        self._cards = [Card(suite, face) 
                       for suite in '♠♥♣♦'
                       for face in range(1, 14)]
        self._current = 0

    @property
    def cards(self):
        return self._cards

    def shuffle(self):
        """洗牌(随机乱序)"""
        self._current = 0
        random.shuffle(self._cards)

    @property
    def next(self):
        """发牌"""
        card = self._cards[self._current]
        self._current += 1
        return card

    @property
    def has_next(self):
        """还有没有牌"""
        return self._current < len(self._cards)


class Player(object):
    """玩家"""

    def __init__(self, name):
        self._name = name
        self._cards_on_hand = []

    @property
    def name(self):
        return self._name

    @property
    def cards_on_hand(self):
        return self._cards_on_hand

    def get(self, card):
        """摸牌"""
        self._cards_on_hand.append(card)

    def arrange(self, card_key):
        """玩家整理手上的牌"""
        self._cards_on_hand.sort(key=card_key)


# 排序规则-先根据花色再根据点数排序
def get_key(card):
    return (card.suite, card.face)


def main():
    p = Poker()
    p.shuffle()
    players = [Player('东邪'), Player('西毒'), Player('南帝'), Player('北丐')]
    for _ in range(13):
        for player in players:
            player.get(p.next)
    for player in players:
        print(player.name + ':', end=' ')
        player.arrange(get_key)
        print(player.cards_on_hand)


if __name__ == '__main__':
    main()
```

> **说明：** 大家可以自己尝试在上面代码的基础上写一个简单的扑克游戏，例如21点(Black Jack)，游戏的规则可以自己在网上找一找。

#### 工资结算系统。

```python
"""
某公司有三种类型的员工 分别是部门经理、程序员和销售员
需要设计一个工资结算系统 根据提供的员工信息来计算月薪
部门经理的月薪是每月固定15000元
程序员的月薪按本月工作时间计算 每小时150元
销售员的月薪是1200元的底薪加上销售额5%的提成
"""
from abc import ABCMeta, abstractmethod


class Employee(object, metaclass=ABCMeta):
    """员工"""

    def __init__(self, name):
        """
        初始化方法

        :param name: 姓名
        """
        self._name = name

    @property
    def name(self):
        return self._name

    @abstractmethod
    def get_salary(self):
        """
        获得月薪

        :return: 月薪
        """
        pass


class Manager(Employee):
    """部门经理"""

    def get_salary(self):
        return 15000.0


class Programmer(Employee):
    """程序员"""

    def __init__(self, name, working_hour=0):
        super().__init__(name)
        self._working_hour = working_hour

    @property
    def working_hour(self):
        return self._working_hour

    @working_hour.setter
    def working_hour(self, working_hour):
        self._working_hour = working_hour if working_hour > 0 else 0

    def get_salary(self):
        return 150.0 * self._working_hour


class Salesman(Employee):
    """销售员"""

    def __init__(self, name, sales=0):
        super().__init__(name)
        self._sales = sales

    @property
    def sales(self):
        return self._sales

    @sales.setter
    def sales(self, sales):
        self._sales = sales if sales > 0 else 0

    def get_salary(self):
        return 1200.0 + self._sales * 0.05


def main():
    emps = [
        Manager('刘备'), Programmer('诸葛亮'),
        Manager('曹操'), Salesman('荀彧'),
        Salesman('吕布'), Programmer('张辽'),
        Programmer('赵云')
    ]
    for emp in emps:
        if isinstance(emp, Programmer):
            emp.working_hour = int(input('请输入%s本月工作时间: ' % emp.name))
        elif isinstance(emp, Salesman):
            emp.sales = float(input('请输入%s本月销售额: ' % emp.name))
        # 同样是接收get_salary这个消息但是不同的员工表现出了不同的行为(多态)
        print('%s本月工资为: ￥%s元' %
              (emp.name, emp.get_salary()))


if __name__ == '__main__':
    main()
```



## 错误和异常

Python有两种错误很容易辨认：`语法错误`和`异常`。

Python `assert`（断言）用于判断一个表达式，在表达式条件为false的时候触发异常。

### 断言

Python assert（断言）用于判断一个表达式，在表达式条件为 false 的时候触发异常。

断言可以在条件不满足程序运行的情况下直接返回错误，而不必等待程序运行后出现崩溃的情况，例如我们的代码只能在 Linux 系统下运行，可以先判断当前系统是否符合条件。

```python
#语法格式如下：
assert expression

等价于：
if not expression:
    raise AssertionError
```

```python
#assert 后面也可以紧跟参数:
assert expression [, arguments]

等价于：
if not expression:
    raise AssertionError(arguments)
```

```python
#以下为 assert 使用实例：
>>> assert True     # 条件为 true 正常执行
>>> assert False    # 条件为 false 触发异常
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
AssertionError
>>> assert 1==1    # 条件为 true 正常执行
>>> assert 1==2    # 条件为 false 触发异常
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
AssertionError

>>> assert 1==2, '1 不等于 2'
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
AssertionError: 1 不等于 2
>>>
以下实例判断当前系统是否为 Linux，如果不满足条件则直接触发异常，不必执行接下来的代码：

实例
import sys
assert ('linux' in sys.platform), "该代码只能在 Linux 下执行"
# 接下来要执行的代码
```



### 语法错误

Python的语法错误或称为解析错误，是初学者经常碰到的，如下实例

```python
>>> while True print('Hello world')
  File "<stdin>", line 1, in ?
    while True print('Hello world')
                   ^
SyntaxError: invalid syntax
    
#函数 print() 被检查到有错误，是它前面缺少了一个冒号 : 。
#语法分析器指出了出错的一行，并且在最先找到的错误的位置标记了一个小小的箭头。
```

### 异常

即便 Python 程序的语法是正确的，在运行它的时候，也有可能发生错误。运行期检测到的错误被称为异常。

大多数的异常都不会被程序处理，都以错误信息的形式展现在这里:

```python
>>> 10 * (1/0)             # 0 不能作为除数，触发异常
Traceback (most recent call last):
  File "<stdin>", line 1, in ?
ZeroDivisionError: division by zero
    
>>> 4 + spam*3             # spam 未定义，触发异常
Traceback (most recent call last):
  File "<stdin>", line 1, in ?
NameError: name 'spam' is not defined
    
>>> '2' + 2               # int 不能与 str 相加，触发异常
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
TypeError: can only concatenate str (not "int") to str
```

#### 异常处理

##### try/except

异常捕捉可以使用 **try/except** 语句。

以下例子中，让用户输入一个合法的整数，但是允许用户中断这个程序（使用 Control-C 或者操作系统提供的方法）。用户中断的信息会引发一个 KeyboardInterrupt 异常。

```python
while True:
    try:
        x = int(input("请输入一个数字: "))
        break
    except ValueError:
        print("您输入的不是数字，请再次尝试输入！")
```

`try` 语句按照如下方式工作；

- 首先，执行 try 子句（在关键字` try `和关键字 `except` 之间的语句）。
- 如果没有异常发生，忽略 except 子句，try 子句执行后结束。
- 如果在执行 try 子句的过程中发生了异常，那么 try 子句余下的部分将被忽略。如果异常的类型和 except 之后的名称相符，那么对应的 except 子句将被执行。
- 如果一个异常没有与任何的 except 匹配，那么这个异常将会传递给上层的 try 中。

一个 try 语句可能包含多个except子句，分别来处理不同的特定的异常。最多只有一个分支会被执行。

处理程序将只针对对应的 try 子句中的异常进行处理，而不是其他的 try 的处理程序中的异常。

一个except子句可以同时处理多个异常，这些异常将被放在一个括号里成为一个元组，例如:

```python
except (RuntimeError, TypeError, NameError):
    pass

#使用一个快捕捉多个异常：
def model_exception(x,y):
  try:
    b = name
    a =x/y
  except(ZeroDivisionError,NameError,TypeError):
    print('one of ZeroDivisionError or NameError or TypeError happend')

#调用函数结果
model_exception(2,0)
```

最后一个`except`子句可以忽略异常的名称，它将被当作通配符使用。你可以使用这种方法打印一个错误信息，然后再次把异常抛出。

```python
import sys

try:
    f = open('myfile.txt')
    s = f.readline()
    i = int(s.strip())
except OSError as err:
    print("OS error: {0}".format(err))
except ValueError:
    print("Could not convert data to an integer.")
except:
    print("Unexpected error:", sys.exc_info()[0])
    raise
```

##### try/except...else

`try/except` 语句还有一个可选的 `else`子句，如果使用这个子句，那么必须放在所有的 except 子句之后。

else 子句将在 try 子句没有发生任何异常的时候执行。

以下实例在 try 语句中判断文件是否可以打开，如果打开文件时正常的没有发生异常则执行 else 部分的语句，读取文件内容：

```python
for arg in sys.argv[1:]:
    try:
        f = open(arg, 'r')
    except IOError:
        print('cannot open', arg)
    else:
        print(arg, 'has', len(f.readlines()), 'lines')
        f.close()
```

使用 else 子句比把所有的语句都放在 try 子句里面要好，这样可以避免一些意想不到，而 except 又无法捕获的异常。

异常处理并不仅仅处理那些直接发生在 try 子句中的异常，而且还能处理子句中调用的函数（甚至间接调用的函数）里抛出的异常。例如:

```python
try:
    runoob()
except AssertionError as error:
    print(error)
else:
    try:
        with open('file.log') as file:
            read_data = file.read()
    except FileNotFoundError as fnf_error:
        print(fnf_error)
finally:
    print('这句话，无论异常是否发生都会执行。')
```

##### finally

```python
#try 语句还有另外一个可选的子句，它定义了无论在任何情况下都会执行的清理行为。 例如:
#不管 try 子句里面有没有发生异常，finally 子句都会执行。
>>> try:
...     raise KeyboardInterrupt
... finally:
...     print('Goodbye, world!')
...
Goodbye, world!
Traceback (most recent call last):
  File "<stdin>", line 2, in <module>
KeyboardInterrupt
```

如果一个异常在 try 子句里（或者在 except 和 else 子句里）被抛出，而又没有任何的 except 把它截住，那么这个异常会在 finally 子句执行后被抛出。

```python
#下面是一个更加复杂的例子（在同一个 try 语句里包含 except 和 finally 子句）:
>>> def divide(x, y):
        try:
            result = x / y
        except ZeroDivisionError:
            print("division by zero!")
        else:
            print("result is", result)
        finally:
            print("executing finally clause")
   
>>> divide(2, 1)
result is 2.0
executing finally clause

>>> divide(2, 0)
division by zero!
executing finally clause

>>> divide("2", "1")
executing finally clause
Traceback (most recent call last):
  File "<stdin>", line 1, in ?
  File "<stdin>", line 3, in divide
TypeError: unsupported operand type(s) for /: 'str' and 'str'
```

#### 预定义的清理行为

一些对象定义了标准的清理行为，无论系统是否成功的使用了它，一旦不需要它了，那么这个标准的清理行为就会执行。

```python
#这面这个例子展示了尝试打开一个文件，然后把内容打印到屏幕上:
#当执行完毕后，文件会保持打开状态，并没有被关闭。
for line in open("myfile.txt"):
    print(line, end="")

#关键词 with 语句就可以保证诸如文件之类的对象在使用完之后一定会正确的执行他的清理方法:
#代码执行完毕后，就算在处理过程中出问题了，文件 f 总是会关闭。
with open("myfile.txt") as f:
    for line in f:
        print(line, end="")

   

temp = os.open('test_text.txt', os.O_RDWR | os.O_CREAT)
temp_file = os.fdopen(temp, 'r')
print(str(temp_file.read()))
os.close(temp)

#就可以简化成：
with open('test_text.txt', 'r') as f:
    print(f.read())        
```



#### 抛出异常

Python 使用 raise 语句抛出一个指定的异常。

`raise` 语法格式如下：

```python
raise [Exception [, args [, traceback]]]
```

以下实例如果 x 大于 5 就触发异常:

```python
x = 10
if x > 5:
    raise Exception('x 不能大于 5。x 的值为: {}'.format(x))
    
#执行以上代码会触发异常：
Traceback (most recent call last):
  File "test.py", line 3, in <module>
    raise Exception('x 不能大于 5。x 的值为: {}'.format(x))
Exception: x 不能大于 5。x 的值为: 10
```

raise 唯一的一个参数指定了要被抛出的异常。它必须是一个异常的实例或者是异常的类（也就是 Exception 的子类）。

如果你只想知道这是否抛出了一个异常，并不想去处理它，那么一个简单的 raise 语句就可以再次把它抛出。

#### 自定义异常

你可以通过创建一个新的异常类来拥有自己的异常。异常类继承自`Exception` 类，可以直接继承，或者间接继承，例如:

```python
>>> class MyError(Exception):
        def __init__(self, value):
            self.value = value
        def __str__(self):
            return repr(self.value)
   
>>> try:
        raise MyError(2*2)
    except MyError as e:
        print('My exception occurred, value:', e.value)
   
My exception occurred, value: 4
>>> raise MyError('oops!')
Traceback (most recent call last):
  File "<stdin>", line 1, in ?
__main__.MyError: 'oops!'
```

在这个例子中，类 Exception 默认的 `__init__() `被覆盖。

当创建一个模块有可能抛出多种不同的异常时，一种通常的做法是为这个包建立一个基础异常类，然后基于这个基础类为不同的错误情况创建不同的子类:

大多数的异常的名字都以"`Error`"结尾，就跟标准的异常命名一样。

```python
class Error(Exception):
    """Base class for exceptions in this module."""
    pass

class InputError(Error):
    """Exception raised for errors in the input.

    Attributes:
        expression -- input expression in which the error occurred
        message -- explanation of the error
    """

    def __init__(self, expression, message):
        self.expression = expression
        self.message = message

class TransitionError(Error):
    """Raised when an operation attempts a state transition that's not
    allowed.

    Attributes:
        previous -- state at beginning of transition
        next -- attempted new state
        message -- explanation of why the specific transition is not allowed
    """

    def __init__(self, previous, next, message):
        self.previous = previous
        self.next = next
        self.message = message
```

### 内置异常类型的结构

```python
BaseException
 +-- SystemExit
 +-- KeyboardInterrupt
 +-- GeneratorExit
 +-- Exception
      +-- StopIteration
      +-- StopAsyncIteration
      +-- ArithmeticError
      |    +-- FloatingPointError
      |    +-- OverflowError
      |    +-- ZeroDivisionError
      +-- AssertionError
      +-- AttributeError
      +-- BufferError
      +-- EOFError
      +-- ImportError
      |    +-- ModuleNotFoundError
      +-- LookupError
      |    +-- IndexError
      |    +-- KeyError
      +-- MemoryError
      +-- NameError
      |    +-- UnboundLocalError
      +-- OSError
      |    +-- BlockingIOError
      |    +-- ChildProcessError
      |    +-- ConnectionError
      |    |    +-- BrokenPipeError
      |    |    +-- ConnectionAbortedError
      |    |    +-- ConnectionRefusedError
      |    |    +-- ConnectionResetError
      |    +-- FileExistsError
      |    +-- FileNotFoundError
      |    +-- InterruptedError
      |    +-- IsADirectoryError
      |    +-- NotADirectoryError
      |    +-- PermissionError
      |    +-- ProcessLookupError
      |    +-- TimeoutError
      +-- ReferenceError
      +-- RuntimeError
      |    +-- NotImplementedError
      |    +-- RecursionError
      +-- SyntaxError
      |    +-- IndentationError
      |         +-- TabError
      +-- SystemError
      +-- TypeError
      +-- ValueError
      |    +-- UnicodeError
      |         +-- UnicodeDecodeError
      |         +-- UnicodeEncodeError
      |         +-- UnicodeTranslateError
      +-- Warning
           +-- DeprecationWarning
           +-- PendingDeprecationWarning
           +-- RuntimeWarning
           +-- SyntaxWarning
           +-- UserWarning
           +-- FutureWarning
           +-- ImportWarning
           +-- UnicodeWarning
           +-- BytesWarning
           +-- ResourceWarning
```

