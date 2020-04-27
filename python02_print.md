<!--
 * @Author: shouxie
 * @Date: 2020-04-27 12:08:07
 * @Description: 
 -->

 # print

print(values,values,sep='',end='\n')
## 格式化输出：
%s:占位符 
print('.........%s......$s' %(str1,str2))
%d:占位符 
## 转义字符：
print('.........%d......$d' %(int1,int2))
\n \t 制表符 \' \r 回车 \\
字符串前面加r，表示原样输出字符串
格式化输出之 %d  %s  %f

代码:
知识点： 
有 + 连接符的使用
## 类型转换： str() , int()
格式化：%d  %f  的使用

name='赵飞'
print('姓名是:'+name)  # str + str

age=18 # str(int) ---> (int ->str)  强制类型的转换 
print('年龄是:'+str(age))  # 'aaa'  int --->str
print('年龄是:%s' % age)  # %s --> str 简写   底层：str(age) ---> '18'
isMarry=False  # 布尔： True， False
print('结婚否？回答: %s' % isMarry)  # str(False) ---> 'False'


```python
print('年龄是:%d' % age) # %d  digit  数字 # age= '18岁'  

# print('年龄是:%d' % age)  

age=18.5   # int(18.5)--->18  取整数
print('年龄是:%d' % age)  

year=2019
print('今年是：%02d' % year)  # 仍然是2019 但是%f就可设置位数


# %f float  小数点后面的位数 而且是四舍五入
salary=8899.32895
print('我的薪水是:%.2f' % salary)
# ticket 49.5                                                                 
# count 35   
# 方法1                                                                 
'''                                                                           
电影 XXX                                                                        
人数 xxx                                                                        
单价 xxx                                                                        
总票价 xxx                                                                       
'''                                                                           
movie = 'ttt'                                                                 
ticket = 79.9                                                                 
count = 35                                                                    
print('电影:%s\n人数:%d\n:单价:%.1f\n总票价%.1f' %(movie,count,ticket,count*ticket))   
# 方法2 
messgae = '''                
电影:%s                
人数:%d                
单价:%.1f              
总票价:%.1f             
'''%(movie,count,ticket,count
print(messgae)   
```
```python
name = 'qpp'                                                                      
age = 19                                                                          
salary='99.99'                                                                    
message = 'my name is {},age is {},my salary is {}'.format(name,age,salary)       
print(message)                                                                      
```
不合法的缩进：
IndentationError: unexpected indent
## ⽤户交互

使⽤input()函数,可以让我们和计算机互动起来
语法:
 内容 = input(提⽰信息)
这⾥可以直接获取到⽤户输入的内容
接收的永远都是字符串
'''python
'''