# Python编码规范


##  1 代码风格


###  1.1 分号

#### [强制] 不要在行尾加分号，也不要用分号将两条命令放在同一行。


### 1.2 行长度

#### [建议] 每行不超过80个字符。

#### 以下情况除外：
   * 长的导入模块语句
   * 注释里的URL

#### [建议] 不要使用反斜杠连接行。
解释：
Python会将与圆括号，中括号，花括号中的行隐式地连接起来，你可以在表达式外围增加一对额外的圆括号。

示例：
```
if (width == 0 and height ==0 and 
    color == 'red' and emphasis == 'strong'):
```

#### [建议] 如果一个文本字符串特别长，一行放不下的话，可以用圆括号来实现隐式连接。

示例：
```
x = ('这是一个非常长非常长非常长非常长 '
     '非常长非常长非常长非常长非常长非常长的字符串')
```

#### [建议] 在注释中，如果必要，将长的URL放在一行上。

示例：
```
good:  
    # See details at
    # http://www.example.com/us/developer/documentation/api/content/v2.0/csv_file_name_extension_full_specification.html
```
```
bad:
    # See details at
    # http://www.example.com/us/developer/documentation/api/content/\
    # v2.0/csv_file_name_extension_full_specification.html
```


### 1.3 括号

#### [强制] 宁缺毋滥地使用括号，除非是实现行连接，否则不要在返回语句或者条件语句中使用括号，不过在元组两边使用括号是可以的。

示例：
```
good：
       if foo:
               bar()
       if x and y:
           bar()
       for (x, y) in dict.items(): ...
```
```
bad:
     if (x):
         bar()
     return (x)
```

### 1.4 缩进

#### [强制] 用`4`个空格来缩进代码，绝对不要用`tab`，也不要`tab`和空格混用，对于行连接的情况，你应该要么垂直对齐换行的元素，或者使用`4`个空格的悬挂式缩进（这时第一行不应该有参数）。

示例：
```
good: 
       #  与起始变量对齐
       foo = long_function_name(var_one, var_two,
                                var_three, var_four)

       # 字典中与起始值对齐
       foo = {
           long_dictionary_key: value1 +
                                value2,
           ...
       }

       # 4 个空格缩进，第一行不需要
       foo = long_function_name(
           var_one, var_two, var_three,
           var_four)

       # 字典中 4 个空格缩进
       foo = {
           long_dictionary_key:
               long_dictionary_value,
           ...
       }
```      
```
bad： 
      # 第一行有变量，并且采用 4 个空格，这种是禁止的
     foo = long_function_name(var_one, var_two,
         var_three, var_four)
     # 2 个空格也是禁止的
     foo = long_function_name(
       var_one, var_two, var_three,
       var_four)
```


### 1.5 空行

#### [强制] 顶级定义之间空两行，比如函数或者类定义，方法定义。类之间的方法，函数之间都应该空一行。 

示例：
```
    class Outer(object):
        
        def function_one():
            pass
    
        def function_two():
            pass


    class Outer_two(object):
 
        def function_one():
            pass

        def function_two():
            pass
 


### 1.6 空格

#### [强制] 括号内不要有空格。

示例：
```
good：
    spam(ham[1], {eggs: 2}, [])
```
```
bad：
    spam( ham[ 1 ], { eggs: 2 }, [ ] )
```

#### [强制] 不要在逗号，分号，冒号前面加空格，但应该在他们后面加（处了在行尾）。

示例：
```
good：
    if x==4:
      print x, y
    x, y = y, x    # y, x交换值
```
```
bad：
    if x == 4 :
      print x , y
    x , y = y , x
```

#### [强制] 参数列表，索引或者切片的左括号前不应加空格。

示例：
```
good：
    spam[1] 
```
```
bad：
    spam [1]
```
```
good：
    dict['key'] = list[index]
```
```
bad：
    dict ['key'] = list [index]
```

#### [强制] 在二元操作符两边都应该加上一个空格，比如赋值`=`，比较`==`，`<`，`>`，`!=`，`<=`，`>=`，`in`，`not in`，`is`，`is not`等，布尔`and`，`or`，`not`等。算数操作符两边也应该加上一个空格，比如`+`，`-`等。

示例：
```
good：
    x == 1
    x += 1
    x = x + 1
```
```
bad：
    x==1
    x<1
```

#### [强制] 当`=`用于指示关键字或者默认参数时，不要在其两侧使用空格。

示例：
```
good：
    def complex(real, imag=0.0): return magic(r=real, i=imag)
```
```
bad:
    def complex(real, imag = 0.0): return magin(r = real, i  = imag)
```

#### [强制] 不要用空格来垂直对齐多行间的标记，因为这会成为维护的负担（适用于`：`，`#`，`=`等）。

示例：
```
good：
    foo = 1000 # 注释
    long_name = 2 #注释不需要对齐

    dictionary = {
        "foo": 1,
        "long_name": 2,
        }
```
```
bad：
    foo              = 1000   # 注释
    long_name = 2         # 注释不需要对齐
    dictionary = {
        "foo":       1,
        "long_name": 2,
        }
```

### 1.7 注释

#### [强制] 确保对模块，函数，方法和行内注释使用正确的风格。

示例：
```
类应该在其定义下有一个用于描述该类的文档字符串. 如果你的类有公共属性(Attributes), 那么文档中应该有一个属性(Attributes)段. 并且应该遵守和函数参数相同的格式.

class SampleClass(object):
    """Summary of class here.

    Longer class information....
    Longer class information....

    Attributes:
        likes_spam: A boolean indicating if we like SPAM or not.
        eggs: An integer count of the eggs we have laid.
    """

    def __init__(self, likes_spam=False):
        """Inits SampleClass with blah."""
        self.likes_spam = likes_spam
        self.eggs = 0

    def public_method(self):
        """Performs operation blah."""
```

#### [强制] `#`符号后加一个空格
#### 块注释和行注释
```
最需要写注释的是代码中那些技巧性的部分. 如果你在下次 代码审查 的时候必须解释一下, 那么你应该现在就给它写注释. 对于复杂的操作, 应该在其操作开始前写上若干行注释. 对于不是一目了然的代码, 应在其行尾添加注释.为了提高可读性, 注释应该至少离开代码2个空格.
# We use a weighted dictionary search to find out where i is in# the array. 
# We extrapolate position based on the largest num
# in the array and the array size and then do binary search to
# get the exact number.
if i & (i-1) == 0:  # true if i is a power of 2

另一方面, 绝不要描述代码. 假设阅读代码的人比你更懂Python, 他只是不知道你的代码要做什么.
# BAD COMMENT: Now go through the b array and make sure whenever i occurs
# the next element is i+1
```



## 2 通用

### 2.1 类

#### [强制] 如果一个类不继承自其他类，就显式的从object继承，嵌套类也一样。

示例：
```
good：
    class SampleClass(object):
        pass


    class OuterClass(object):
    
        class InnerClass(object):
            pass


    class ChildClass(ParentClass):
        """从父类继承"""
```
```
bad：
    class SampleClass:
        pass


    class OuterClass:

        class InnerClass:
            pass
```

解释：

继承自 object 是为了使属性(properties)正常工作, 并且这样可以保护你的代码, 使其不受Python 3000的一个特殊的潜在不兼容性影响. 这样做也定义了一些特殊的方法, 这些方法实现了对象的默认语义, 包括 \_\_new__, \_\_init__, \_\_delattr__, \_\_getattribute__, \_\_setattr__, \_\_hash__, \_\_repr__, and \_\_str__ .

### 2.2 字符串

#### [强制] 字符串使用规范如下

示例：
```
good：
    x = a + b
    x = '%s, %s!' % (a, b)
    x = '{}, {}!'.format(a, b)
    x = 'name: %s; score: %d' % (name, n)
    x = 'name: {}; score: {}'.format(name, n)
```
```
bad：
    x = '%s%s' % (a, b)  # use + in this case
    x = '{}{}'.format(a, b)  # use + in this case
    x = a + ', ' + b + '!'
    x = 'name: ' + name + '; score: ' + str(n) 
```
#### [强制] 避免在循环中用`+`和`+=`操作符来累加字符串。

解释：
由于字符串是不可变的,这样做会创建不必要的临时对象,并且导致二次方而不是线性的运行时间.作为替代方案,你可以将每个子串加入列表,然后在循环结束后用`.join`连接列表.

示例：
```
good：
    items = ['<table>']
     for last_name, first_name in employee_list:
         items.append('<tr><td>%s, %s</td></tr>' % (last_name, first_name))
     items.append('</table>')
     employee_table = ''.join(items)
```
```
bad：
    employee_table = '<table>'
    for last_name, first_name in employee_list:
        employee_table += '<tr><td>%s, %s</td></tr>' % (last_name, first_name)
    employee_table += '</table>'
```

#### [强制] 引用字符串优先使用单引号作为符号`'`，如果字符串内要使用单引号，才使用双引号`"`引用字符串。

示例：
```
    Python('Why are you hiding your eyes?')
    Gollum("I'm scared of lint errors.")
    Narrator('"Good!" thought a happy Python reviewer.')
```

#### [强制] 多行字符串使用三重双引号`"""`，而非三重单引号`'''`。多行字符串也要保证缩进规则。

示例：
```
good：
    print ("This is much nicer.\n"
           "Do it this way.\n")

    “”“This is a nice string"""
```
```
bad：
    print """This is pretty ugly.
  Don't do this.
  """
```

### 2.3 文件和sockets

#### [强制] 在文件和socket结束时，显式地关闭它。推荐使用`with`语句管理文件。

示例：
```
    with open('hello.txt') as hello_file:
        for line in hello_file:
            print(line)
```

### 2.3 导入格式

#### [强制] 每个导入应该独占一行。

示例：
```
good：
    import os
    import sys
```
```
bad：
    import os,sys
```
#### [强制] 导入总应该放在文件顶部，位于模块注释和文档字符串之后，模块全局变量和变量之前，导入应该按照从最通用到最不通用的顺序分组：
* 标准库导入.
* 第三方库导入.
* 应用程序指定导入.
#### 每种分组中，应该根据每个模块的完整包路径按字典序排序，忽略大小写。

示例：
```
    import foo
    from foo import bar
    from foo.bar import baz
    from foo.bar import Quux
    from Foob import ar
```

### 2.4 语句

#### [建议] 通常每个语句应该独占一行，不过，如果测试结果和测试语句在一行放得下，也可以将它们放在同一行。如果是`if`语句，只有在没有else时才能这样做，特别地，绝不要对try/except这样做，因为try和except不能放在同一行。

示例：
```
good：
    if foo: bar(foo)
```
```
bad：
    if foo: bar(foo)
    else:   bar(foo)

    try:               bar(foo)
    except ValueError: bar(foo)

    try:
        bar(foo)
    except ValueError: baz(foo)
```


## 3 命名

### [强制] 命名规则如下

示例：
```
module_name
package_name
ClassName
method_name
ExceptionName
function_name
GLOBAL_VAR_NAME
instance_var_name
function_parameter_name
local_var_name
```

#### [强制] 应该避免的名称

* 单字符名称，除了计数器和迭代器.
* 包/模块名中的连字符`-`.
* 双下划线开头并结尾的名称（Python保留，例如`__init__`）.

#### [建议] 命名约定
* 所谓"内部(Internal)"表示仅模块内可用, 或者, 在类内是保护或私有的.
* 用单下划线(_)开头表示模块变量或函数是protected的(使用import * from时不会包含).
* 用双下划线(__)开头的实例变量或方法表示类内私有.
* 将相关的类和顶级函数放在同一个模块里. 不像Java, 没必要限制一个类一个模块.
* 对类名使用大写字母开头的单词(如CapWords, 即Pascal风格), 但是模块名应该用小写加下划线的方式(如lower_with_under.py). 尽管已经有很多现存的模块使用类似于CapWords.py这样的命名, 但现在已经不鼓励这样做, 因为如果模块名碰巧和类名一致, 这会让人困扰.

#### [强制] 命名规范

| Type        | Public           | Internal  |
| ------------- |:-------------:| -----:|
|Modules| 	lower_with_under |	_lower_with_under|
|Packages| 	lower_with_under |	     |
|Classes |	CapWords 	|_CapWords  |
|Exceptions | 	CapWords | 	 
|Functions | 	lower_with_under() | _lower_with_under() |
|Global/Class Constants | CAPS_WITH_UNDER| 	_CAPS_WITH_UNDER|
|Global/Class Variables |	lower_with_under |	_lower_with_under|
|Instance Variables| lower_with_under| 	_lower_with_under (protected) or __lower_with_under(private)|
|Method Names|lower_with_under() |_lower_with_under()(protected) or __lower_with_under()(private) |
|Function/Method Parameters |	lower_with_under |  |	 
|Local Variables| 	lower_with_under | | 	 

  

