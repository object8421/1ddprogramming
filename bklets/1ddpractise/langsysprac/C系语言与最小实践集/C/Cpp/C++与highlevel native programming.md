/*!

\page C++与桌面开发

============= C++与桌面开发

开发领域分为三种，一是系统开发，二是桌面开发，三是领域和分布式开发（框架开发）


为什么业界老把UI作为APPmodel，，为什么QT老强调它是个GUI framework胜过强调它是一个CPP general lib

------------- SDK开发与封装开发,MFC


32位的图形化操作系统Windows的出现,曾使一直在Dos下编制16位控制台应用程序的程序员们产生不小的恐慌,Windows的易用性和在Windows下进行软件开发工作的复杂性是很大的一对矛盾,在微软没有推出它的解决方案之前(前面说到,这是一种必要),程序员要实现从 Dos平台到Windows系列平台的转型门槛很高,在降价这个技术门槛的工作中,微软首先要解决的是实现应用程序的图形化界面编制,C++加API的解决方案仍然很复杂,虽然有效但却留给程序员们太多的工作,除此之外,程序员还要考虑Windows的消息机制,消息机制是Windows的内部实现,对 Windows的编程不可避免地要涉及到消息,于是,微软的工作还包括在其产品中考虑增加对消息机制的编程支持(后来我们知道微软的产品是VC++).


windows ctrl机制是一套c framework,,,消息,窗口.这跟绘不绘制无关,,窗口也有不经绘制,而有handle的..这是一种framework级的东西,,,是windows内核实现级的机制.封装它的库如mfc足够被称为gui framework,甚至language framework


------------- CPP的库与集成

cpp的标准库很小，然后它的第三方库却很多，很丰富。它们与标准库一起组成了CPP桌面应用开发体系与生态。

cpp and kde are so guity,c井和gnome vala,mono都基于gtk


cpp is nunessary when there is enough c runtimes and a language like c#，vala,delphi for appdev,and cpp itself is not high and ready enough for higher-than-desktop dev

c语言的能手，都是从开发linux，阅读linux src的历史中获得经验的，这点很显然，linux下的c级应用库，gnome系列，比kde系列要天然一点。



一般一程序离开了compiler，只要宿主运行时就可运行，可是vm类语言不同，它将编译器整合在运行时中，所以全程都是编译，可以产生类解释语言的效果，，所以解释器，也就是整合的编译器加运行时或者说，运行时编译器



也即，纯粹的解释器就是是运行时光突突的一个本身，，，，加入了编译器的运行时，就是vm

原来所谓vm的解释器，，就是将编译器运行时化啊。形成动态编译而已。。

难怪c# cls，，要提供system.runtime.compilerservices,,,interpservices这样的东西啊，，在原来cpp中分离的东西，，它把它们都给整合了。

C#，CPP到底谁复杂谁更简单，，C#有大量的库可以容易验证实践，，而CPP标准库很小，却有大量第三方库，，不能拿来就用，，本身也不容易验证实践，说到小的语法机制，C#甚至复杂性超过了CPP，，，它有PME不说，CPP有的它几乎全有，还有组件内省反射lambda。。

java,qt,.net这样的语言才是真正的语言，，真正完善的语言，因为它们的库，考虑进了平台，语言，库三重因素的有同结合。

像c#.net,netfx,这种语言，平台，库三者合一而显得模糊不清的语言系统，clr是什么地位，c#又是什么地位,bcl在整个netfx中的地位呢？system.toppest中的八大类型在bcl中的地位呢？

.net fx 原来分也分几层，bcl,,和wpf,wcf什么的。。

c#中， system.runtime应该是 system.languagetechs.xxx

gobject就相当于cmcbox linux os下的clr，，通用语言runtime。。相当于py vm,clr,也相当于better c runtime，不过它是"translator to" runtime


xx

*/