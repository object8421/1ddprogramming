
>重谈“什么是分布式”
在谈OS网络的时候谈到分布式，其实分布式在不同层次解决不同的问题。

分布式PC分布式网络分布式应用程序系统，，这三者的界限是什么。。each应包括什么有限的功能

那么我们在这里要谈的就是APPSVR，APPMODEL级别的“分布式”


>分布式问题


weakly-linked (across network boundery,process boudry,machine boudry,,各种异构boundry,by msgsys) parallel process/svr framework--------分布式的特点是弱连接。通讯双方就跟IO双方一样，都是极其不定的只靠发消息发现和加入这个集群。分布式天然就是个msg oriented sys(分布式IO天然就是个asio event oriented sys),,,so how build a appmodel for it-------io都要靠协议工作的。协议都是一种msg,msg都是一种event

整个分布式，其实就是关于各种各样svrs的事。程序上的抽象。这个svr可以是一个进程(lpc,rpc svr)，也可以是一个tcpsvr(network io svr)，，但都是msgsvr(a system dealing with presenting the procal buffer and processing the event io)-----------event:socket buffer read/write io invacation resulted notiy event mapped into appmodel eventsys domain,,,区分msg io deplex与appmodel eventsys。一个是问题本身一个可能是语言功能。这二者的映射与结合关系。

它包括cs和p2p.是对这二者的综合考虑。

所谓p2p，就是based on tcpsocket下，用户空间自主路由的一种协议栈和svr集群结构。

>分布式与消息

消 息传递指的是程序之间通过在消息中发送数据进行通信，而不是通过直接调用彼此来通信，直接调用通常是用于诸如远程过程调用的技术。排队指的是应用程序通过 队列来通信。队列的使用除去了接收和发送应用程序同时执行的要求

However, most application protocols are based on the idea of "messages";在一个distributed appmodel中msg总是based on the idea of event,,this is what libio dealt with-------tcp stream->ingoingoutgoing buffer->packet->msg


通用highlvl local/dist IO表示和IO处理 lib...t general local/dist io present and process lib:gippl


>分布式与组件分布式

组件->lpc->rpc->纯粹统一的socket-msg-like based svr appmodel.本来本地lpc是不需要socketlike msg的(idl只是调用协议不是网路协议)，但是为了统一还是采用了跟socket svr一样的msg表示与处理机制as the上层应用框架外观，统一idl与socket protal

com server or socket server framework or hybird,com shouldt come accross network boundary(or it brings lateny,and i dontlike proxy/stub,or idl lang trans binding),local com is a transport w/o protocal(vs network socket,转协议机制为通用ipc,rpc这样的例子如http->soap多了去了)----distrubted com appsvr,or distrubuted msgqueue appsvr(msg brings分布并发二层意义，GUI在应用开发层是grapch/view,,,network则是msg)msg含了com msg和network msg

so ,a question will be,,y wanna use compent based servers or (non com based)msgqueue based libs as the dustributed appmodel frk---------as i mentioned b4,com shouldnt happen across netowk boundry,so com rpc based unform distributed appmodel is not acceptable?gcf has one implentment,zeromq has impentments 2 for rpc.
--------rpc works at programming lvl(the method recovery and invocation services),not only the compentlvl.
----------com lib is exec time loadable and linkable,while common lib is compiler time loaddable or prelinked.

>分布式appmodel

msgquene代表一个分布式appmodel，，难怪。像.net的消息规范wcf-msmq，j2ee的jms。

分布式应用(inc the appmodel)的本质特征是什么，the overviews engineering fullsocpe，1，松散的客户端，2，内容表现共享。所有用户在同一套应用外观。--------tech atleast involes asio,eventsys,worker queue,mutithread,big data trans,msg serinal,msgframing,mutilsvr payload banlance/commucation,centraledsvr or p2p corpor,urliz(通用URL到底为了什么能达到什么效果),


传统网络程序开发中，将大量通讯相关的任务交给了程序员这实际上是不好的。

web开发不是socket network开发，因为它隐藏了网络开发的复杂性将其作成框架(j2ee的jboss,etc..)或者应用服务器或客端(lamp+browswer)，虽然它只有二种协议,而且，说实话，如何发消息，组装消息，如何保证不粘包，保证通讯不阻塞而且高效化，，这些服务器技术，这本来就不是用户编程管的事。应该跟web开发一样做成中间件藏起来。


tcp在物传网链会表应层，都遵守同样差不多的逻辑。。都有传链会表机制。

msg format,proctal encode,the present
msg queue,the event io process

protocol buffer 语言？？？ZeroMQ就是网络协议的sql！！将协议格式化为领域语言和领域处理机。


网络开发的业务逻辑应该不是如何搭建服务器单元和管理消息IO行为等，这些应由框架完成，而是构建具体应用密切尾端相关的协议表示和协议处理。

http,ftp协议实现@cppee不是generaldevkit中的，而是appmodel中的。

任何dist appmodel，都可以用服务器群和消息来解释吗？




>zeromq

zeromq is a userlvl tcpstack implemnt?like fuse??

zeromq has 2 layer,the socket and socketio abstract layer,,,and the msg pattern queue layer.

what about zeromq's persist for the proctoal buffer to disk?

zeromq's "m fan in n fan out" is fact the io event deplex.zeromq is based on traditonal tcpsocket but not meant for replacing it.it developt it. to "m fan in n fan out"(vs tcpsocket's 1:1)taking whole a svr a "endpoint" but not socket binding port or connecting port.


zeromq有表示层（协议表示，持久化）网络层（router），传输层（socket pattern），是用户级的network app model(protocal stack). if peers work in c/s manner then it became cs network appmodel frk,if peers work in euqal-join manner then the p2p appmodel frk.


zeromq is infact a metasvr framework，用于建那种由连接服务器（协议路由，过滤）和处理服务器构成的集群，，svr frasture framework，且创造一种cross svr comucation,load balancing和no singel point failure的效果。而这其实是用户空间的网络工程，就像内核的那个tcp protal stack一样。

连接服务器 in zeromq is the router,,,zeromq is the metasvr lib(svr's svr,,or svr based on svr),zeromq endpoint comucates not by portocals but by svr unit.

zeromq with m:n io,,,it can archives to a p2p decenternizd effect. is a server archiet framework based on a asio network lib.and a protocal marsh-customable lib(procing the msg buffer).,,,,in the biggest overall,,,its a msg framework(for msg based network appmodel).with lpc/rpc is msg based dist appmodel

zeromq在命名上突出那个msg，且msgqueue实际上很不好，因为of the biggest view,,,is a svr oriented lib.not msg oriented,msg只是其表示层的东西，物传网链会表应中的表，在整个appmodel，也是表示层的东西，not logic essinal ones.要说它重要，它可能表现在整合了lpc,rpc,network io into 1: the msg oriented present and process system,event driven distributed appmodel system

>engitor dist

libsvr:asio+wlsfasio,,wlsf:weaklinked svr frastruste,,,mixed rpc+socket linked svr fransturste, ,in engitorm2 implentment,,,in proc svrs(peered ones) will use rpc,,,,,,,,,,cs svrs will use socket ones.to bkreadmes
--------------
engitor shouldnt only be appsvr,,in fact its a os and appsvr,it includes in connectsvr,like vpnd,,safesvr like ..then the appsvr..turnning os_stack_lvl_svr to distos svr,,infact its a appsvr.
