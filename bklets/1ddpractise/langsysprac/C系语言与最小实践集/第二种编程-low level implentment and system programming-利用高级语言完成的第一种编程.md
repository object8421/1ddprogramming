第二种编程 : low level implentment : 利用高级语言完成的第一种编程
=============

用户级的IO及多任务并发，系统实现中的，系统空间的IO及并发，，要分清内核空间与用户空间的区别，进而带来的系统实现和系统开发的区别。

>当实现我们自己的操作系统时,如果按照历史做法,我们也需要先实现一些std c lib中的函数,比如malloc,printf等等,因为std ansi c lib的各种实作品,都不是跨平台的，而且都是内核用的，不是用户程序用的,其实这个说法有点混乱,std ansi c lib的确是跨平台的(但仅限于已知的那些平台windows,unix,linux等等),也就是说,它的跨平台不是绝对跨平台,只是相对意义上的,这就是跨平台的真正意义.而如果你要开发自己的操作系统平台,自然不属于已知那些平台之列,自然要实现自己的malloc,printf等等(假定你是开发一个OS的那些历史做法来做的).

>一般地,我们实现一个新OS时,我们采用pure C,用软件上的虚拟机虚拟一套硬件环境,再开发一套会编环境,最后采用或发明高级语言开始写书OS.

以上是基本的流程.



<table>
<tbody>
<tr>
<th>
标题</th>
</tr>
</tbody>
<tbody>
<tr>
<td></td>
</tr>
</tbody>
</table>





------------- hardware contrl


对系统初启的研究,任何对于操作系统核心进行讲解的教程,都应从这里开始,这样,可以发现一些隐式,但十分有利于我们明显化了解某些大局方面的事情.OS常驻内存,跟一般病毒的原理相当.

启动CPU,Booting机器






------------- 第三种编程- 应用编程 low level IO Programming


IO首先来自于平台，下面细述之

在硬件上，冯氏机，就是内存加CPU组成的计算系统，IO系统是由除非CPU加内存组成的内部系统组成的那些PC外部系统。(IO由CPU代理由CPU负责，由IO硬件发中断)，，DMA的出现，使IO硬件与CPU直接通讯。

硬件上用IO位图处理IO请求的优先权，以达到实时效果。

>>这种系统就是冯氏系统的本质，即内存修改器和IO进出器。这也影响了PC下的编程，其并发问题和优先级处理过程是不可缺少的（因为要并发，所以要处理优先关系，因为进入计算中心同时只有一个-------后面我们会谈到软件上的假并行），无论是用户程序对硬件功能的扩展（我们还没有谈到软件），还是平台内置的IO规程，还是它们相互之间交互，都存在这种过程。而且，无论以后在哪个层次，，都会遇到IO的并发和优先处理。

当PC强大起来的时候，它有了更强大的保护模式，可以对IO和进出CPU的计算实现保护和控制，，因此出现了软件系统，即OS。IO的种类变得尤为复杂化了。

OS隐藏了物理内存，给用户空间的应用程序和应用程序开发者一个虚拟的4g视图，，一般地，我们用系统开发语言开发基于系统之上的应用。。语言的后端(有一个内存分配器)或你使用的某个库（提供了内存分配方案）替你要OS讨要内存，，代为一个代理者，，当然，由于内存是用户空间的资源，语言标准库和后端也好，第三方库也好，，，其向OS讨要内存的权力，和要选择的方案都是平等的。。都可以在自己的开发层次定制。。


操作内存,实现一个内存池

对一段大内存，如何利用数据结构加算法的手段让它更有效地被利用，是发明一个OS（内存管理）到，普通应用开发（如实现一个对象系统，STL中的分配器）都要涉及到的。

缓冲池,往往是对于数据结构的缓冲.

io 的stream化是很重要的，这样就不需要一次性被载入内存

CPU体系与它的外设交互主要是一种IO，这跟PC跟PC之间的网络交互相似，也可以形成某种协议或规程，（这种协议实际上是指函数栈，不是会话协议）

同步与异步

spinlock是CPU级的策略，很费资源

信号量等是OS的策略

平台的内置类型


String IO,File IO,Socket IO,System Stdlevel IO,Lanuagelevel IO,,pooled io devices

异常的,可重叠的IO,指windows平台特有的IO机制,这跟socket结合,会产生异步的,可重叠的socket

buffer pool is a type of io device,,一个cache or buffer system往往是用hash完成的io体抽象,like a db


------------- low level schedule Programming


对多任务的讨论首先是来自多CPU处理系统的,然后才转到单任务下多线程里去的.但是对于单CPU的并发和本质上多CPU的并发,在编程层面,它们都要涉及到同样的同步语义.

Volatile原来在汇编中出现时,就是指对硬件内存的保护,如AGP内存(shadow memery),volatile是用来修饰访问硬件内存的(硬件以控制器作为它的CPU,,以硬件内存或硬件寄存器作为它的存储器与中央CPU交互,map io,当然GPU是独立有显存的,因此称它为硬件内存,,硬件缓冲),利用这个关键字可以禁止编译器对该段代码进行访问,此时,这些变量的变化是独立于程序的,它们中的内容可以显式被程序更改,也可被硬件设备本身更改.所以称它们为“不稳定的内存变量”
各种平台上的并发逻辑,,一般OS基于CPU,而应用程序的基于开发它的语言内部的并发支持,OO语言和它后面的东西,设计模式,,,,OO语言跟过程式C语言的关系,就跟Windows跟LINUX的关系一样,,他把一切逻辑都用界面来封装,人们操作界面来调用计算机的内部逻辑,但实际上,Linux的SHELL能提供的逻辑才最接近计算机的内部逻辑和强大的逻辑,CUI比GUI有着更强大的逻辑,就是学电脑的新手不够适应,因为GUI出现的更多的逻辑也就导致了,为了解决GUI问题而出现的线程问题是线程的应用之一一也就是其中一个..有人说UNIX比何比WINDOW好,实际上WINDOW就是在CUI上套个GUI,再对这个GUI做多了文章,导致了GUI之后的很多特定逻辑,而这些逻辑在CUI下根本不被考虑,,,开发中不需考虑这样的逻辑..
从开发者的眼光来看,整个OS kernel,就是完成一个由内核支撑起来的用户空间,对于用户程序开发者和内核程序开发者来说,它们手中掌有的资源是不一样的(用户程序开发者以内核的逻辑为基础,而内核开发者,只以“语言”为中心,甚至malloc()都要发明),,比如发生在这二者交界处的联系点sys call,这是由int 80中断到实现在内核中的某些例程,对用户程序开发的支撑.还比如,对于内核线程,它在内核级就有调度,这要跟用户级的多线程区分开来,因为用户级的程序,大部分OS默认不提供来自OS的调度支持.

Java中对线程的讲解请注意,人们说JAVA在语言级就实现了它的多线程[1. 也就是说,如果描述线程所用的数据结构是来自OS core的,那么它就是用OS原生线程支持实现的并发逻辑.如果在用户线用posix这样的库,这个库里面包含自己的对线程,同步,锁,等概念的描述,那么这种并发,是进程级的.而OS CORE是一个整体,作为机器功能存在的,不是某个应用层的进程.没有因为进程共享某个资源而带来的并发问题.],这句话与我们平常说的多线程是不一样的,,它的多线程是针对JVM的多线程,而非具体针对我们日常使用的某个平台,,比如WIN32的线程
语言对于任务,IO的支持往往被集成在它们的执行环境里,C是这样(C的库基于OS而来),C++也是这样,而JAVA,PYTHON等这样,有属于自己的执行平台的语言,是不是可以完全依赖于执行平台自身的这些功能逻辑呢?(比如Java和Python都有自己的GUI库,那么对于任务的支持呢,对于多任务呢)

并发性可用进程或线程来实现,线程被称为轻量级的进程,,一般由软件或用户来实现(当然也可由OS来抽象集成),,相比来说进程是重量级的,因此进程被用来进行重量的基于任务的资源分配等,而线程被用来进行轻量的基于函数的任务,,进程一般由OS直接抽象集成,,其实有一些软件会完全采用它们自己的进程和线程模型,,,,因为这二者在底层是依赖一些相同的东西比如长跳转,非局部跳转等机器操作.

在语言级,C和C++都没有实现一个并行库(并行库并不一定要在OS级实现),,因此很多软件都自行实现了它们(比如Java就会有它自己的线程支持),如posix api,

往往用协程来来实现用户级的并发逻辑.



>Todo:移走这里 EJB容器在一定程序上就像一个数据库(还有容器查询语言来着),,,因为容器也要涉及到持久机制,也即对容器内的对象进行持久,因此它也要提供跟数据库系统一样的持久机制,,事务机制和安全机制等等

而一个完整的数据库对于这些机制也是必不可少的(基于一个数据库系统还要处理跟线程有关的并发机制)