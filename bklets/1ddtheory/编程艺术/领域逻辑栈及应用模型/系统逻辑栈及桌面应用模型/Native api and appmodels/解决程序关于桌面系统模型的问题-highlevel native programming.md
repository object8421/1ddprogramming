﻿解决程序关于桌面系统模型的问题
=============

纵观PC上各种语言的各种代码,都是“系统逻辑”相关的,而不是“系统逻辑”独立的,只是程度不一而已,都不可能是纯粹的应用和业务领域的事情,比如字符串(实际上既是计算机上的事物 – 编译器通过运行时表现出来的,也是人们要抽象得到的东西 – 人们用计算机上的这种概念上的“字符组成的串”表组合在一起的字符),还比如文件,既是计算机文件系统上实体,也是抽象称之为“文档或程序”的东西.

其实，桌面领域的那些东西，也是系统内核中的那些东西(不但直接使用了内核的设施，如系统调用给出的API，而且也是按内核实现的思想来进行的)，，比如用户程序级有db，，OS中的进程实现有pdb（task struct as queryable db）,数据库，，就是一个强化的语言级的数据结构，而形成的一套产品,等等

桌面领域，GUI的API通常被设计成处理对象间的通讯（一种异步IO）---不计它的MVC仅从实现的眼光看，，网络的API通常被设计成SOCKET，也是一种IO（其底层的网络硬件拓朴逻辑就是OS眼光中的堆栈IO设备），，数据库的API，，也是一种IO（建立连接，操作数据，trigger即是一种异步IO）
故，lowlevel native programming与highlevel native programming是同源的，，要掌握highlevel的桌面编程，lowlevel是必须的
其实，桌面编程，只要是native编程，不管是low level还是highlevel的桌面编程，系统知识，系统低层知识都是必须的。

桌面开发由几大领域逻辑构成，它们是DB，网络等,mfc只是app fc,而不是db,network domainlogicframework

plugin提供了动态修改或增强运行时类的功能，并深入到源码级 

native编程的最大架构特征在于将一个领域的所有抽象弄为core+plugins实现的产品体系 


>GUI问题,一方面是解决程序模型的事(而这,只是它用于应用的很小部分),另一方面,其实是多媒体开发中的“2D图形处理”

网络界面这样的东西，一方面是软件功能（它们增加了os core），一方面是开发上的接口（应用程序和桌面应用由此源发）

如果说任务编程来自对OS中cpu的调度封装之上的开发，那么文件系统与利用内存的db，则来自OS中对IO的封装之上形成的开发(是程序上的抽象，然而也是另一种更高层次上的问题，即桌面上的问题)。

系统编程是直接关系到操作系统逻辑的编程活动,比如你要开发的程序,要直接涉及到从OS获得进程,利用OS上提供的GUI原生库进行界面显示.
**虽然软件的方向可以千千万,但离不开文本处理,图形处理,数据库,因为PC的绝大部分日常应用也就仅于此**[1. 除了国防,科研,找外星人项目等这样的项目和课题, 任何应用逻辑都基于某种常见系统逻辑,因为这是计算机功能和它所做的事决定的,比如,web的应用主要是系统编程的IO和internet,socket功能,GUI抽象来源于显卡的IO,并发逻辑来源于系统的任务编程. ],Python内刚好提供了强大的文本机制和IO,对这些日常编程动作的强大支持.

学编程为什么要学系统呢?因为系统是编程产生软件的目标执行平台(术语叫宿主),比如IO实际上是一种现实系统的模型,我们现今使用在PC上的程序必须由一个CUI或GUI界面显示给用户,才能得到输入产生输出,所以IO编程其中有一种必定是处理字符的输入输出,而OS上的图形UI,又显然会跟系统的GUI子模块有关. 所以平台编程语言必定跟开发这种平台所用的语言有关联，必须统一学习 而且,所有的编程都是一定程度上的系统编程[2. 机器类型和OS类型,是一门高级语言提供它的编译器类型时要考虑的因素],即使high level开发如web编程,也要涉及到系统逻辑,因为web的东西,再怎么高级和上层,它的底层机制还是系统编程支撑下来的那些逻辑和应用.是相承的关系而并非绝对对立的东西,在后来的开发中并没有抽象到完全绝缘(换言之,PC的日常应用也就这些). 就某一种语言来说,编程中只要涉及到并发,网络,几乎总要懂得与之相关的这些系统逻辑, 即便高级语言如Python对它进行了怎么样的封装,但它最初源于基本的系统逻辑还是不变的,总得有挂起,信号量,可阻塞这样领域词汇要掌握(所以,不要指望抽象会让你学习编程的曲线下降为0). 而且,设计上的东西,无论是系统编程,还是高级编程,都是共同的. (比如图形界面和并发都是设计问题),而且它的确同时密切关系着编程和编程语言,这对理解后来的高层编程也是必须的. 深切思考GUI,SOCKET,DB的由来,懂了由来,就一定会懂编程吗?会实现应用吗,会使用API吗??我们觉得是的.因为我们明白了事情真实发生时的步骤,这就是“程序”,编程不过,重现这个“步骤” 当然,这指的是实现性编程,而这对应用性编程,也不是就没有好处. 通过本章的学习,主要是要领会(从要领上仅仅达到一个会的程度就可以了)系统的设计方面的一些东西.

学C语言的重要手段之一,是学习可以由C解决的那类问题,,而不仅仅是学习C语言本身..所以,我们在这里选取了linux core的实现.来作为对学习c语言的补充,当然,正如题目所明写的,其实我们更是在学习“由C解决的那类问题”
你看,本书大部分内容讲语言,而语言必须运行在某个系统,用语言开发又服务于系统功能的发掘与抽象,各种高阶的业务逻辑又建立在系统逻辑上.所以系统认识是编程的必备技能.





