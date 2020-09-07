# Python_ALiyun【重要易混知识点汇总】
【一、变量、运算符与数据类型】
1.注释
在 Python 中，# 表示注释，作用于整行。
''' ''' 或者 """ """ 表示区间注释，在三引号之间的所有内容被注释。
2. 运算符
（1）算术运算符
print(3 / 4)  # 0.75
print(3 // 4)  # 0 整除（地板除）
print(3 % 4)  # 3取余
print(2 ** 3)  # 8 幂
（2）比较运算符【注意：==, != 对比的是两个变量的值】
print(3 == 4)  # False 等于
print(3 != 5)  # True 不等于
（3）逻辑运算符
print((3 > 2) and (3 < 5))  # True 与
print((1 > 3) or (9 < 2))  # False 或
print(not (2 > 1))  # False 非
（4）位运算符【】
print(bin(4))  # 0b100
print(bin(5))  # 0b101
print(bin(~4), ~4)  # -0b101 -5 按位取反
print(bin(4 & 5), 4 & 5)  # 0b100 4 按位与
print(bin(4 | 5), 4 | 5)  # 0b101 5 
print(bin(4 ^ 5), 4 ^ 5)  # 0b1 1 
print(bin(4 << 2), 4 << 2)  # 0b10000 16 左移
print(bin(4 >> 2), 4 >> 2)  # 0b1 1 右移
（5）三元运算符
有了这个三元操作符的条件表达式，你可以使用一条语句来完成以上的条件判断和赋值操作。
x, y = 4, 5
small = x if x < y else y
print(small)  # 4
（6）其他运算符 not is/is/in/not in【注意：is, is not 对比的是两个变量的内存地址】
letters = ['A', 'B', 'C']
if 'A' in letters:# A exists
    print('A' + ' exists')
if 'h' not in letters:# h not exists
    print('h' + ' not exists')
比较的两个变量均指向不可变类型/可变类型【常用】。
#不可变类型  #可变类型
a = "hello"   a = ["hello"]
b = "hello"   b = ["hello"]
print(a is b, a == b)  # True True
print(a is not b, a != b)  # False False
【注意：】
比较的两个变量，指向的都是地址不可变的类型（str等），那么is，is not 和 ==，！= 是完全等价的。
对比的两个变量，指向的是地址可变的类型（list，dict，tuple等），则is，is not 和 ==，！=两者是有区别的。
运算符的优先级
一元运算符优于二元运算符。例如3 ** -2等价于3 ** (-2)。
先算术运算，后移位运算，最后位运算。例如 1 << 3 + 2 & 7等价于 (1 << (3 + 2)) & 7。
逻辑运算最后结合。例如3 < 4 and 4 < 5等价于(3 < 4) and (4 < 5)。
print(-3 ** 2)  # -9
print(3 ** -2)  # 0.1111111111111111
print(1 << 3 + 2 & 7)  # 0
print(-3 * 2 + 5 / -2 - 4)  # -12.5
print(3 < 4 and 4 < 5)  # True
3. 变量和赋值
在使用变量之前，需要对其先赋值。变量名可以包括字母、数字、下划线、但变量名不能以数字开头。
Python 变量名是大小写敏感的，foo != Foo。
4. 数据类型与转换
int整型 <class 'int'>
float浮点型<class 'float'>3.149, 11.11
bool布尔型<class 'bool'>True, False【 布尔 (boolean) 型变量只能取两个值，True 和 False。当把布尔型变量用在数字运算中，用 1 和 0 代表 True 和 False。】
（1-2）整数型/浮点型
【例1】通过 print() 可看出 a 的值，以及类 (class) 是int。
a = 1031
print(a, type(a)) # 1031 <class 'int'>
a = 0.00000023
b = 2.3e-7
print(a)  # 2.3e-07
print(b)  # 2.3e-07
Python 里面万物皆对象（object），整型也不例外，只要是对象，就有相应的属性 （attributes） 和方法（methods）。
【例2】b = dir(int)【？？对它们有个大概印象就可以了，具体怎么用，需要哪些参数 （argument），还需要查文档。】
print(b)
【例3】找到一个整数的二进制表示，再返回其长度。
a = 1031
print(bin(a))  # 0b10000000111
print(a.bit_length())  # 11
【例4】getcontext() 显示了 Decimal 对象的默认精度值是 28 位 (prec=28)。
有时候我们想保留浮点型的小数点后 n 位。可以用 decimal 包里的 Decimal 对象和 getcontext() 方法来实现。
Python 里面有很多用途广泛的包 (package)，用什么你就引进 (import) 什么。包也是对象，也可以用上面提到的dir(decimal) 来看其属性和方法。
import decimal
from decimal import Decimal
a = decimal.getcontext()
print(a)
# Context(prec=28, rounding=ROUND_HALF_EVEN, Emin=-999999, Emax=999999,
# capitals=1, clamp=0, flags=[], 
# traps=[InvalidOperation, DivisionByZero, Overflow])
b = Decimal(1) / Decimal(3)
print(b)
# 0.3333333333333333333333333333【28位】
【例5】使 1/3 保留 4 位，用 getcontext().prec 来调整精度。
decimal.getcontext().prec = 4
c = Decimal(1) / Decimal(3)
print(c)
# 0.3333
（3）布尔型
print(True + True)  # 2
print(True + False)  # 1
print(True * False)  # 0
除了直接给变量赋值 True 和 False，还可以用 bool(X) 来创建变量，其中 X 可以是
基本类型：整型、浮点型、布尔型
容器类型：字符串、元组、列表、字典和集合
【例子】bool 作用在基本类型变量：X 只要不是整型 0、浮点型 0.0，bool(X) 就是 True，其余就是 False。
bool 作用在容器类型变量：X 只要不是空的变量，bool(X) 就是 True，其余就是 False。
确定bool(X) 的值是 True 还是 False，就看 X 是不是空，空的话就是 False，不空的话就是 True。
对于数值变量，0, 0.0 都可认为是空的。
对于容器变量，里面没元素就是空的。
获取类型信息 type(object)
注：
type() 不会认为子类是一种父类类型，不考虑继承关系。
isinstance() 会认为子类是一种父类类型，考虑继承关系。
【如果要判断两个类型是否相同推荐使用 isinstance()。】
print(type(0), bool(0), bool(1))
# <class 'int'> False True
print(type(10.31), bool(0.00), bool(10.31))
# <class 'float'> False True
print(type(True), bool(False), bool(True))
# <class 'bool'> False True
print(type(''), bool(''), bool('python'))
# <class 'str'> False True
print(type(()), bool(()), bool((10,)))
# <class 'tuple'> False True
print(type([]), bool([]), bool([1, 2]))
# <class 'list'> False True
print(type({}), bool({}), bool({'a': 1, 'b': 2}))
# <class 'dict'> False True
print(type(set()), bool(set()), bool({1, 2}))
# <class 'set'> False True
print(isinstance(1, int))  # True
print(isinstance(5.2, float))  # True
print(isinstance(True, bool))  # True
print(isinstance('5.2', str))  # True
（4）类型转换
转换为整型 int(x, base=10)
转换为字符串 str(object='')
转换为浮点型 float(x)
5. print() 函数【没有参数时，每次输出后都会换行。每次输出结束都用end设置的参数&结尾，并没有默认换行。】
print(*objects, sep=' ', end='\n', file=sys.stdout, flush=False)
将对象以字符串表示的方式格式化输出到流文件对象file里。其中所有非关键字参数都按str()方式进行转换为字符串输出；
关键字参数sep是实现分隔符，比如多个参数输出时想要输出中间的分隔字符；
关键字参数end是输出结束时的字符，默认是换行符\n；
关键字参数file是定义流输出的文件，可以是标准的系统输出sys.stdout，也可以重定义为别的文件；
关键字参数flush是立即把内容输出到流文件，不作缓存。
【例1】shoplist = ['apple', 'mango', 'carrot', 'banana']
print("This is printed with 'end='&''.")
for item in shoplist:
    print(item, end='&')
print('hello world')
# This is printed with 'end='&''.
# apple&mango&carrot&banana&hello world
【item值与'another string'两个值之间用sep设置的参数&分割。由于end参数没有设置，因此默认是输出解释后换行，即end参数的默认值为\n。】

【二、位运算】
1. 原码、反码和补码
二进制有三种不同的表示形式：原码、反码和补码，计算机内部使用补码来表示。
原码：就是其二进制表示（注意，有一位符号位）。
反码：正数的反码就是原码，负数的反码是符号位不变，其余位取反（对应正数按位取反）。
补码：正数的补码就是原码，负数的补码是反码+1。
符号位：最高位为符号位，0表示正数，1表示负数。在位运算中符号位也参与运算。
2. 按位运算
（1）按位非操作 ~
~ 1 = 0
~ 0 = 1
~ 把num的补码中的 0 和 1 全部取反（0 变为 1，1 变为 0）有符号整数的符号位在 ~ 运算中同样会取反。
00 00 01 01 -> 5
~
---
11 11 10 10 -> -6
（2）按位与操作 & 
1 & 1 = 1
1 & 0 = 0
0 & 1 = 0
0 & 0 = 0
只有两个对应位都为 1 时才为 1
（3）按位或操作 |
1 | 1 = 1
1 | 0 = 1
0 | 1 = 1
0 | 0 = 0
只要两个对应位中有一个 1 时就为 1
（4）按位异或操作 ^
1 ^ 1 = 0
1 ^ 0 = 1
0 ^ 1 = 1
0 ^ 0 = 0
只有两个对应位不同时才为 1
【异或操作的性质：满足交换律和结合律】
（5）按位左移操作 <<
num << i 将num的二进制表示向左移动i位所得的值。
00 00 10 11 -> 11
11 << 3
---
01 01 10 00 -> 88 
（6）按位右移操作 >>
num >> i 将num的二进制表示向右移动i位所得的值。
00 00 10 11 -> 11
11 >> 2
---
00 00 00 10 -> 2
按位左移操作 <<
num << i 将num的二进制表示向左移动i位所得的值。
00 00 10 11 -> 11
11 << 3
---
01 01 10 00 -> 88 
按位右移操作 >>
num >> i 将num的二进制表示向右移动i位所得的值。
00 00 10 11 -> 11
11 >> 2
---
00 00 00 10 -> 2
3. 利用位运算实现快速计算
通过 <<，>> 快速计算2的倍数问题。
n << 1 -> 计算 n*2
n >> 1 -> 计算 n/2，负奇数的运算不可用
n << m -> 计算 n*(2^m)，即乘以 2 的 m 次方
n >> m -> 计算 n/(2^m)，即除以 2 的 m 次方
1 << n -> 2^n
通过 ^ 快速交换两个整数。 通过 ^ 快速交换两个整数。
a ^= b
b ^= a
a ^= b
通过 a & (-a) 快速获取a的最后为 1 位置的整数。
4. 利用位运算实现整数集合
一个数的二进制表示可以看作是一个集合（0 表示不在集合中，1 表示在集合中）。
比如集合 {1, 3, 4, 8}，可以表示成 01 00 01 10 10 而对应的位运算也就可以看作是对集合进行的操作。
元素与集合的操作：
a | (1<<i)  -> 把 i 插入到集合中
a & ~(1<<i) -> 把 i 从集合中删除
a & (1<<i)  -> 判断 i 是否属于该集合（零不属于，非零属于）
集合之间的操作：
a 补   -> ~a
a 交 b -> a & b
a 并 b -> a | b
a 差 b -> a & (~b)
注意：整数在内存中是以补码的形式存在的，输出自然也是按照补码输出。
【例子】
print(bin(3))  # 0b11
print(bin(-3))  # -0b11
print(bin(-3 & 0xffffffff))  
# 0b11111111111111111111111111111101
print(bin(0xfffffffd))       
# 0b11111111111111111111111111111101
print(0xfffffffd)  # 4294967293
【注意】
Python中bin一个负数（十进制表示），输出的是它的原码的二进制表示加上个负号，巨坑。
Python中的整型是补码形式存储的。
Python中整型是不限制长度的不会超范围溢出。
所以为了获得负数（十进制表示）的补码，需要手动将其和十六进制数0xffffffff进行按位与操作，再交给bin()进行输出，得到的才是负数的补码表示。
【四、条件语句】
1. if 语句
if expression:
    expr_true_suite
if 语句的 expr_true_suite 代码块只有当条件表达式 expression 结果为真时才执行，否则将继续执行紧跟在该代码块后面的语句。
单个 if 语句中的 expression 条件表达式可以通过布尔操作符 and，or和not 实现多重条件判断。
if expression:
    expr_true_suite
else:
    expr_false_suite
Python 提供与 if 搭配使用的 else，如果 if 语句的条件表达式结果布尔值为假，那么程序将执行 else 语句后的代码。
【if语句支持嵌套，即在一个if语句中嵌入另一个if语句，从而构成不同层次的选择结构。Python 使用缩进而不是大括号来标记代码块边界，因此要特别注意else的悬挂问题。】
3. if - elif - else 语句
if expression1:
    expr1_true_suite
elif expression2:
    expr2_true_suite
    ……
elif expressionN:
    exprN_true_suite
else:
    expr_false_suite
elif 语句即为 else if，用来检查多个表达式是否为真，并在为真时执行特定代码块中的代码。
4. assert 关键词
assert这个关键词我们称之为“断言”，当这个关键词后边的条件为 False 时，程序自动崩溃并抛出AssertionError的异常。
【在进行单元测试时，可以用来在程序中置入检查点，只有条件为 True 才能让程序正常工作。】
my_list = ['lsgogroup']
my_list.pop(0)
assert len(my_list) > 0
# AssertionError
【五、循环语句】
1. while 循环
while语句最基本的形式包括一个位于顶部的布尔表达式，一个或多个属于while代码块的缩进语句。
while 布尔表达式:
    代码块
while循环的代码块会一直循环执行，直到布尔表达式的值为布尔假。
如果布尔表达式不带有<、>、==、！=、in、not in等运算符，仅仅给出数值之类的条件，也是可以的。当while后写入一个非零整数时，视为真值，执行循环体；写入0时，视为假值，不执行循环体。也可以写入str、list或任何序列，长度非零则视为真值，执行循环体；否则视为假值，不执行循环体。布尔表达式返回0，循环终止。
2. while - else 循环
while 布尔表达式:
    代码块
else:
    代码块
当while循环正常执行完的情况下，执行else输出，如果while循环中执行了跳出循环的语句，比如 break，将不执行else代码块的内容。 
count = 0
while count < 5:
    print("%d is  less than 5" % count)
    count = count + 1
else:
    print("%d is not less than 5" % count) 
# 0 is  less than 5
# 1 is  less than 5
# 2 is  less than 5
# 3 is  less than 5
# 4 is  less than 5
# 5 is not less than 5
count = 0
while count < 5:
    print("%d is  less than 5" % count)
    count = 6
    break
else:
    print("%d is not less than 5" % count)
# 0 is  less than 5
3. for 循环
for循环是迭代循环，在Python中相当于一个通用的序列迭代器，可以遍历任何有序序列，如str、list、tuple等，也可以遍历任何可迭代对象，如dict。
for 迭代变量 in 可迭代对象:
    代码块
每次循环，迭代变量被设置为可迭代对象的当前元素，提供给代码块使用。
【例1】member = ['张三', '李四', '刘德华', '刘六', '周润发']
for each in member:
    print(each)
或
for i in range(len(member)):
    print(member[i])
# 张三
# 李四
# 刘德华
# 刘六
# 周润发
【例2】dic = {'a': 1, 'b': 2, 'c': 3, 'd': 4}
for key, value in dic.items():
    print(key, value, sep=':', end=' ')  
# a:1 b:2 c:3 d:4 
【例3】dic = {'a': 1, 'b': 2, 'c': 3, 'd': 4}
for key in dic.keys():
    print(key, end=' ') 
# a b c d
4. for - else 循环
for 迭代变量 in 可迭代对象:
    代码块
else:
    代码块
当for循环正常执行完的情况下，执行else输出，如果for循环中执行了跳出循环的语句，比如 break，将不执行else代码块的内容，与while - else语句一样。
for num in range(10, 20):  # 迭代 10 到 20 之间的数字
    for i in range(2, num):  # 根据因子迭代
        if num % i == 0:  # 确定第一个因子
            j = num / i  # 计算第二个因子
            print('%d 等于 %d * %d' % (num, i, j))
            break  # 跳出当前循环
    else:  # 循环的 else 部分
        print(num, '是一个质数')
# 10 等于 2 * 5
# 11 是一个质数
# 12 等于 2 * 6
# 13 是一个质数
# 14 等于 2 * 7
# 15 等于 3 * 5
# 16 等于 2 * 8
# 17 是一个质数
# 18 等于 2 * 9
# 19 是一个质数
5. range() 函数
range([start,] stop[, step=1])
这个BIF（Built-in functions）有三个参数，其中用中括号括起来的两个表示这两个参数是可选的。
step=1 表示第三个参数的默认值是1。
range 这个BIF的作用是生成一个从start参数的值开始到stop参数的值结束的数字序列，该序列包含start的值但不包含stop的值。
for i in range(2, 9):  # 不包含9
    print(i)
# 2
# 3
# 4
# 5
# 6
# 7
# 8
6. enumerate()函数
enumerate(sequence, [start=0])
sequence：一个序列、迭代器或其他支持迭代对象。
start：下标起始位置。
返回 enumerate(枚举) 对象
【例1】seasons = ['Spring', 'Summer', 'Fall', 'Winter']
lst = list(enumerate(seasons))
print(lst)
# [(0, 'Spring'), (1, 'Summer'), (2, 'Fall'), (3, 'Winter')]
lst = list(enumerate(seasons, start=1))  # 下标从 1 开始
print(lst)
# [(1, 'Spring'), (2, 'Summer'), (3, 'Fall'), (4, 'Winter')]
enumerate()与 for 循环的结合使用。
for i, a in enumerate(A)
    do something with a  
用 enumerate(A) 不仅返回了 A 中的元素，还顺便给该元素一个索引值 (默认从 0 开始)。此外，用 enumerate(A, j) 还可以确定索引起始值为 j。
【例2】for i, language in enumerate(languages, 2):
    print(i, 'I love', language)
print('Done!')
# 2 I love Python
# 3 I love R
# 4 I love Matlab
# 5 I love C++
# Done!
7. break 语句
break语句可以跳出当前所在层的循环。
import random
secret = random.randint(1, 10) #[1,10]之间的随机数
省略
8. continue 语句
continue终止本轮循环并开始下一轮循环。
9. pass 语句
pass 语句的意思是“不做任何事”，如果你在需要有语句的地方不写任何语句，那么解释器会提示出错，而 pass 语句就是用来解决这些问题的。
pass是空语句，不做任何操作，只起到占位的作用，其作用是为了保持程序结构的完整性。尽管pass语句不做任何操作，
但如果暂时不确定要在一个位置放上什么样的代码，可以先放置一个pass语句，让代码可以正常运行。
def a_func():
    pass
10. 推导式
（1）列表推导式
[ expr for value in collection [if condition] ]
x = [-4, -2, 0, 2, 4]
y = [a * 2 for a in x]
print(y)
# [-8, -4, 0, 4, 8]
（2）元组推导式
( expr for value in collection [if condition] )
a = (x for x in range(10))
print(a)
# <generator object <genexpr> at 0x0000025BE511CC48>
print(tuple(a))
# (0, 1, 2, 3, 4, 5, 6, 7, 8, 9)
  （3）字典推导式
{ key_expr: value_expr for value in collection [if condition] }
  b = {i: i % 2 == 0 for i in range(10) if i % 3 == 0}
print(b)
# {0: True, 3: False, 6: True, 9: False}
  （4）集合推导式
{ expr for value in collection [if condition] }
  c = {i for i in [1, 2, 3, 4, 5, 5, 6, 4, 3, 2, 1]}
print(c)
# {1, 2, 3, 4, 5, 6}
  （5）其它
next(iterator[, default]) Return the next item from the iterator. If default is given and the iterator is exhausted, it is returned instead of raising StopIteration.
【六、异常处理】
异常就是运行期检测到的错误。计算机语言针对可能出现的错误定义了异常类型，某种错误引发对应的异常时，异常处理程序将被启动，从而恢复程序的正常运行。
1. Python 标准异常总结【异常体系内部有层次关系】
BaseException：所有异常的 基类
Exception：常规异常的 基类
StandardError：所有的内建标准异常的基类
ArithmeticError：所有数值计算异常的基类
FloatingPointError：浮点计算异常
OverflowError：数值运算超出最大限制
ZeroDivisionError：除数为零
AssertionError：断言语句（assert）失败
AttributeError：尝试访问未知的对象属性
EOFError：没有内建输入，到达EOF标记
EnvironmentError：操作系统异常的基类
IOError：输入/输出操作失败
OSError：操作系统产生的异常（例如打开一个不存在的文件）
WindowsError：系统调用失败
ImportError：导入模块失败的时候
KeyboardInterrupt：用户中断执行
LookupError：无效数据查询的基类
IndexError：索引超出序列的范围
KeyError：字典中查找一个不存在的关键字
MemoryError：内存溢出（可通过删除对象释放内存）
NameError：尝试访问一个不存在的变量
UnboundLocalError：访问未初始化的本地变量
ReferenceError：弱引用试图访问已经垃圾回收了的对象
RuntimeError：一般的运行时异常
NotImplementedError：尚未实现的方法
SyntaxError：语法错误导致的异常
IndentationError：缩进错误导致的异常
TabError：Tab和空格混用
SystemError：一般的解释器系统异常
TypeError：不同类型间的无效操作
ValueError：传入无效的参数
UnicodeError：Unicode相关的异常
UnicodeDecodeError：Unicode解码时的异常
UnicodeEncodeError：Unicode编码错误导致的异常
UnicodeTranslateError：Unicode转换错误导致的异常  
  2. Python标准警告总结
Warning：警告的基类
DeprecationWarning：关于被弃用的特征的警告
FutureWarning：关于构造将来语义会有改变的警告
UserWarning：用户代码生成的警告
PendingDeprecationWarning：关于特性将会被废弃的警告
RuntimeWarning：可疑的运行时行为(runtime behavior)的警告
SyntaxWarning：可疑语法的警告
ImportWarning：用于在导入模块过程中触发的警告
UnicodeWarning：与Unicode相关的警告
BytesWarning：与字节或字节码相关的警告
ResourceWarning：与资源使用相关的警告
3. try - except 语句
try:
    检测范围
except Exception[as reason]:
    出现异常后的处理代码
try 语句按照如下方式工作：
首先，执行try子句（在关键字try和关键字except之间的语句）
如果没有异常发生，忽略except子句，try子句执行后结束。
如果在执行try子句的过程中发生了异常，那么try子句余下的部分将被忽略。如果异常的类型和except之后的名称相符，那么对应的except子句将被执行。最后执行try - except语句之后的代码。
如果一个异常没有与任何的except匹配，那么这个异常将会传递给上层的try中。
 4. try - except - finally 语句
try: 检测范围 except Exception[as reason]: 出现异常后的处理代码 finally: 无论如何都会被执行的代码
不管try子句里面有没有发生异常，finally子句都会执行。
【例子】如果一个异常在try子句里被抛出，而又没有任何的except把它截住，那么这个异常会在finally子句执行后被抛出。
def divide(x, y):
    try:
        result = x / y
        print("result is", result)
    except ZeroDivisionError:
        print("division by zero!")
    finally:
        print("executing finally clause")
divide(2, 1)
# result is 2.0
# executing finally clause
divide(2, 0)
# division by zero!
# executing finally clause
divide("2", "1")
# executing finally clause
# TypeError: unsupported operand type(s) for /: 'str' and 'str'
  5. try - except - else 语句
如果在try子句执行时没有发生异常，Python将执行else语句后的语句。
try:
    检测范围
except:
    出现异常后的处理代码
else:
    如果没有异常执行这块代码
使用except而不带任何异常类型，这不是一个很好的方式，我们不能通过该程序识别出具体的异常信息，因为它捕获所有的异常。
try: 检测范围 except(Exception1[, Exception2[,...ExceptionN]]]): 发生以上多个异常中的一个，执行这块代码 else: 如果没有异常执行这块代码
  【注意：else语句的存在必须以except语句的存在为前提，在没有except语句的try语句中使用else语句，会引发语法错误。】
【例子】
  try:
    fh = open("testfile.txt", "w")
    fh.write("这是一个测试文件，用于测试异常!!")
except IOError:
    print("Error: 没有找到文件或读取文件失败")
else:
    print("内容写入文件成功")
    fh.close()
# 内容写入文件成功
6. raise语句
Python 使用raise语句抛出一个指定的异常。
  

