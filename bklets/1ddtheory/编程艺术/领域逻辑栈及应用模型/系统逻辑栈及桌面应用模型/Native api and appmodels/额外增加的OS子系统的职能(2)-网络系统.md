﻿其它OS子系统的职能(2) :网络系统
=============

似乎在我们一路讲到这里的时候,没有什么概念是大到可以拿来跟网络对比的(本部分小标题为“系统眼光看开发”,显然没有一个“网络是一个可以编程的系统”之类的说法),因为从编程者的眼光来看,网络,跟计算机系统对应(是分布式计算系统).
计算机系统是喝着数学和电子工业的乳法长大的，而网络是喝着计算机系统和通信工业的乳汁长大的。

网络不是计算机系统,因此它的硬件基础,跟计算机系统不一样,它的主体是资源和通信子网. 当然，我们并非研究网络本身，而是研究“具有分布能力的计算机系统”，也即，我们研究的，还是具有网络能力的计算机。作为网络通信主体的计算机系统，而并非研究计算机网络本身，那是另外一个问题，另外一个工程领域的事。

在OS的实现眼光中，，它是用IO和IO堆栈的眼光来看待对网络系统的接入的，这跟其内部的设备驱动分层分级模型很相似，因为都是一层一层地发布消息的方式，离不开消息机制和消息处理机制

以太网是物理网，对于计算机实现来说，是设备和驱动，得用驱动程序接入内核,,写进网络在内核中如何被接入，作为很多IO被接入的

整个协议 栈的分层模型和文件系统 设备驱动的分层模型类似






一些历史
-------------

计算机网络的最初模型是具有通信功能的单机系统,人们通过终端(可能是一台tty)跟主机通信.后来这个模型不断演化,成为计算机通信网(大主机模式的网络).但由于没有集成对网络资源的集中管理,这样的网络还不能称为计算机网络.

等到出现网络操作系统的时候,计算机网络的概念才成形了.一个具体的计算机网络,它在逻辑可以分为通信子网和资源子网.

在不同的历史条件下,出现过很多不同的计算机网络,由于它们的组成方式,对应OSI各层的通讯方式的各各不同,因此可以按不同的方式分为以下几种

如果按拓朴结构分,可以分为星形,总线型等等

如果按数据交换方式分,可以分为线路交换,报文交换,分组交换等(分组交换在后来成了主流[1. 分组其实也是报文,但它是报文组,所以跟报文不一样,总体上来说,数据交换方式有线路类和报文类]),当然,还可按其它方式,比如带宽分.

要注意,这个时候的计算机网络,往往都处在各自为政的情况,还离统一标准化的计算机网络比较远.所以存大大量性质各异的网络，这种状况下,没有规模很大的全球性的网络.

这些网络，就称为“局域网”(注意,局域网实际上是一种泛义,可是它又可特指IEEE制定的以太网标准),

而且,它是为教育和共享资源用的,不是为商业用的.所以这个时候还远远没有诸如企业网这样的概念.

>ARPA net[2. 现代的计算机网络技术起始于20世纪60年代末,当时,美国国防部要求计算机科学家为无限量的计算机通信找到某种途径,使任何一台计算机都无需充当"中枢".其时,美苏关系紧张,不知将来是否会爆发核大战,而防务战略家认为,一个中枢控制的网络遭到"核攻击"的可能性防不胜防,于是美国国防部于1969年出资研究开发ARPA网,该网络被设计成可在计算机间提供许多路线(在计算机术语中称为路由)的网络,这就是说，网络的可靠性在于坏了一个节点后，另一个节点的可达性](69年)一开始是internet的主干,后 (80年代初期)为了鼓动更多的网加入Internet研究出来了tcpip, 86年NFS net(美国科学界用的一种网)取代ARPA net,成为Internet的新主干,后来在90年代,又被商业化. 国际规范化组织1977提出了规范ＷＡＮ互联的要求,83年完成OSＩ(即ＩＳＯ7498),它主要解决网络互联的问题. (与ＩＳＯ的OSＩ一样,ＩＥＥＥ制定了ＬＡＮ的参考模型.ＬＡＮ的技术主要有传输介质,拓朴结构,介质访问控制mac方法 - 比如csma/cd)

为什么要先谈七层模型
-------------

ISO七层模型只是一个学术的模型和官方的标准（还没有一个一丝不苟地按照它来实现的现实七层网络），它的价值在于从学术上描述所有概念的和现实的网络模型，因此，它可以作为建设现实的某种网络模型的参考（它还是有实际价值的）和对现实某种实际网络的模型描述工具。现今主要的网络模型不是ISO，而是TCP/IP网络模型（它才是被广泛在用的标准）以及以它为基础建立出来的一系列协议规范，软件体系，硬件实现，编程接口。

分布式系统的模型是OSI七层模型，满足这个模型的分布式系统实现都可以相互通讯，作为一种完备的网络协议，它指出了分布式系统的全部交互逻辑(协议即某种分布式主体交互使用的IO模型，，使用XX协议的网络被称为XXX网，可能是另外一个名字 ---- 协议作为IO这种模型在编程上被看作是socket,这是后话)，，，而具体的分布式系统，如lan,wan这样的专用网往往只实现全功能分布式系统的某些部分，完成某些层次的交互就功成身退了（如以太网往往被用来实现局域网）。

>>lan,wan不但指出了网络的规模，它实际上也指出了该网络通常所拥有的协议（在OSI七层中的对应物。）

现今最通用的TCPIP协议（tcpip协议是一个实现了OSI某些层的协议组，TCPIP网即使用TCPIP协议进行通讯的分布式系统）是网际网协议，internet（大小写的i通常被用来区分互联网和网际网---网网互联）指网际网，即网间网，网络的网络，不要把它称为互联网，，它是泛义，学术用语，现今存在的网间网----那个由apr形成的网间网，才称为互联网(Internet大写的I)，除了互联网它还有一个名字，即公网。可是，它没有特指的代号。这纯粹是历史问题。

Global Internet是由不同协议的网络(它们往往是某种lan,wan)进行桥接形成的internets，这些internets大部分是wan规模的tcpip网。在这个层次上，需要使用路由方面的协议（如Internet tcpip的IP，，注意TCP仅是应用层的，它往往与程序员有关），在具体internets内部，可能仅是一些靠近OSI下层的协议。


也即，类似“网络模型”这种说法，是对一个网络中出现的所有东西的总概括（是对出现在该网络模型中的，软件的，硬件的，具体协议的，编程接口的一个总括）。

ISO可很好用来描述TCP/IP，如果将tcp/ip看成是“由OSI网络模型参考而来的一种OSI网络”，那么它可被这样描述：TCP是TCP/IP网络模型中的传输层协议代表，IP是TCP/IP网络模型中网络层协议的代表，相比于标准的学术的概念的OSI，实际的TCP/IP主要只涉及到其中的五层而已，即ip网络层及以上的部分：网络层，传输层，会话层，表示层，应用层，也即，支撑整个TCP/IP网络的，虽然其底下一定有物理层和数据链路层，但代表TCP/IP这个“网络模型标准”的，是后五层。
>iso网络模型描述的是一个可由软硬实现的网络体系，不是计算机体系（每机一配的网卡处在物理连接层，当然，计算机本身也可作为一切通用的网络硬件，这时，它在软件上实现了整个模型的所有重要层,比如tcpip），在软件上，针对这个模型，往往解决提供一族协议（交互细节）的问题，即协议工程问题。
对于程序员，研究一个网络和网络模型，其中关于软件的，具体协议的，编程接口的这些部分跟我们有关。

研究计算机网络，跟研究计算机CG一样，依然是对算法(出现在某一“网络模型”中所有关乎“实现”的程序，无论它是软件的，还是硬件的)的研究(所以，对计算机网络的实现讲解的技术书籍，应首先从“网络模型”着手讲解，因为它是计算机网络的最高构架，如何互联，如何构造网络应用，只是应用的问题或是一种艺术，它们都不是实现，只有“网络模型实现”，才是中心问题)，只不过有些算法，如路由算法，做成了硬件而已。posix network os一般在内核就实现了路由算法因此它可用路由器，思科路由器在硬件上实现了网络层和传输层，网络层主要是路由），一般地，tcp/ip实现在网络通信的主机内核中，以开发的眼光来看tcp/ip socket programming,它已经不属于内核开发了，而是app开发了。

OSI七层
-------------

OSI有七层，前四层跟硬件相关（可能会实现在硬件上），后四层是纯粹的软件意义上的（根本不需要实现在硬件上），TCP/IP中二个实体进行通信时，发送方从物理层开始，一直到应用层，将原始数据加上一定的处理（增加额外的成份或指令，这些东西，是TCP/IP网络进行正常通信必要的，每一层都有很多协议，它们加工原始数据，加上它应加上的成份，送到它上面的一层再待处理，完成一个“接力”过程），发送到接收方的应用层，接收方从应用层开始，一直到物理层，将收到的数据，去掉这些额外信息，得到原始数据(在接收方，也由不同层次的协议处理非原始数据，完成一个“接力”过程)。至此，整个传输完成。

一个数据从发送方到接收方，在二端经历了一个互逆过程，发送方的TCP/IP层的所有协议对原始数据的处理称为发送方的TCP/IP协议栈，它是一个层次的协议堆，接收方的TCP/IP也称为一个协议栈。它们构成了TCP/IP所有各层协议（在一端的上下层之间，和二端之间的对等层之间）的功能和。研究计算机网络，就是研究数据传送的二大互逆“接力”过程，这二大过程都有什么协议，用什么算法实现(至于它是实现在作为计算机网络的主体[3. 计算机网络自然是用计算机完成的，计算机充当路由器，充当集线器，充当主机，充当入网终端，等等，也即主体是计算机。] - 计算机的内核中，还是被思科路由器实现，这些我们都管不到，我们只需研究同一个“TCP/IP协议栈”就行了。)。

这里要说明的是，不存在“二端之间的对等层之间”的直接通信(它只是一个“看起来是这样“的虚拟说法)，通信只发生在发送方的物理层和接收方的应用层之间，二端只负责对数据的协议处理。而且是一个关于数据的层次协议的处理（因此，数据是受多个协议多次处理的），而不是二端在对等层协作，用双方同一层次的协议处理数据，然后将中间结果直接发送到对方的对等层。

>因此，TCP/IP网络中，没有真正平等的通信双方（严格意义上的p2p，没有地位的分别角色的分别，而TCP/IP中有），双方所遵守的过程一个是对数据的增加，一个是对数据的去除增加的成份。虽然共享同一个“TCP/IP实现”，但对数据的处理方式不一样。故不是平等的个体。虽然接收方也可转变角色变成发送方，但在“一次就完成”的数据通信过程中，双方盼演的角色不一样。TCP/IP中的P2P就是“发送方与接收方转变角色完成对方的事”这种意义上的P2P。TCP/IP本来就被设计成存在有管理角色的。

局域网络:OSI最低二层
-------------

我们先来看标准局域网.因为标准广域网实际上是标准局域网的网,本质上并不存在“广域网”这种实体,internet[4. interconnected network](它是一种具体网,原名叫arpanet,是它发展来的)作为一种“(国际)互联(广域)网”,实际上,只是大量局域网连到一个叫“aprnet”的局域网的现状(并且在它那里注册一个IP地址而已[5. 人们叫它公网internet,注意Global IP Internet(特指的internet),跟表示一般互联网概念的小写internet第一个字母的区别]),而实际上,并不存在internet.,广大局域网与它是地位相同的.换言之,局域网技术,才是广域网技术的主体.

>集线器连接多个机子(构成一个单位的局域网),网桥连接多个集线器构成更多单位的大LAN(此时还称LAN),路由器连接多个兼容或不兼容的LAN,构成更更大的LAN(此时不称ＬＡＮ,因为跨局域了,所以称为ＷＡＮ,广域网,或一般意义上的互联网) ＴＣＰ/IP的某个实现,是针对ＷＡＮ的(解决接入外面网络 – 主机或基本本地网络出网的技术), 一般地,通过局域网系统的主机,和不通过局域网系统的主机,它们都能出网 – 这个网指一般意义的internet外网,主机(的网卡)能通过它连接到的局域网的路由器出网　－　因为局域网出网,所以主机相应的也就出网了. 一条线路可能是没经过路由也可能是经过路由的，经过路由的可再度路由或交换（通过路由器和交换机），没经过路由的，只能在内部网使用，这个意义上,它是通过网卡出的网(路由器必然最终联系到某个网卡),另外,主机也可不依赖局域网系统(网卡和路由器)而依赖猫和串行线路出网到internet(所以Ｔcp/ip也包括独立的物理层链路层,比如slip),这二种情况下,都能出网. 前一种情况,ＷＡＮ技术(解决主机或局域网接入外网的技术)建立在ＬＡＮ技术(解决组成基本本地网络的技术)之上,一般称OSＩ是七层,tcp/ip作为这种规范的产品,它可以在概念上是6层[6. 数据链路层不是TCP/IP协议的一部分,但它是TCP/IP赖以存在的各种通信网和TCP/IP之间的接口,](最低端二层解决利用局域网卡,物理层在局域网技术内)或7层(独立于局域网技术直接由主机连入internet),但是这对OSＩ来说都是七层,所以可统一讨论(这也是OSＩ的目的所在,只要符合七层,OSＩ就透明). osi七层模型,在各层传输的数据从低到高分别为比特(物理层),(链路层)帧(也称为包),(网络层)分组,从传输层开始,是(段),这就有了网络的概念.tcp/ip就在这里开始被实现,最后才是原始数据(合并或分用), tcpip是一个协议体现,它是对OSI七层模型的一个实现,TCP,IP只是这个协议体系的一员,这种以其中之一来代称全部的称法的确有点让人混淆.但这也显示,TCP,IP是这个协议体系地位很重要的一部分. ＩＰ层的重要性和意义是因为它可以表明一个外网的存在,对于物理层的网络,它有自己的世界(以太网卡地址),当它开始出网时,它就面临着不能再把硬件地址当外网地址用的问题了,此时需要出现链路层,提供地址转换到外网互联网,或由互联网转入硬件以太网地址. 表现在数据流上,就是tcp/ip环境下二机(可能是路由器或主机)交互时,数据要从ＩＰ层开始加入或去除特定的外网地址字段.解决了名字的问题,实际上还有一个实际传送的问题,各种可能不同质的局域网通过路由器接成一个透明的internet,同样表现在数据流上,tcp/ip环境下二机(可能是路由器或主机)交互时,数据要从ＩＰ层开始加入或去除特定的同步字段(以去除各种可能的不兼容).

解决基于七层协议的局域网的问题.除了解决底层的通信子网的技术,还要解决资源子网的问题,但七层模型只是一种标准,对于各种实现品,如TCP/IP是其中一种,在各种不同的实现之间往往在1-7层的某一层会出现不相同,这个时候,解决“网络互联”问题就出来了(当然,它比前面未标准化前的互联问题要方便得多)

这样的技术,依然是提出抽象,即,在出现问题的层面提出一个中继抽象,比如在物理层提供中继器,在链路层提供网桥,在网络层提供路由器.在传输层及以上提供协议转换(称为网关).往往出现问题的层面出现在网关.

于是在可能解决以上几个层面的问题的情况下,局域网互联可以通过在网关互联,或直接通过网络相联,这二种方式有什么区别呢,实际上只是策略不同,最终要涉及到对上面几大问题的综合讨论.前者只是最直接,最直观的连接方式而已(任何情况都适用),后者是在确定要进行网络级互联的情况下进行的(它也可能涉及到处理网关)

互联技术
-------------

要互联网[7. 首先是单人相连,联机,然后发现不够,需要联网,最后是需要网联.],必然先联机(所以必然从基本的物理链路开始),形成通信网(局域网),才能组网(以下四种情况)互联成互联网.

lan-lan lan-wan wan-wan lan-wan-lan

因为局域网只是一个通信网,所以它应包括物,数链层和网络层,但是局域网任何二点之间都可以用一条直接链路,没有路由问题,所以可以不需要设置网络层,而将原来网络层的部分功能融合到数据链路层,这样,数链层就较显得功能模糊[8. 在作为抽象的软件设计中，有时不能精确地划分抽象的层次，一些逻辑可以在二层之间的任何一层或多或少地存在一些,或完全放在其中一层],但仍然可以分为二个子层,即介质访问控制(如ＣＳＭＡ/ＣＤ协议)和逻辑链路控制层.
>一个交换机只能识别MAC，它工作在那些仅需MAC就能形成网络的网络中，比如一个以太网，由于不需要一个IP地址，此时还没有IP协议，也就没有一个TCP网络。
**TCPIP网络是以其它网络以基础完成它部分对应于标准ISO网络模型的某些层的。**

tcpip是借助具体局域网技术完成它关于iso七层标准的某些层的。tcpip由ip开始。解决的是基于业已形成的网络之上构建网络的问题。是网络间通讯协议。而不是联机（联设备）组网的问题，以太网等局域网技术才是。网间网需要路由设备和统一的地址（因为不可能进入网内的设备。进行网内设备间的直接通讯）以促成网间协议。联机（联设备）仅需这些设备的mac。因为仅需要设备间的交互（交换机和交换协议）。当网络间出现断层时就不能沟通（在局域网物理网层可能有的是以太网有的是电信网有的是广播网。在网际网间有的是tcpip有的是appletalk）。由于处在不同物理网层的节点可能实现了多种协议。故它们不能在低级网上通讯。但可在高级网上通讯。
一般解决了局域网的问题就解决了网络问题(内网，网内网),但没有解决网络互联问题(外网，网际网),一般情况下有下面几种

>网络互联的方案(需要中间设备[9. 网络的硬件,不过是一些软件上协议的算法,做成了硬件而已,所以,从软件的眼光,可以看透一切.]) １,从协义的层次来看,可以把网络互联分为四层 物理层中继,物理层面向线路,是硬件链路,中继器可以处理在不同的电缆间复制信号 数据链路层－网桥,是数据链路层的互联,在局域网之间转发数据帧. 网络层中继,即ＩＰ路由器,在不同的网络之间转发分组. 传输层及其以上,网关. ２,根据接口情况分 在节点级,数据电路端,相当于在网络层或数据链路层进行互联,比如猫 在主机级,相当于在网络层以上的层次进行互联,计算机,终端都是数据终端设备 ３,网络互联的二种方法 １,直接通过网关互联,２,通过互联网络相连.

现实中,为了进入互联网,一台主机可以通过使用终端连入另一台已联接Internet的主机(此终端没有ＩＰ,所以应用起来是大受限制的),或自行通过slip进入另一台已联接Internet的主机(有ＩＰ,是Internet中独立一员).另外一类方法就是通过既有的互联网入网. (这种局域网往往用专用高速线路连接到某主干网,在局域网内才负责网内各主机接入Internet的逻辑) 当使用一台局域网服务器进入互联网时,除了这个服务器,其它的机器没有ＩＰ. 当使用路由器时(其里面的机器可以有ＩＰ). 无论是在哪种架构下,一根网线必须最终是路由了的[10. hub和switcher工作在经过路由了的网线后面，工作在连接层，一个路由=路由了的网线+hub,普通家用的hub一般都是几口的，而网吧或公用单位的hubs一般都是多口的]，经过路由的，我们才能用它上网

跟网络有关的硬件有三类,1,网卡,2,网线(称为线路媒体),3(网络设备)

路由器,不像网卡,它们是独立工作的网络设备(而网卡是附属计算机的设备),一般在谈到网络设备时不突出网卡(因为它是计算机的,而计算机是网络中的主体不是设备),而把网桥,路由器,集线器,交换机,称为网络设备,把通信线路称为线路媒体.

>osi七层协议关系,物,链,网是,网络功能,上面四层是用户功能 二机交互时,数据在一端的七层传输跟另一端是完全互反的,但是,因为OSＩ是抽象的,在本层对下面各层已被屏蔽掉了,这就给人这样一种效果,就好像二端的同等层直接交互一样.

那么,什么是使用协议的主体呢?在协议的最下面,是物理硬件,比如物理层的网卡,链路层的网桥,网络层的路由器,等等.在最上面,就是端口,应用,和进程了.