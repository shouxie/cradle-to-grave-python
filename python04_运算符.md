#### 运算符种类
- 赋值运算符
 = += -= *= /=
 id(var1) # 返回变量内存地址
- 算术运算符
加：+  减：- 乘：* 除：/ 幂：** 整除：// 取余：% 
'str'*n # n次str
```python
print(8**2) # 64
print('hello'*3) #hellohellohello
```
数学函数

|     函数名      |          函数的说明           | 示例                          |
| :----------: | :----------------------: | --------------------------- |
|     abs      |           取绝对值           | abs(-10)                    |
|   pow(x,y)   |          x的y次方           | pow(10,2)求10的平方             |
| round(x,[n]) |   浮点数的4舍5入， n代表保留小数的位数   | round(3.456)                |
|    max()     |        求给定参数的最大值         | max(21,43,65,75,86,32,3,45) |
|    min()     |        求给定参数的最小值         | min(21,43,65,75,86,32,3,45) |
| math.ceil()  | 需要导入import  math库   向上取整 | math.ceil(18.1) #19         |
| math.floor() | 需要导入import  math库   向下取整 | math.floor(18.1) #18        |
|  math.sqrt   | 需要导入import  math库   求平方根 | math.sqrt(100)              |


随机函数

获取随机数，需要引入random库。

import  random

|                函数名                |                   函数说明                   |
| :-------------------------------: | :--------------------------------------: |
| random.randrange(start,stop,step) | start 指定范围的起始值 包含本身，默认是0；stop 指定范围的结束值 不包含本身； step 步长，默认步长是1。该函数返回一个整数 |
|     random.randint(start,end)     |   返回[start  end]之间的一个随机整数，start必须小于end   |
|          random.random()          |           返回一个[0.0,1.0)之间的随机小数           |

##### 注意

 优先级：  ** >正负号 > // % * /  > + -
 从左向右算
 tip:!!!在幂运算和一元运算符联合计算时，从右向左算，例如： -1 ** 2 = -1

- 关系运算符
'''
源文件：一起解释编译复用内存
交互式：小整数复用 大整数，定义一个变量会重新开辟内存
'''
关系运算就是比较运算，如果表达式成立，返回True，否则返回False。关系运算的结果是布尔值。

| 运算符  | 示例       | 说明                             |
| ---- | -------- | ------------------------------ |
| ==   | a == b   | a和b值相等，结果是True，a和b值不相等结果为False |
| !=   | a != b   | a不等于b 结果为True，否则结果为True        |
| >    | a  > b   | a大于b结果为True，否则为False           |
| >=   | a  >=  b | a大于等于b结果为True，否则为False         |
| <    | a < b    | a小于b结果为True，否则为False           |
| <=   | a <= b   | a小于等于b结果为True，否则为False         |
is 对象比较
注意：

 优先级： 比较运算符优先级相同
 从左向右算
 可以这样算：`1 < a < 3`  等价于 a > 1  and  a < 3

- 逻辑运算符
逻辑运算符可以用于构造复杂条件。逻辑运算符包括：

 逻辑与 and  对应汉语的意思是“并且”  、 “同时”
 逻辑或  or   对应汉语意思为"或者"
 逻辑非 not  对应汉语意思为”相反“

在逻辑运算中，False、None、0、0.0、‘’（空字符串）被看做假（False），其它的看做真(True)

- 位运算符
bin() # 十进制转二进制 二进制表示：以0b开头
int() # 二进制转十进制
八进制表示：以0o开头
八进制转二进制 3610 -> 3 -> 011  6 -> 110   1 -> 001   0 -> 000 ===>  011110001
负数：
>正数的反码和补码都与原码相同。 
而负数的反码为对该数的原码除符号位外各位取反。 
负数的补码为对该数的原码除符号位外各位取反，然后在最后一位加1 
在计算机中，负数以原码的补码形式表达。 

bit byte 1byte=8bit 二进制表示其实有8位 如： 5 ---> 0000 0101
二进制负数计算：
5求负数：-x=!x+1
1. 先求5的二进制 0000 0101
2. 取反         1111 1010
3. 最后位数加1   1111 1011

bin(-5) # python 的bin方法，是直接求出5的二进制表示，再在前面加负号

十六进制 以0x开头，0-9 a-f
十六进制转二进制 3610 -> 3 -> 0011  6 -> 0110   1 -> 0001   0 -> 0000 ===>  0011011000010000

---
第一位是符号位，1为负数，0为正数
异或: 两个数上下对齐，相同为0，不同为1
##### 位运算 与：& 或：|  非：~ 异或：^ 左移：>> 右移：<<
&：
1 True 0 False
  0000 1010
& 0101 0011
——————————————
  0000 0010

```python
# -x=!x+1 在计算机中，负数以原码的补码形式表达。
print(~0b0101)  # 取反=> 1111 1010 减1-> 1111 1001      取反->0000 0110
print(~-4)  # -4 : 化二进制数：- 0000 0100 -> 1111 1011 +1 -> 1111 1100 取反==== 0000 0011 正数 不需要转换 为3
print(~5)  # 6: 0000 0101 -> 各位取反： 1111 1010 转为10进制数： ------> 1开头的为负数。转为： x=！（-x-1） 1111 1001 -》 0000 0110 -》 -6

```
左移：>> m>>n m*2的n次方
右移：<< m<<n m//2

#### 三目运算符
resultTrue if tiaojian else resultFalse

#### 运算符优先级
**
~
+ - (符号运算符)
* / // %
+ - (加减)
<< >>
&
^
|
== != < > <= >=
is is not
not
and
or