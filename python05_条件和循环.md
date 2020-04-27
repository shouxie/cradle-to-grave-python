#### if语句
if 条件:
  条件成立执行的语句


if 条件:
  条件成立执行的语句
else:
  条件不成立执行的语句

if 条件:
  语句
elif 条件:
  语句
elif 条件:
  语句
else:
  语句
#### for语句

range(start=0,end,step) # 不包含end

- for i in []:
  语句

- for...else 适用于for正常执行完或者没有循环数据时需要做的事(break跳出来的循环不适用)
for i in []:
  语句
else:
  语句
```python
for i in range(5):
    print('my age is %d' %i)
else:
    print('my age is -0')
```
- pass 空语句
> 只要有锁进，锁进的内容还不确定的时候，此时为了保证语法完整性，可以使用pass占位，不会报语法错误
```python
```
- break 强制跳出for循环！for循环包含整个循环，包含for...else结构的部分
```python
for i in range(3):
    username = input('请输入用户名')
    password = input('请输入密码')
    if username == 'qpp' and password == '11':
        print('hello')
        break
    else:
        print('用户名或密码错误，只有三次机会请重新输入')
else:
    print('账户锁定')
```

#### while 循环
while 条件:
      语句体
else:
      语句体
```python
i = 1
while i <= 30:
    if not(i % 3):
        print('i:%d' % i)
    i += 1

```
Python continue 语句跳出本次循环，而break跳出整个循环。

continue 语句用来告诉Python跳过当前循环的剩余语句，然后继续进行下一轮循环。

continue语句用在while和for循环中。

--------基础部分：从现在开始不看视频了，看菜鸟教程！！！
#### 循环嵌套
