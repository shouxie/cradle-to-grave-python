# python 简介

乱七八糟的整理出来，js转python，首先克服下语法习惯，没有分号真的难受。😣

> python的创始⼈为吉多·范罗苏姆（Guido van Rossum）龟爷。1989年的圣诞节期间，吉多·
范罗苏姆为了在荷兰-阿姆斯特丹打发时间，决⼼开发⼀个新的脚本解释程序，作为ABC语⾔的⼀种继承。 
Python可以应⽤于众多领域，如：数据分析、组件集成、⽹络服务、图像处理、数值计算
和科学计算等众多领域

## ⽬前Python主要应⽤领域
- 云计算: 云计算最⽕的语⾔， 典型应⽤OpenStack
- WEB开发: 众多优秀的WEB框架，众多⼤型⽹站均为Python开发，Youtube, Dropbox, ⾖瓣。。。， 典型WEB框架有Django
- 科学运算、⼈⼯智能: 典型库NumPy, SciPy, Matplotlib, Enthought librarys,pandas
- 系统运维: 运维⼈员必备语⾔
- ⾦融：量化交易，⾦融分析，在⾦融⼯程领域，Python不但在⽤，且⽤的最多，⽽且重要性逐年提⾼。原因：作为动态语⾔的Python，语⾔结构清晰简单，库丰富，成熟稳定，科学计算和统计分析都很⽜逼，⽣产效率远远⾼于c,c++,java,尤其擅⻓
策略回测
- 图形GUI: PyQT, WxPython,TkInter


## python的优缺点
- 优点：
  - Python的定位是“优雅”、“明确”、“简单”，所以Python程序看上去总是简单易
懂，初学者学Python，不但⼊⻔容易，⽽且将来深⼊下去，可以编写那些⾮常⾮常
复杂的程序。
  - 开发效率⾮常⾼，Python有⾮常强⼤的第三⽅库，基本上你想通过计算机实现任何
功能，Python官⽅库⾥都有相应的模块进⾏⽀持，直接下载调⽤后，在基础库的基
础上再进⾏开发，⼤⼤降低开发周期，避免重复造轮⼦。
  - ⾼级语⾔————当你⽤Python语⾔编写程序的时候，你⽆需考虑诸如如何管理你
的程序使⽤的内存⼀类的底层细节
  - 可移植性————由于它的开源本质，Python已经被移植在许多平台上（经过改动
使它能够⼯ 作在不同平台上）。如果你⼩⼼地避免使⽤依赖于系统的特性，那么你
的所有Python程序⽆需修改就⼏乎可以在市场上所有的系统平台上运⾏
  - 可扩展性————如果你需要你的⼀段关键代码运⾏得更快或者希望某些算法不公
开，你可以把你的部分程序⽤C或C++编写，然后在你的Python程序中使⽤它们。
  - 可嵌⼊性————你可以把Python嵌⼊你的C/C++程序，从⽽向你的程序⽤户提供
脚本功能。
- 缺点：
  - 速度慢，Python 的运⾏速度相⽐C语⾔确实慢很多，跟JAVA相⽐也要慢⼀些，因此
这也是很多所谓的⼤⽜不屑于使⽤Python的主要原因，但其实这⾥所指的运⾏速度
慢在⼤多数情况下⽤户是⽆法直接感知到的，必须借助测试⼯具才能体现出来，⽐如
你⽤C运⼀个程序花了0.01s,⽤Python是0.1s,这样C语⾔直接⽐Python快了10倍,
算是⾮常夸张了，但是你是⽆法直接通过⾁眼感知的，因为⼀个正常⼈所能感知的时
间最⼩单位是0.15-0.4s左右，哈哈。其实在⼤多数情况下Python已经完全可以满
⾜你对程序速度的要求，除⾮你要写对速度要求极⾼的搜索引擎等，这种情况下，当
然还是建议你⽤C去实现的。
  - 代码不能加密，因为PYTHON是解释性语⾔，它的源码都是以名⽂形式存放的，不过我不认为这算是⼀个缺点，如果你的项⽬要求源代码必须是加密的，那你⼀开始就
不应该⽤Python来去实现。
  - 线程不能利⽤多CPU问题，这是Python被⼈诟病最多的⼀个缺点，GIL即全局解释器锁（Global Interpreter Lock），是计算机程序设计语⾔解释器⽤于同步线程的⼯具，使得任何时刻仅有⼀个线程在执⾏，Python的线程是操作系统的原⽣线程。在Linux上为pthread，在Windows上为Win thread，完全由操作系统调度线程的执⾏。⼀个python解释器进程内有⼀条主线程，以及多条⽤户程序的执⾏线程。即使在多核CPU平台上，由于GIL的存在，所以禁⽌多线程的并⾏执⾏。关于这个问题的折衷解决⽅法，我们在以后线程和进程章节⾥再进⾏详细探讨。

## python解释器
 > 当我们编写Python代码时，我们得到的是⼀个包含Python代码的以.py为扩展名的⽂本
⽂件。要运⾏代码，就需要Python解释器去执⾏.py⽂件。
由于整个Python语⾔从规范到解释器都是开源的，所以理论上，只要⽔平够⾼，任何⼈都
可以编写Python解释器来执⾏Python代码（当然难度很⼤）。事实上，确实存在多种
Python解释器。
- CPython
当我们从Python官⽅⽹站下载并安装好Python 2.7后，我们就直接获得了⼀个官⽅版
本的解释器：CPython。这个解释器是⽤C语⾔开发的，所以叫CPython。在命令⾏下运
⾏python就是启动CPython解释器。
CPython是使⽤最⼴的Python解释器。教程的所有代码也都在CPython下执⾏。
- IPython
 IPython是基于CPython之上的⼀个交互式解释器，也就是说，IPython只是在交互⽅
式上有所增强，但是执⾏Python代码的功能和CPython是完全⼀样的。好⽐很多国产浏览
器虽然外观不同，但内核其实都是调⽤了IE。
CPython⽤>>>作为提示符，⽽IPython⽤In [序号]:作为提示符。
- PyPy
 PyPy是另⼀个Python解释器，它的⽬标是执⾏速度。PyPy采⽤JIT技术，对Python代
码进⾏动态编译（注意不是解释），所以可以显著提⾼Python代码的执⾏速度。
绝⼤部分Python代码都可以在PyPy下运⾏，但是PyPy和CPython有⼀些是不同的，这就
导致相同的Python代码在两种解释器下执⾏可能会有不同的结果。如果你的代码要放到
PyPy下执⾏，就需要了解PyPy和CPython的不同点。
- Jython
 Jython是运⾏在Java平台上的Python解释器，可以直接把Python代码编译成Java字节
码执⾏。
- IronPython
 IronPython和Jython类似，只不过IronPython是运⾏在微软.Net平台上的Python解
释器，可以直接把Python代码编译成.Net的字节码。

python解释器+lib(内置库)+pip包管理器
可扩展性
## pip包管理器
mac里面python自带easy_install的，最快的应该就是在terminal里面sudo easy_install pip
pip 是 Python 包管理工具，该工具提供了对Python 包的查找、下载、安装、卸载的功能。
```shell
$ curl https://bootstrap.pypa.io/get-pip.py -o get-pip.py   # 下载安装脚本
$ sudo python get-pip.py    # 运行安装脚本
```
注意：用哪个版本的 Python 运行安装脚本，pip 就被关联到哪个版本，如果是 Python3 则执行以下命令：
```shell
$ sudo python3 get-pip.py    # 运行安装脚本。
一般情况 pip 对应的是 Python 2.7，pip3 对应的是 Python 3.x。
```
pip install
pip list
pip uninstall
升级包 pip install --upgrade SomePackage
升级指定的包，通过使用==, >=, <=, >, < 来指定一个版本号。
卸载包 pip uninstall SomePackage
搜索包 pip search SomePackage
显示安装包信息 pip show 
查看可升级的包 pip list -o
注意事项
如果 Python2 和 Python3 同时有 pip，则使用方法如下：
 Python2：
 python2 -m pip install XXX
 Python3:
 python3 -m pip install XXX

pip freeze > requirements.txt // 将项目依赖的包输出到指定的requirements.txt
pip install -r requirements.txt // 使用pip安装requirements中 的包
python -m pip install upgrade pip // 升级pip
## python发展史
- 1989年，为了打发圣诞节假期，Guido(⻳叔)开始写Python语⾔的编译器。
Python这个名字，来⾃Guido所挚爱的电视剧Monty Python’s Flying Circus。他
希望这个新的叫做Python的语⾔，能符合他的理想：创造⼀种C和shell之间，功能
全⾯，易学易⽤，可拓展的语⾔。
- 1991年，第⼀个Python编译器诞⽣。它是⽤C语⾔实现的，并能够调⽤C语⾔的库
⽂件。从⼀出⽣，Python已经具有了：类，函数，异常处理，包含表和词典在内的
核⼼数据类型，以及模块为基础的拓展系统。
Granddaddy of Python web frameworks, Zope 1 was released in 1999
- Python 1.0 - January 1994 增加了 lambda, map, filter and reduce.
- Python 2.0 - October 16, 2000，加⼊了内存回收机制，构成了现在Python语⾔
框架的基础
- Python 2.4 - November 30, 2004, 同年⽬前最流⾏的WEB框架Django 诞⽣
- Python 2.5 - September 19, 2006
- Python 2.6 - October 1, 2008
- Python 2.7 - July 3, 2010
In November 2014, it was announced that Python 2.7 would be
supported until 2020, and reaffirmed that there would be no 2.8 release
as users were expected to move to Python 3.4+ as soon as possible
- Python 3.0 - December 3, 2008
- Python 3.1 - June 27, 2009
- Python 3.2 - February 20, 2011
- Python 3.3 - September 29, 2012
- Python 3.4 - March 16, 2014
- Python 3.5 - September 13, 2015
