﻿SOA与云计算
=============

云计算，和移动开发、物联网一样，也是业界公认的未来重要发展趋势之一，**是计算机工程进行到一个相当程度的综合产物**（请联系在导读什么是平台语言算法一文），它不只是一种平台，而是平台语言问题设计等的综合。






------------- web is common clouding

web不是通用云计算

曾几何时，我们直接把WEB当成了我们需要的那朵云
诚然，企业靠WEB实现了它们大多数业务需求。。分布式开发似乎非WEB莫属。

可是，如果翻开历史，就可以看到，，最初的web仅仅是为了分享资源，促进教育

。

html的发明就是最初那个WEB，，，被人们称为静态WEB的那个年代，WEB只是展示

和分享用的东西。。

后来动态WEB出现了，，，它就成了一种“WEB平台的东西”

我们知道平台这个词是重量的，，它至少是应用的平台，开发的平台，发布的平台（组件平台）。。

1,硬件平台上，应用，开发，发布，，都是以PC为主体的。

2，软件平台上（有OS的平台），以上三者都是以应用程序为主体的。

3，分布式平台上（有网络的平台），以上三者都是以虚拟机为主体的。

1，2比较好理解，3需要归纳一下。《请看我的QT救赎下的WEBGAME》


在现今阶段，，我们所指的云，，主要是WEB，而云，，它的广义，，是指通用分布式平台（应用，开发，发布），，而不仅仅是我们已经做得很好的那套ＷＥＢ。

于是，我们误用了太多东西，，，webgame,,web xx ,,web all，即使它们有时仅是表面上工作得正常。。

－－－－－－－－－－－－－－－－－－－－－－－－－－－－－－－－－－

需要出现一种全新的架构，比如，以组件为基础的分布式平台来统一云计算（比如.net vm,java中的enterprise beans），重新改良现有ＷＥＢ架构的Ｂ／Ｓ部分，使之容纳通用的云计算应用。

平台：分布式和虚拟化
-------------

iaas,paas

分布式和虚拟化指出了平台的硬件上的（较之以前机器和桌面时代）特点，云计算主要是相对以前的大主机来说的，云计算实际上是个老概念的引伸,它侧重于指服务端,而不是客户端,虚拟化和集群是一对相对的概念，虚拟化是云计算的一部分，如果说RIA是将GUI做到了服务端，那么虚拟化就是将机器分成多份做到了服务端(这就跟出现OS时，要将硬件上的机器虚拟成软件上的多份，且将计算能力和存储能力虚拟成任务机制一样)，.net就是将开发也做到了服务端，所有这些是一整套方案的迁移，所以是大架构级的的概念，这就是微软适应java造就的时代的举措(比如C井可以将大部分组件转换成WEB服务，这统一了桌面开发和WEB开发(甚至移动开发)，WEB开发可以利用桌面上的东西，这跟j2ee建立在j2se上一样)，

>云计算是硬件决定软件软件影响硬件的绝好典范（处理器水平和网络带宽都在提高）。尤其这种影响发生在计算架构上。和由比带来的开发方式和应用架构上


开发
-------------

那么开发呢？云计算下的客户端主要不是跟服务端一样的通用开发。而是领域相关的脚本编程。设计和制作。比如对于web客户端，主要是设计网页和写作javascript的dom逻辑，并没有数据库，IO等平台知识在其中。

>从开发上来讲，云客户端就是一个最终件（程序中除了可执行体外的资源部分）部署运行平台。所以它只需要强大的存储就可以了。甚至也可以不要。

>嵌入式语言的封装库少。是不是能胜任云客户端开发呢。比如3d ria,我们到底要嵌入开发图形还是通用语言开发图形

意义
-------------

使网络上的计算机，，成为逻辑上的，“一台计算机”，，就是云计算

云计算模糊了PC与终端,它倡导一种用网络来代替冯氏PC架构来进行计算的能力,未来计算资源将成为水电等基础设施而不是人手一台的带自处理功能的PC终端,(你只需用这种资源进行高层应用,不必直接掌握电能,电能本来就不必开发,,因为包括软件都是云计算所说的电,,切,而且这个电会智能为你个人定制服务,只要你一个要求,即SaaS)

实际上以上概念还不是云计算的重点,它的另一个特征是我们日常意义说的软件将不存在,人们不必为终端开放驱动计算的软件,所有的计算能力能给人类(个人或企业)的东西都表现为在internet上的服务,人们只需要一个终端(可能是不需要CＰＵ的ＮC -----以前的NC改胎换面变成了现在的云终端 ------,未来可能是ＧＰＵ大行其道的时候..当然如果云的计算能力和运输能力足够强,那么本地不必配置图象处理设备,只需配置和实现显示抽象就行了)与之交互来获得这些服务就行了(提代访问控制和个人内容),它包括二个方面,一个是富INTERNET(还提供人类知识的全集和智能计算为使用者服务的能力),一个是THIN终端