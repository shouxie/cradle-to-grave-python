
 ##  进程(待详细补充，后续会详细总结os)

 > 进程是计算机中的程序关于某数据集合上的一次运行活动，是系统进行资源分配和调度的基本单位，是操作系统结构的基础

- 进程特征

动态性：进程的实质是程序在多道程序系统中的一次执行过程，进程是动态产生，动态消亡的。
并发性：任何进程都可以同其他进程一起并发执行。
独立性：进程是一个能独立运行的基本单位，同时也是系统分配资源和调度的独立单位。
异步性：由于进程间的相互制约，使进程具有执行的间断性，即进程按各自独立的、不可预知的速度向前推进。

- 结构组成：程序、数据和进程控制块

- 进程与程序区别

程序是指令和数据的有序集合，其本身没有任何运行的含义，是一个静态的概念。
而进程是程序在处理机上的一次执行过程，它是一个动态的概念。
程序可以作为一种软件资料长期存在，而进程是有一定生命期的。
程序是永久的，进程是暂时的。


生活中，你可能一边听歌，一边写作业；一边上网，一边吃饭。。。这些都是生活中的多任务场景。电脑也可以执行多任务，比如你可以同时打开浏览器上网，听音乐，打开pycharm编写代码...。简单的说**多任务就是同一时间内运行多个程序**

- 单核CPU实现多任务原理：操作系统轮流让各个任务交替执行，QQ执行2us，切换到微信，在执行2us，再切换到陌陌，执行2us……。表面是看，每个任务反复执行下去，但是CPU调度执行速度太快了，导致我们感觉就行所有任务都在同时执行一样
（os里面，时间片原理）
- 多核CPU实现多任务原理：真正的秉性执行多任务只能在多核CPU上实现，但是由于任务数量远远多于CPU的核心数量，所以，os也会自动把很多任务轮流调度到每个核心上执行（待补充：进程调度算法：先来先服务，短作业优先等）

- 并发和并行
  - **并发**：当有多个线程在操作时,如果系统只有一个CPU,则它根本不可能真正同时进行一个以上的线程，它只能把CPU运行时间划分成若干个时间段,再将时间 段分配给各个线程执行，在一个时间段的线程代码运行时，其它线程处于挂起状。.这种方式我们称之为并发(Concurrent)。**同一时间段**
  - **并行**：当系统有一个以上CPU时,则线程的操作有可能非并发。当一个CPU执行一个线程时，另一个CPU可以执行另一个线程，两个线程互不抢占CPU资源，可以同时进行，这种方式我们称之为并行(Parallel)。**同一时刻**
- 实现多任务的方式：
  - 多进程模式；
  - 多线程模式；
  - 协程。
  进程  >  线程  >  协程

## 同步/异步
同步（synchronous）： 所谓同步就是一个任务的完成需要依赖另外一个任务时，只有等待被依赖的任务完成后，依赖的任务才能算完成，这是一种可靠的任务序列。

简言之，要么成功都成功，失败都失败，两个任务的状态可以保持一致。

异步（asynchronous）：所谓异步是不需要等待被依赖的任务完成，只是通知被依赖的任务要完成什么工作，依赖的任务也立即执行，只要自己完成了整个任务就算完成了。至于被依赖的任务最终是否真正完成，依赖它的任务无法确定，所以它是不可靠的任务序列。

## python 中进程

### 进程创建
```python
# -*- coding:utf-8 -*-
#@Time : 2020/4/28 下午3:00
#@Author: 手写
#@File : process1.py

from multiprocessing import Process
# import time
from time import sleep
import os
def task1():
    while True:
        sleep(1)
        print('-------------> task1', 'task1的进程号是：{}, 父进程是：{}'.format(os.getpid(), os.getppid()))

def task2():
    while True:
        sleep(1)
        print('--------------> task2', 'task2的进程号是：{}, 父进程是: {}'.format(os.getpid(), os.getppid()))

if __name__ == '__main__':
    # built-in: def __init__(self, group=None, target=None, name=None, args=(), kwargs={}):
    p1 = Process(target=task1, name='task1')
    p1.start()
    p2 = Process(target=task2, name='task2')
    p2.start()
    print('-------------->main', 'main 进程号:{}'.format(os.getpid()))
    
    
'''
运行的时候会开启一个进程。
运行结果：
-------------->main main 进程号:11495
-------------> task1 task1的进程号是：11497, 父进程是：11495
--------------> task2 task2的进程号是：11498, 父进程是: 11495
'''
```
### 进程创建，传参
from multiprocessing import Process

  process = Process(target= 函数，name=进程的名字，args=（给函数传递的参数）)
  process 对象

  对象调用方法:
  process.start()    启动进程并执行任务
  process.run()  只是执行了任务但是没有启动进程
  terminate()   终止
  is_alive      判断进程是否存活
  ```python
  # 上述代码：
  def task1(sec):
    while True:
        sleep(sec)
        print('-------------> task1', 'task1的进程号是：{}, 父进程是：{}'.format(os.getpid(), os.getppid()))

  p1 = Process(target=task1, name='task1', args=(2,))
  ```
  ### 多进程对于全局变量访问
  **进程访问变量互不干扰**
  多进程对于全局变量访问，在每一个全局变量里面都放一个m变量，
  保证每个进程访问变量互不干扰。
  m = 1  # 不可变类型
  list1 = []  # 可变类型
  主进程启动子进程，启动之后无法控制是谁先谁后
  ```python
  # -*- coding:utf-8 -*-
#@Time : 2020/4/28 下午3:00
#@Author: 手写
#@File : process1.py

from multiprocessing import Process
# import time
from time import sleep
import os

num = 0
def task1(sec):
    while True:
        global num
        sleep(sec)
        num += 1
        print('-------------> task1, num : {}'.format(str(num)))

def task2():
    global num
    while True:
        sleep(1)
        num += 1
        print('--------------> task2, num:{}'.format(str(num)))

if __name__ == '__main__':
    # built-in: def __init__(self, group=None, target=None, name=None, args=(), kwargs={}):
    p1 = Process(target=task1, name='task1', args=(2,))
    p1.start()
    p2 = Process(target=task2, name='task2')
    p2.start()
    # 这里会先输出，因为父进程创建完成，子进程创建完成就干子进程的事了
    # print('-------------->main, main num : {}'.format(str(num)))

    while True:
        sleep(1)
        print('-------------->main, main num : {}'.format(str(num)))
'''
运行的时候会开启一个进程。
运行结果：
-------------->main, main num : 0
--------------> task2, num:1
-------------->main, main num : 0
-------------> task1, num : 1
--------------> task2, num:2
-------------->main, main num : 0
--------------> task2, num:3
-------------->main, main num : 0
-------------> task1, num : 2
--------------> task2, num:4
-------------->main, main num : 0
--------------> task2, num:5
-------------->main, main num : 0
-------------> task1, num : 3
--------------> task2, num:6
-------------->main, main num : 0
--------------> task2, num:7
-------------->main, main num : 0
-------------> task1, num : 4
--------------> task2, num:8
'''
  ```

  ### 进程：自定义

  ```python
  # -*- coding:utf-8 -*-
# @Time : 2020/4/29 上午11:01
# @Author: 手写
# @File : process2.py

from multiprocessing import Process


class MyProcess(Process):
    def __init__(self, name):
        super().__init__()
        self.name = name

    # 重写run方法
    def run(self):
        n = 1
        while True:
            print('----------> 自定义进程{}, n: {}'.format(self.name, n))
            n += 1


def task():
    while True:
        print('---------> task')


if __name__ == '__main__':
    p = MyProcess('test')
    # p1 = Process(target=task, name='task')
    # p1.start()
    p.start()


  ```

  ### 进程池
  > 当需要创建的子进程数量不多时，可以直接利用multiprocessing中的Process动态成生多个进程，
但如果是上百甚至上千个目标，手动的去创建进程的工作量巨大，此时就可以用到multiprocessing模块提供的Pool方法。
初始化Pool时，可以指定一个最大进程数，当有新的请求提交到Pool中时，如果池还没有满，
那么就会创建一个新的进程用来执行该请求；但如果池中的进程数已经达到指定的最大值，那么该请求就会等待，
直到池中有进程结束，才会创建新的进程来执行。

 pool = Pool(max)  创建进程池对象
 pool.apply()  阻塞的
 pool.apply_async()  非阻塞的
 pool.close()  添加任务结束
 pool.join()  让主进程让步，让出cpu

```python
# -*- coding:utf-8 -*-
# @Time : 2020/4/29 上午11:20
# @Author: 手写
# @File : pool3.py

from multiprocessing import Pool

'''
非阻塞式: 全部添加到队列中，立刻返回，并没有等待其他的进程完毕，但是回调函数是等待任务完成之后才调用。
阻塞式: 添加一个执行一个任务，如果一个任务不结束另一个任务就进不来

创建一个进程池，最大连接为5。每个进程执行一个任务
'''
list0 = []
import random
from time import sleep, time
from multiprocessing import Pool


def task(taskname):
    print('-----------> 执行任务： {}开始'.format(taskname))
    startTime = time()
    sleep(random.random())
    endTime = time()
    print('-----------> 执行任务： {}完成'.format(taskname), '用时{}'.format(str(endTime - startTime)))
    return '任务{} 用时{}'.format(taskname, str(endTime - startTime))


def handleCall(data):
    list0.append(data)


if __name__ == '__main__':
    # def __init__(self, processes=None, initializer=None, initargs=(),  processes: 最大进程数
    #                  maxtasksperchild=None, context=None):
    p = Pool(5)

    # built-in： def apply_async(self, func, args=(), kwds={}, callback=None, 非阻塞
    #         error_callback=None):
    #     '''
    #     Asynchronous version of `apply()` method.
    #     '''
    tasks = ['任务1', '任务2', '任务3', '任务4', '任务5', '任务6', '任务7']
    for i in tasks:
        # p.apply_async(task, args=(i,), callback=handleCall)

        # built-in： def apply(self, func, args=(), kwds={}):
        p.apply(task, args=(i,))
    # p.apply_async(task, args=('任务1',),  callback=handleCall)
    # p.apply_async(task, args=('任务2',), callback=handleCall)
    # p.apply_async(task,args=('任务3',), callback=handleCall)
    p.close()# 添加任务结束
    p.join()

    for l in list0:
        print('l:', l)

'''
运行结果：
非阻塞式
-----------> 执行任务： 任务1开始
-----------> 执行任务： 任务2开始
-----------> 执行任务： 任务3开始
-----------> 执行任务： 任务4开始
-----------> 执行任务： 任务5开始
-----------> 执行任务： 任务3完成 用时0.3876230716705322
-----------> 执行任务： 任务6开始
-----------> 执行任务： 任务4完成 用时0.43808794021606445
-----------> 执行任务： 任务7开始
-----------> 执行任务： 任务1完成 用时0.5240042209625244
-----------> 执行任务： 任务2完成 用时0.6877861022949219
-----------> 执行任务： 任务5完成 用时0.8197996616363525
-----------> 执行任务： 任务6完成 用时0.7132937908172607
-----------> 执行任务： 任务7完成 用时1.0014679431915283
l: 任务任务3 用时0.3876230716705322
l: 任务任务4 用时0.43808794021606445
l: 任务任务1 用时0.5240042209625244
l: 任务任务2 用时0.6877861022949219
l: 任务任务5 用时0.8197996616363525
l: 任务任务6 用时0.7132937908172607
l: 任务任务7 用时1.0014679431915283


pool中最大5个进程，当任务3完成的时候，任务6就可以开始了。每个任务做完都把用时抛出来，回调方法接收这个返回值，回调方法就是任务完成要执行的动作

阻塞式
-----------> 执行任务： 任务1开始
-----------> 执行任务： 任务1完成 用时0.21695709228515625
-----------> 执行任务： 任务2开始
-----------> 执行任务： 任务2完成 用时0.38028597831726074
-----------> 执行任务： 任务3开始
-----------> 执行任务： 任务3完成 用时0.8004181385040283
-----------> 执行任务： 任务4开始
-----------> 执行任务： 任务4完成 用时0.3384280204772949
-----------> 执行任务： 任务5开始
-----------> 执行任务： 任务5完成 用时0.48204588890075684
-----------> 执行任务： 任务6开始
-----------> 执行任务： 任务6完成 用时0.5169289112091064
-----------> 执行任务： 任务7开始
-----------> 执行任务： 任务7完成 用时0.3745450973510742
'''

```

### 进程间通信

队列和管道属于进程之间的通信机制。

#### 队列

> 创建共享的进程队列，Queue是多进程安全的队列，可以使用Queue实现多进程之间的数据传递。

```python
# -*- coding:utf-8 -*-
#@Time : 2020/4/29 下午12:07
#@Author: 手写
#@File : queue4.py

from multiprocessing import Queue


# built-in: def __init__(self, maxsize=-1):
q = Queue(5)
# built-in: def put(self, obj, block=True, timeout=None):
# q.put('1') 如果queue满了则只能等待，除非有‘空地’则添加成功
for i in range(4):
    q.put(str(i)) 

# print(q.qsize())
print(q.get(timeout=2))
print(q.get(timeout=2))
print(q.full()) # 判断队列是否满
print(q.empty())
q.get_nowait()

'''
mac 不能打印 print(q.qsize())
NotImplementedError
 # Raises NotImplementedError on Mac OSX because of broken sem_getvalue()
'''
```
#### 队列实现进程间通讯
```python
# -*- coding:utf-8 -*-
# @Time : 2020/4/29 下午1:54
# @Author: 手写
# @File : process5.py

from multiprocessing import Process, Queue
from time import sleep


def download(q):
    print('download start')
    sleep(2)
    print('download end')
    q.put('1.png')


def save(q):
    image = q.get()
    print(image)


if __name__ == '__main__':
    q = Queue(5)
    p1 = Process(target=download, args=(q,))
    p2 = Process(target=save, args=(q,))
    p1.start()
    p1.join()
    p2.start()
    p2.join()

```

## 线程

> 进程是线程的容器
进程有很多优点，它提供了多道编程，让我们感觉我们每个人都拥有自己的CPU和其他资源，可以提高计算机的利用率.但是进程只能在一个时间干一件事，如果想同时干两件事或多件事，进程就无能为力了；进程在执行的过程中如果阻塞，例如等待输入，整个进程就会挂起，即使进程中有些工作不依赖于输入的数据，也将无法执行

进程由若干线程组成，一个进程至少一个线程；
一个标准的线程由线程ID，当前指令指针(PC），寄存器集合和堆栈组成。线程是进程中的一个实体，是被系统独立调度和分派的基本单位，线程自己不拥有系统资源，只拥有一点儿在运行中必不可少的资源，但它可与同属一个进程的其它线程共享进程所拥有的全部资源。
一个线程可以创建和撤消另一个线程，同一进程中的多个线程之间可以并发执行。由于线程之间的相互制约，致使线程在运行中呈现出间断性。线程也有就绪、阻塞和运行三种基本状态。就绪状态是指线程具备运行的所有条件，逻辑上可以运行，在等待处理机；运行状态是指线程占有处理机正在运行；阻塞状态是指线程在等待一个事件（如某个信号量），逻辑上不可执行。每一个程序都至少有一个线程，若程序只有一个线程，那就是程序本身

### 线程和进程区别

地址空间和其它资源（如打开文件）：进程间相互独立，同一进程的各线程间共享。某进程内的线程在其它进程不可见。
通信：进程间通信IPC，线程间可以直接读写进程数据段（如全局变量）来进行通信——需要进程同步和互斥手段的辅助，以保证数据的一致性。
调度和切换：线程上下文切换比进程上下文切换要快得多。
在多线程操作系统中，进程不是一个可执行的实体。


### 创建线程

```python
# -*- coding:utf-8 -*-
#@Time : 2020/4/29 下午2:10
#@Author: 手写
#@File : thread6.py
from time import sleep
import threading

def download():
    print('download start')
    sleep(2)
    print('download end')

def listen():
    print('listen start')
    sleep(3)
    print('listen end')

if __name__ == '__main__':
    '''
    built-in:
    def __init__(self, group: None = ...,
                     target: Optional[Callable[..., None]] = ...,
                     name: Optional[str] = ...,
                     args: Iterable = ...,
                     kwargs: Mapping[str, Any] = ...,
                     *, daemon: Optional[bool] = ...) -> None: ...
                     
         __init__(self, group=None, target=None, name=None,
     args=(), kwargs=None, *, daemon=None):
    '''
    t1 = threading.Thread(target=download, name='download')
    t2 = threading.Thread(target=listen, name='listen')
    t1.start()
    t2.start()
```
### 线程共享全局变量

```python
# -*- coding:utf-8 -*-
# @Time : 2020/4/29 下午2:20
# @Author: 手写
# @File : thread7.py
import threading
from time import sleep

ticket = 100


def buy1():
    global ticket
    n = 0
    while n < 100:
        if ticket > 0:
            sleep(0.1)
            ticket -= 1
            print('buy01 ticket {}'.format(ticket))
            n += 1
        else:
            print('票没了')

def buy2():
    global ticket
    n = 0
    while n < 100:
        if ticket > 0:
            sleep(0.1)
            ticket -= 1
            print('buy02 ticket {}'.format(ticket))
            n -= 1
        else:
            print('票没了')


if __name__ == '__main__':
    t1 = threading.Thread(target=buy1, name='buy1')
    t2 = threading.Thread(target=buy2, name='buy2')
    t1.start()
    t2.start()

```

### GIL 全局解释器锁

> 为了让各个线程能够平均利用CPU时间，python会计算当前已执行的微代码数量，达到一定阈值后就强制释放GIL

```python
# -*- coding:utf-8 -*-
#@Time : 2020/4/29 下午2:29
#@Author: 手写
#@File : thread8.py

import threading

n = 1

def func():
    global n
    for i in range(100000000):
        n += 1
        print(n)

if __name__ == '__main__':
    t1 = threading.Thread(target=func, name='func1')
    t2 = threading.Thread(target=func, name='func2')
    t1.start()
    t2.start()
```

Gil锁  : 保证同一时刻只有一个线程能使用到cpu
互斥锁 : 多线程时,保证修改共享数据时有序的修改,不会产生数据修改混乱