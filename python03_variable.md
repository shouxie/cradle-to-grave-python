# 变量和数据类型
#### 变量
> 将运算的中间结果暂存到内存,以便后续程序调⽤.

变量的命名规则:
 1, 变量由字⺟, 数字,下划线搭配组合⽽成
 2, 不可以⽤数字开头,更不能是全数字
 3,不能是python的关键字, 这些符号和字⺟已经被python占⽤, 不可以更改
 4,不要⽤中⽂
 5,名字要有意义
 6,不要太⻓
 7, 区分⼤⼩写
推荐⼤家使⽤驼峰体或者下划线命名
驼峰体: 除⾸字⺟外的其他每个单词⾸字⺟⼤写
下划线: 每个单词之间⽤下划线分开
#### 常量
在python中不存在绝对的常量. 约定俗成, 所有字⺟⼤写就是常量
例如: PI = 3.141592653
 BIRTH_OF_SYLAR = 1990

#### 注释
 > 有时候我们写的东⻄不⼀定都是给⽤户看的. 或者不希望解释器执⾏. 那我们可以使⽤#来注释掉代码. 被注释的内容是不会执⾏的.可以⽅便后⾯的程序员来拜读你的代码
 单⾏注释: # 被注释的内容
 多⾏注释:''' 被注释的内容 ''', """这个也是多⾏注释"""

#### python的基本数据类型
type() 判断数据类型
int('1') # 转为int类型
str() 转为字符串
%d
多个变量赋值： a,b,c = 1,2,'hello'
python中数据类型可以分为：

- 内置类型
  - 数值类型：整型int，浮点型float，复数（complex） 3+5j
  - str:字符串
  - bool:布尔值【True，False】
  - None：空值，表示变量没有确定的值
  - list：列表
  - tuple：元组
  - dict：字典
  - set：集合
- 自定义类型
  - class ：类

##### 基础类型

- **数值类型**：
  - 整型（int）： python3中只有int一种，可以表示整数，例如：10，-5,10000

  - 浮点型（float）： 表示带小数点的实数，有两种表示法：
    - 小数表示： 1.9     .23
    - 科学计数法： 用e来表示10的指数，1e2就代表了100，注意e前面必须有数值，e后面必须为整数

  - 复数（complex）：表示数学上的无理数，形如：a+bj
----
Python 中数学运算常用的函数基本都在 math 模块、cmath 模块中。

Python math 模块提供了许多对浮点数的数学运算函数。

Python cmath 模块包含了一些用于复数运算的函数。

cmath 模块的函数跟 math 模块函数基本一致，区别是 cmath 模块运算的是复数，math 模块运算的是数学运算。

要使用 math 或 cmath 函数必须先导入：
import math
python3移除了cmp()函数

- **布尔型(bool)**：表示事务的两种状态，男女、阴晴、亮暗等，它只有两个值：True，False
long 类型只存在于 Python2.X 版本中，在 2.2 以后的版本中，int 类型数据溢出后会自动转为long类型。在 Python3.X 版本中 long 类型被移除，使用 int 替代。
- None：表示空对象，一般用于判断，不同于0和空字符

- **字符串（str）**：在python中，用引号（单引号、双引号、三引号）表示字符串

python的字串列表有2种取值顺序:

从左到右索引默认0开始的，最大范围是字符串长度少1
从右到左索引默认-1开始的，最大范围是字符串开头
'h e l l o'
 0 1 2 3 4
 -5 -4 -3 -2 -1
 如果你要实现从字符串中获取一段子字符串的话，可以使用 [头下标:尾下标] 来截取相应的字符串，其中下标是从 0 开始算起，可以是正数或负数，下标可以为空表示取到头或尾。
[头下标:尾下标] 获取的子字符串包含头下标的字符，但不包含尾下标的字符。
Python 列表截取可以接收第三个参数，参数作用是截取的步长
  - 字符串的表示

    ```
    # 用单引号表示： 'hello'
    # 用双引号表示："我用python"
    # 用3个单引号表示：可以表示多行文本，例如：
    	'''伟大
    	   的
    	   祖国
    	 '''
    # 用3个双引号表示：可以表示多行文本，例如：
    	"""生死看淡，
    	不服就干"""
    ```

  - 转义字符：有些特殊字符无法从键盘输入，可以使用转义字符表示，另外，无论是单引号、双引号还是三引号字符串，其中引号是字符串界定符，引号并不是字符串的内容，那么如何在单引号字符串中表示一个单引号呢，这也可以使用转义字符表示。常见的转义字符

    | 转义字符   | 描述          | 转义字符 | 描述       |
    | ------ | ----------- | ---- | -------- |
    | `\'`   | 表示一个普通字符单引号 | \n   | 换行       |
    | `\"`   | 表示一个普通字符双引号 | \r   | 回车       |
    | `\'''` | 一个普通的三单引号   | `\\` | 一个普通的字符 |
    | `\"""` | 一个普通的三双引号   | \a   | 响铃       |
    | \t     | tab键        | \b   | 回删一个字符   |

  - 字符串编码：计算机只能识别二进制，那么字符串如何存储到计算机里呢
    ```
    计算机不能直接存储字符串，但我们可以将字符编码，例如用65表示大写字符A，66表示大写字符B....等这种表示方式就是美国类的ASCII码，只能表示127个字符，但对于美国人来说已经足够了。一但能用整数表示字符，我们可以很方便的把整数用二进制表示，那么字符串也就和容易存储到计算机了。
    但还有很多其他国家的语言是不能用ASCII表示的，所有ISO组织就推出了unicode码，用来表示任何一种语言的字符，unicode码也称之为万国码，通用码，可以表示任何一种语言的任何一个字符。unicdoe码有多中表示方式，例如：utf-8、utf-16、utf-32等。一般使用较多的是utf-8，utf-8是一种变长的编码，表示一个字符可能用一个字节，也可能是三个字节
    中文常用编码一般用GBK编码，用2个字节表示一个汉字
    ```

in， not in 在。。。里
字符串格式化
r 保留原格式
print(r'\'111\'')  # \'111\'
print('\'111\'')  # '111'
hello[start:end:方向和步长] 负数表示反方向，倒叙
```python
hello = 'hello world'
#  逆序输出world 正序输出hello 逆序输出字符串 打印oll 打印llo wo
print(hello[-1:-6:-1])
print(hello[0:5])
print(hello[::-1])
print(hello[4:1:-1])
print(hello[2:8])
```
字符串内置函数
capitalize() # 将字符串第一个字母大写
upper() # 转大写
lower() # 转小写
title() # 每个单词的首字母转大写   istitle() # 判断每个单词的首字母是否是大写
```python
message = 'my name is hh'
msg = message.capitalize()
print(msg)  # My name is hh
msg = message.upper()
print(msg) # MY NAME IS HH
msg = message.lower()
print(msg) # my name is hh
msg = message.title()
print(msg) # My Name Is Hh

valityCode = 'Assfewoi23460jgjF8ib0jjgil2GYTLiKgbhO210'
import random
code = ''
for i in range(4):
    ran = random.randint(0, len(valityCode) - 1)
    code += valityCode[ran]
print(code.lower())

j,code1 = 0,''
while j < 4:
    ran = random.randint(0,len(valityCode)-1)
    code1 += valityCode[ran]
    j +=1
print(code1.lower())
```
find lfind rfind rindex lindex index replace
find(str, beg=0, end=len(string))
检测 str 是否包含在字符串中，如果指定范围 beg 和 end ，则检查是否包含在指定范围内，如果包含返回开始的索引值，否则返回-1

index(str, beg=0, end=len(string))
跟find()方法一样，只不过如果str不在字符串中会报一个异常.

rfind(str, beg=0,end=len(string))
类似于 find()函数，不过是从右边开始查找.

rindex( str, beg=0, end=len(string))
类似于 index()，不过是从右边开始.

replace(old, new [, max])
把 将字符串中的 str1 替换成 str2,如果 max 指定，则替换不超过 max 次。
```python
str = 'hello wolrd'
print('x' in str) # False
print('o' in str) # True
print('x' not in str) # True
print(str.find('x'))
print(str.rfind('o'))
print(str.index('x'))
```
编码：
encode decode
```python
print('哈哈'.encode('utf-8')) # b'\xe5\x93\x88\xe5\x93\x88'
print('哈哈'.encode('utf-8').decode())
```
startswith endswith
startswith(substr, beg=0,end=len(string))
检查字符串是否是以指定子字符串 substr 开头，是则返回 True，否则返回 False。如果beg 和 end 指定值，则在指定范围内检查。
endswith(suffix, beg=0, end=len(string))
检查字符串是否以 obj 结束，如果beg 或者 end 指定则检查指定的范围内是否以 obj 结束，如果是，返回 True,否则返回 False.
```python
print(str.startswith('hell'))
print(str.endswith('d'))
your = input('请上传图片')
if your.endswith('jpg') or your.endswith('png') or your.endswith('gif'):
    print('yes')
else:
    print('no')
```
isalpha()
如果字符串至少有一个字符并且所有字符都是字母则返回 True, 否则返回 False
isdigit()
如果字符串只包含数字则返回 True 否则返回 False..

```python
print(str.replace(' ','').isalpha())
str1 = '121'
print(str1.isdigit())

sum1 = 0
for i in range(3):
    inp = input('请输入数字')
    if inp.isdigit():
        sum1 += int(inp)
    else:
        print('error')
        break
else:
    print('sum %d' % sum1)
```
join lstrip rstrip strip
```python
print('-'.join('hello')) # h-e-l-l-o
list1 = ['h','e','1',0]
print(' '.join(list1)) # TypeError: sequence item 3: expected str instance, int found list包含数字，不能直接转化成字符串。
print(' '.join('%s' % id for id in list1)) # h e 1 0
```
count(str, beg= 0,end=len(string))
返回 str 在 string 里面出现的次数，如果 beg 或者 end 指定则返回指定范围内 str 出现的次数
split(str="", num=string.count(str))
num=string.count(str)) 以 str 为分隔符截取字符串，如果 num 有指定值，则仅截取 num+1 个子字符串
单词：
   Keyword :  关键字
   arguments  参数
Ignore  忽略
Join 加入

##### list：列表
 > 列表可以完成大多数集合类的数据结构实现。它支持字符，数字，字符串甚至可以包含列表（即嵌套）。
列表用 [ ] 标识，是 python 最通用的复合数据类型。
列表中值的切割也可以用到变量 [头下标:尾下标] ，就可以截取相应的列表，从左到右索引默认 0 开始，从右到左索引默认 -1 开始，下标可以为空表示取到头或尾
加号 + 是列表连接运算符，星号 * 是重复操作
```python
list0 = ['hello', 'world', 1, 23, False]
print('list is ', list0[0:4:2])
print(list0*2)
print(list0+[1])
print(list0[-1:])
```
names = ['','','']
extend
append
del
max
min
sum
remove # list.remove(obj)  obj -- 列表中要移除的对象。
clear 清除列表所有元素
list.pop([index=-1]) 移除列表中的一个元素（默认最后一个元素），并且返回该元素的值
list.reverse() 反向列表中元素 会改变列表
list.count(obj) 统计某个元素在列表中出现的次数
list.sort(cmp=None, key=None, reverse=False) 对原列表进行排序

cmp -- 可选参数, 如果指定了该参数会使用该参数的方法进行排序。
key -- 主要是用来进行比较的元素，只有一个参数，具体的函数的参数就是取自于可迭代对象中，指定可迭代对象中的一个元素来进行排序。
reverse -- 排序规则，reverse = True 降序， reverse = False 升序（默认）。


排序，reverse=True 降序
sorted(ranList,reverse=True)
列表中的元素可以存放：列表。。。
类型转换：
list() # 转为列表,只能将可迭代的转为列表，整型不能转
int()
str()
print(list(range(0,5)))  # [0, 1, 2, 3, 4]
```python

list0 = ['1',2,3,'hello',4]
list0.append('world')
print(list0) # ['1', 2, 3, 'hello', 4, 'world']
list0.extend('hello')
print(list0) # ['1', 2, 3, 'hello', 4, 'world', 'h', 'e', 'l', 'l', 'o']
list0.extend([3,4])
print(list0) # ['1', 2, 3, 'hello', 4, 'world', 'h', 'e', 'l', 'l', 'o', 3, 4]
list0 = list0+[0]
print(list0) # ['1', 2, 3, 'hello', 4, 'world', 'h', 'e', 'l', 'l', 'o', 3, 4, 0]
del list0[0]
print(list0) # [2, 3, 'hello', 4, 'world', 'h', 'e', 'l', 'l', 'o', 3, 4, 0]
print(1 in list0) # False
list0.insert(1,'name')
print(list0) # [2, 'name', 3, 'hello', 4, 'world', 'h', 'e', 'l', 'l', 'o', 3, 4, 0]


# 产生10个不同随机数放入列表中
import random
ranList,i = [],0
while i < 10:
    ran = random.randint(0,15)
    if (ran not in ranList):
        ranList.append(ran)
        i+=1
print(ranList)

# max min sum
maxVal = minVal = ranList[0]
sum1 = 0
for i in ranList:
    if i < minVal:
        minVal = i
    if i > maxVal:
        maxVal = i

    sum1 += i
print(maxVal,max(ranList),minVal,min(ranList),sum1,sum(ranList))

```

##### 元组
元组用 () 标识。内部元素用逗号隔开。但是元组不能二次赋值，相当于只读列表。
```python
tuple = (1, 'hello', 1.10, -10, True, 'world')
print(tuple[1:5])  # ('hello', 1.1, -10, True)
print(tuple[0])  # 1
print(tuple*3)  # (1, 'hello', 1.1, -10, True, 'world', 1, 'hello', 1.1, -10, True, 'world', 1, 'hello', 1.1, -10, True, 'world')
print(tuple + (1, 2, 3))  # (1, 'hello', 1.1, -10, True, 'world', 1, 2, 3)
print(tuple[0:4:2])  # (1, 1.1)
```
元组中的元素不可修改
如果元组只有一个元素，需要加上逗号：(1,)
tuple()

下标和切片同列表
sum
min
max
len
tuple.count(obj) # obj存在的次数
tuple.index(obj) # obj的下标，不存在会报错
sorted() # 会返回成列表类型
##### 组包与解包

组包：python解释器自动将多个数据组装到一个容器中
解包：将容器中的多个数据拆出来
```python
#组包: 解释器把1,2,3自动组包成一个元组,然后赋值给a,a的类型就是元组类型的

　　a = 1,2,3 # 相当于 a = (1,2,3)
　　print(a) # (1, 2, 3)
　　print(type(a)) # <class 'tuple'>

#解包: 解释器会自动对元组(1,2)进行 解包,然后把1赋值给m,把2赋值给n，把3赋值给3
　　m,n,k = (1,2,3) # m=1,n=2,k=3
　　print(m) # 1
　　print(n) # 2
　　print(k) # 3 
```
变量个数与元组不一致：
*变量名： 表示未知个数，此变量为列表
```python
a,*b=(1,2,3)
print(a,b, *b, *[1,2,3,4]) # 1 [2, 3] 2 3 1 2 3 4
a,*b = (1,)
print(a,b) # 1 []
```

##### 字典
> 字典(dictionary)是除列表以外python之中最灵活的内置数据结构类型。列表是有序的对象集合，字典是无序的对象集合。
两者之间的区别在于：字典当中的元素是通过键来存取的，而不是通过偏移存取。
字典用"{ }"标识。字典由索引(key)和它对应的值value组成

##### Python数据类型转换
有时候，我们需要对数据内置的类型进行转换，数据类型的转换，你只需要将数据类型作为函数名即可。
以下几个内置的函数可以执行数据类型之间的转换。这些函数返回一个新的对象，表示转换的值。
int(x [,base])

将x转换为一个整数

long(x [,base] )

将x转换为一个长整数

float(x)

将x转换到一个浮点数

complex(real [,imag])

创建一个复数

str(x)

将对象 x 转换为字符串

repr(x)

将对象 x 转换为表达式字符串

eval(str)

用来计算在字符串中的有效Python表达式,并返回一个对象

tuple(s)

将序列 s 转换为一个元组

list(s)

将序列 s 转换为一个列表

set(s)

转换为可变集合

dict(d)

创建一个字典。d 必须是一个序列 (key,value)元组。

frozenset(s)

转换为不可变集合

chr(x)

将一个整数转换为一个字符

unichr(x)

将一个整数转换为Unicode字符

ord(x)

将一个字符转换为它的整数值

hex(x)

将一个整数转换为一个十六进制字符串

oct(x)

将一个整数转换为一个八进制字符串
```python
# 元组只有成对出现才可以转字典
tuple3 = (('name', '123'),('age',12))
print(dict(tuple3)) # {'name': '123', 'age': 12}
tuple4 = [('name', '123', '456'),('age', 12,13)]
print(dict(tuple4)) # ValueError: dictionary update sequence element #0 has length 3; 2 is required
```
增加：
字典不支持‘+’ # obj1+obj2 报错
dict.get(key, default=None):返回指定键的值，如果值不在字典中返回default值
dict.clear():删除字典内所有元素
dict.copy(): 返回一个字典的浅复制
dict.has_key(key):如果键在字典dict里返回true，否则返回false，py3已移除，改为__contains__
dict.fromkeys(seq[, val]): 创建一个新字典，以序列 seq 中元素做字典的键，val 为字典所有键对应的初始值
dict.setdefault(key, default=None):**和get()类似, 但如果键不存在于字典中，将会添加键并将值设为default**
dict.update(dict2):把字典dict2的键/值对更新到dict里,如果有相同的key，会替换成update的值
pop(key[,default]):删除字典给定键 key 所对应的值，返回值为被删除的值。key值必须给出。 否则，返回default值。
popitem():返回并删除字典中的最后一对键和值。
```python
obj = {}
obj['name'] = 'zhangsan'
print(obj) # {'name': 'zhangsan'}
print(obj['name'])  # zhangsan # 取不到会报错

print(obj.get('age')) # 18 如果取不到不会报错

for i in obj:
    print(i) # 遍历出来的是key


obj.clear()
print(obj)
obj['name'] = 'zhangsan'
obj['age'] = 19
obj['ferght'] = 100
print(obj.copy())
print(obj.get('aaa',1), obj)  # 1 {'name': 'zhangsan', 'age': 19, 'ferght': 100}
print(obj.setdefault('aaa',1),obj) # 1 {'name': 'zhangsan', 'age': 19, 'ferght': 100, 'aaa': 1}
# print(obj.has_key('name')) # py3 remove
print(obj.__contains__('name'))  # True

obj1 = {'name': 'lisi', 'age':20,'hhh':'hello'}
obj1.update(obj)
print(obj1) # {'name': 'zhangsan', 'age': 19, 'hhh': 'hello', 'ferght': 100, 'aaa': 1}

print(obj2.fromkeys(tuple5)) # {'name': None, 'age': None}
print(obj2.fromkeys(tuple5, 10)) # {'name': 10, 'age': 10}
print(obj2.fromkeys(list1))
print(obj2.fromkeys(list1,10))
print(obj2) # {}
```
字典里面的函数：
items() values() keys()
```python
# 转为列表包含元组的形式
print(obj.items()) # dict_items([('name', 'zhangsan'), ('age', 18)])
# 取出字典中所有的值，保存到列表中
print(obj.values()) # dict_values(['zhangsan', 18])
# 取出字典中所有的key 保存到列表中
print(obj.keys()) # dict_keys(['name', 'age'])

for i in obj.items():
    print(i) 
    # ('name', 'zhangsan')   
    #  ('age', 18)
for key, value in obj.items():
    print(key,value)
    '''
    name zhangsan
    age 18
    '''
```
删除：
del dict[key]
内置函数：
dict.pop(key, default) # 返回删除的value，会改变dict.default为删除的时候找不到key，返回默认值
dict.popitem() # 一般从末尾删除元素
```
#### 集合 set
无序，不重复的集合
s1 = set() # 创建空集合只能用set()方式，因为 s1={} 声明一个字典
{元素1,元素2,元素3,...} 
```python
list1 = [1,2,2,3,4]
print(set(list1))
```
add
update
```python
s1 = set()
s1.add('hello')
s1.add('111')
s1.add(2)
print(s1) # {'111', 2, 'hello'}
s1.update((1,2))
print(s1) # {'111', 1, 2, 'hello'}
s1.add((1,2))
print(s1) # {1, 2, (1, 2), '111', 'hello'}
```

删除：
pop # 删除第一个
remove # 删除指定元素 删除不存在元素会报错
clear
dicard # 删除指定元素 删除不存在元素不报错

符号操作：
in
== ：判断两个集合中的内容是否相等 
-： 差集 difference
&： 交集 intersection
| ： 并集 union
^：对称差集 ----- 两个集合中不同的元素
不支持+ *
difference_update() # 加上update，就是会改变集合 s1.difference_update(s2)  将差集赋值给s1
```python
# 集合的交集，并集，差集合
s1 = {1,2,3,4}
s2 = {1,2,3,5,6,7}

s3 = s2 - s1
print(s3) # {5, 6, 7}
print(s2.difference(s1)) # {5, 6, 7}

s4 = s1 & s2
print(s1.intersection(s2)) # {1, 2, 3}
print(s4) # {1, 2, 3}

s5 = s1 | s2
print(s1.union(s2)) # {1, 2, 3, 4, 5, 6, 7}
print(s5) # {1, 2, 3, 4, 5, 6, 7}

 # 对称差集 ----- 两个集合中不同的元素
print(s1^s2) # {4, 5, 6, 7}
```
##### 类型判断

我们可以使用type和isinstance来测试和判断数据类型

~~~
#type用法：
  type(obj)
  功能：返回obj的数据类型
  参数：obj是你要测试变量或数值
  示例：
    age = 10
    name = 'hello'
    print(type(name),type(age))
    
    #判断变量是否是指定类型
    if type(age) is int:
       print('是')
    else:
       print('否')

#isinstance用法：
  isinstance(obj,typename)
  功能：判断obj是否是指定类型，是返回True,否返回False
  参数： objobj是你要判断的变量或数值
        typename是指定数据类型,可以是int,float,str等。也可是一个
                 类型的元组,例如:(int,float)
  示例：
    age = 10
	name = 'hello'	
	print(isinstance(age,int))
	print(isinstance(name,(str,int)) #只要name是str或int的一种就返回True
	
	if isinstance(age,int):
	    print('是')
	else:
	    print('否')
	    
#type和isinstance的区别
type判断基本类型是没问题的，但无法判断子类对象是父类的一种
isinstance可以判断子类对象是父类的一种
class A:
    pass

class B(A):
    pass

objA = A()
objB = B()

#输出否
if type(objB) is A:
    print('是')
else:
    print('否')
    
print(isinstance(objB,A))  #True
~~~

结论：优先使用isinstance

##### 整数(int)
> 常⻅的数字都是int类型. ⽤于计算或者⼤⼩的比较
在32位机器上int的范围是: -2**31～2**31-1，即-2147483648～2147483647
在64位机器上int的范围是: -2**63～2**63-1，即-9223372036854775808～9223372036854775807
够你⽤了吧. 注意这些是整数. 

##### 字符串(str)
> 在Python中,凡是⽤引号引起来的,全是字符串.
字符串可以⽤单引号，双引号，或者三引号引起来，没有什么区别，只是⼀些特殊的格式需要不⽤的引号
⽐如：
```python
msg = "My name is Alex , I'm 22 years old!" 
# 这个就需要单双引号配合。
msg = """
今天我想写⾸⼩诗，
歌颂我的同桌，
你看他那乌⿊的短发，
好像⼀只炸⽑鸡。
"""
'''想多⾏赋值⼀个字符串，就需要三引号。
数字类型有 +-*/ 字符串有么？
字符串只有 + *。
'''
#字符串的拼接
s1 = 'a '
s2 = 'bc'
#print(s1 + s2)
#相乘 str*int 重复int次的字符串,float 类型的会报错
name = '坚强'
#print(name*8)
# print(s1+s2+1) 字符串拼接int类型会报错
```
''' 保证样式（格式）输出，换行空格等，作为注释使用

##### 布尔值(bool), 真或者假, True和False

##### 可变 不可变
不可变： 对象所指的内存中的值是不可变的（int string float tuple）
可变: dict字典 list列表 set集合,  值改变
```python
# 变量的值改变，是重新指向了一个地址空间
str = 'hello'
print(id(str)) # 4335977392
str = 'hello1'
print(id(str)) # 4335985392

li = [1,2,3]
print(li, id(li)) # [1, 2, 3] 4519372928
li.pop()
print(li,id(li)) # [1, 2] 4519372928

s = {1,2,3}
print(s,id(s)) # {1, 2, 3} 4527199616
s.discard(1)
print(s,id(s)) # {2, 3} 4527199616
```
##### 类型转换
