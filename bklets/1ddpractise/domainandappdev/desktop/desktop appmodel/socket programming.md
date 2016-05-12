Socket programming
=============

套接字提供的接口是有限的,就像系统调用是用限的一样,但所有的基于OS上的东西都是由它发展起来的,所以,接口,这个东西,在最初期,是越小越好.正交性.这也是unix的一种哲学,从内核支持tcpip(在编程上实现tcpip协议),再到实现编程层的支持(socket),socket建立在tcpip之上,一定要注意这二种关系.前者是网络协议,后者是一个库.

socket is not just rpc only ,,but a way of lpc
socket as lpc is like memeryshare way

tcpip跟客户端服务端的区分无关，，它是底层的连接处理，应用层，应用成客户还是服务，它并没有一个框架性的东西或基建

>socket与tcpip没有必然的联系，比如websocket可以也是一种socket,所谓socket只是一种方便编程(这里是网络编程)的软件抽象而已。在编程中，每种协议，都可以绑定一个socket，进行通讯。。

整个TCPIP协议组中，我们用得最多，接确得最多，可能未来也会接确最多的二个协议是TCP和UDP，因为它们用户级的

socket的加入,区分了二大unix的流派.bsd unix出现,socket最初是为了IPC,所以它被做成类管道的东西,,一个二头都需要接上才能通信的抽象,即插座.

>所谓抽象，就是使之变得“像”某个现实存在物或概念，你可以把抽象理解为“使之形象或意象”，关键是这个象字
socket编程跟IO编程从来同袍共母 ，网络编程的技术点在于io和协议工程。





tcpip中，用协议来构造应用，填补七层的抽象，协议作为内抽象也作为应用层的外产品，底层是各种算法，安全啊，传输控制，比如TCP不仅是一种协议，这个名字也表示它底下的程序实现是传输控制类算法

联网程序,服务器协议工程
-------------

协议工程就是像是应用层的协议FTP一样，一般地，如果制造一个网络程序，在客户端和服务端要定义一套“消息协议”，这就是协议工程。不过是应用级的。跟实现级的TCP/IP协议处在内核级的是不同一个层次的。


网络节点交互的模型再抽象（协议，或高于协议的整个软硬件模型），，在底层都是封包流动逻辑，，所以，比如在一个net gameplayer中，具体到move，commands这样的交互逻辑，在底层实现上，都是作为协议实现的(基于udp的子协议)。再加上具体协议的封包表示加处理逻辑，无一例外

Socket
-------------

Socket是一种编程抽象,即套接字(它本身无客端，服务端之分),它支持包括TCP/IP在内的多种协议，是一种多协议API。我们的网络,是一种非中央集权的机制,二台机器要在网络中建立一条连接,一开始并不存在谁是服务器谁是客户机的概念,只要在一台机器上实现了TCP/IP网络,那么它本质上就可以当成一台internet上的服务器或客户端(当然,按照使用惯例,人们往往用高配置的电脑作为服务器接受来自各种不确定客户请求,而用日常使用的PC作为访问者,相比之上,访问者寻找服务器并访问它这个过程往往是确定的),从这里开始,才出现服务器和客户端的分别,一般是先由客户端主动发出针对面向某个实现了TCP/IP并在它某一端口实现了waitting的服务器的连接,一个连接必定包含作为CS二方的地址和端口,这些就是一个套接字.它描述了建立连接用的设施.

network programming
-------------

udp和TCP都可以作为传数据的协议这方面是无差别的，高底协议可以调用它们传数据作更高的协议抽象

network programming的主线抽象，无论是在低层(common network programming)还是高层(game networking programming)，都是 
connecting,more advanced connecting,transferring,more advanced transferring（至于你要把它实现为自定义的协议或不那样做，这是程序外的考虑）

network programming focus on socket programming,socket programming focus on interexchange programming(an type of io)

ftp,http是应用网络的schedma，应用网络的语义，即二个端点交互的语义，，就跟sql作为db持久领域的存取语义一样

sql是how to use db,,,http,ftp是how to use socket

network programming engine
-------------

完善的网络库要涉及到concurrency architectures(为连接作并发和池存储处理)，event demultiplexing,protocol stacks，raknet core中除topmost game sepfied network logic外其它也跟ace 这样的通用网络库没区别

传统TCPIP只把节点当抽象文件一种IO设备，这方便UNIX等OS将它与本地的IO设备统一看待。可是把节点当设备，交互当IO，OS当网络OS，这就固然缺少一种真正强大的OS之外的应用层的网络模型和网络开发模型，我们知道它仅是socket，甚至并没有一个network mgr system。p2p engine(这个network peer engine并不是指网络上的p2p，而是指基于tcpip socket之上的网络开发引擎，真正的p2p在分布式开发介绍一节中会讲到)就好比应用层之于dbms对于持久的管理

其实，ace,raknet,enet中对于uniform udp,tcp的封装都是p2p的(peer engine)，，都是为socket提供一个封装库，以进行更高级的桌面级网络开发


路由协议DNS，这些东西只能代表有限的节点逻辑，和节点交互逻辑(比如在IP层以下，我们就不好控制TCPIP了)。而p2p，就是在应用协议层，来重新提出一个“逻辑上的，基于节点的抽象分布式系统”，或者说来强化，TCPIP这方面的能力，与其让TCPIP和internet来做节点的OS，不如让这个抽象的分布式系统来做。


高级网络开发的本质精神是什么？最终要提供一个什么样的领域框架？还有高级数据库开发呢？能不能去掉或下移该死的sql到用户级。
是connector,reactor 吗，就像a c e 做的那样


本地程序微端化框架，中的，协议设计，，应是服务器设计，，注意，这种服务器不是指网络服务器，，也并非组件的进程服务器，，，而是超越了这一切的logic servers协议设计，，，无所谓必须用网络协议还是LPC，RPC实现，，，反正它是一种IO协议规范。


  