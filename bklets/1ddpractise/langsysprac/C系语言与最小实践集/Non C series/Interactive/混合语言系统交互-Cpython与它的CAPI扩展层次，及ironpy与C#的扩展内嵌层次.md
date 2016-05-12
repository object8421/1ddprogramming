语言系统的交互
=============

在单语言环境下，编译器与平台合作，，存在，lexals,,parsing,,interpting过程。
在多语言环境下，已有代码平台与代码（宿主与宿主逻辑），与要欠入到的代码平台与代码（虚拟机与脚本）间，又产生了一个translator过程(binding)。。


以CPP为宿主的欠入式脚本语言的发明，包括lexer,parse,translator部分，jass2 war3 api中有很多convert()s就是to jass 的native bindings,the translator parts

translator往往是no vm scripting translated to native logics



cpython or ironpy，，that is a question,,这不仅是换语言的问题，还关系到迁移到一种新的编程平台上的问题。

利用C语言写成的某语言的runtime api,可以以这种语言为hosting lang的dlr，，作no vm scripting,,其实就是extending programming

cpython较之ironpy，更适合被当成一门to highlevel native programming的glue programming和embeded programming language

cpython跟ironpy一样走系统编程和general programming的道路就不可爱了，它只应是glue 和embed domain programming language

下阶的语言不可能对高阶的语言进行extending,比如py不能对C++ extending，，只能欠入，而c++可对于py进行extending,在py中内欠CPP是没有意义的


CPy语言系统的c/py api扩展层次
-----------------------
在整个cpython src[^1]和它实现的python中,有着错综复杂的关于对象,类型,类之类的概念,我们将从字眼和它的所指,这二方面去分清这个体系:

首先在cpython src一级有pyobject*,什么时候开始,cpython src一级的对象概念已悄悄成为了python中的对象呢,比如pyint_type,对应python的type int,pytype_type对应metaclass,

>这二大体系关于它们对对象,类,类型的所指不是绝然分离的,而是很早就有了结合与相互对应的,比如python 中int,str,dict,List等对象,本身就是从py/c api中产生的,这也就是说,(py中最重要的部分就是运行时类型及它们构成的语义,它最能代表python,而编译引擎和解释引擎,其实只是一些死东西,它跟其它的语言系统没有什么很大的区别,要说有区别,也只是python的解释引擎要抽象和高级一点而已,但这些,都不能代表python的特点)py/c才是整个python的基础,python是用这一套东西实现起来的,有了py/c,我们可以构造自己的运行时类型及语义系统,你看,这不正是python扩展性的概念吗,所有这些话,等同于说,python本身,只是py/c的一个扩展 – 当然,此时的py/c不包括由python开发团队构造起来的int,str,dict,List,code,frame等python主体的东西 Py/c中最基础的部分是pyintfromlong这样的东西,然后才是整个python开发团队构造起来的由一系列类型组成的,我们今天看到的python和它的扩展体系(你该明白python跟它的扩展体系的区别了吧) 而 cpython和python级的类型很早就结合了,这成为py/c的关键,因为它的类型系统全是C的,因此,可在C级,而不是python级被扩展, 即,可以在py/c中被扩展,而不是在业已形成的python级被扩展(整个py扩展原来是从C扩展c/py,而不是从python去扩展python, 这是C的能力而不属于python语言能力).这就是为什么你在py/c中看到那么多可供扩展的内容的原因.

在python3.0中,我们键入type

>接口的转换 extending,binding,converting,wrappering,都表示语言间接口的转换。其实所谓转换，并不严格要求，按源语言的某一接口转换成目标语言的某一对应接口，有时转换成了“被改造过的接口”。所以，又可以称为语言间的接口改造。自动化的swig是多种语言间的接口转换软件（它并不作为一个库被使用而是一个工具），其它类型的软件还有tolua等，（tolua是一个库不是一个工具），，二者都靠一些“接口互换描述文件”，即.i文件或pkg文件来工作，通过提供这些文件，它们可以完成对应语言间的接口互换。如果手工来进行，那么就称为extending,不过，比起tolua来说，extending往往工作在最低的lua c/api层次，比如pyobj*级（不妨假设有一个topython），它实际上是扩展py解析器和运行时系统，而topython通过配置文件，工作在更高层而已(high level extending，运用了库的extending)。要明白embedding和extending的区别，extending是py cpi中写c的代码，还要写出一个py文件为接口文件，而embedding只需要在c中写initpy代码，然后写py.extending要复杂一些，因为要理解py capi和明白具体接口间转换的需求。

ironpy与CLR
-------------------------
clr注重clr平台上原生应用和逻辑，ironpy的扩展库注重原生的CLR，而Cpy的扩展库注重binding natvie的相关逻辑，前者是平台注重的，将任何东西都做成clr依赖的，这样可以充分发挥clr的特性，而后者不是新平台依赖的，除了语言，它只有一个native平台作为逻辑的来源，cpy作为胶水语言与通用语言，胶水语言的特性要大些

传统的托管程序与.net上对应的程序并不等价，要说转移和封装其实更是一种全新的重实现，要知道。比如xna不是.net版本的mdx,.net并没有为mdx设置一套专门的执行环境。这样的例子还有很多。net的windows和wpf是.net的gui.决不是win32 gui的.net版本。

[1. 扩展与嵌入不一样，这二者不是谁进行native programming谁进行scripting programming的区别，而是谁面向interal extending(extends innerly),谁面向exteral extending的区别(extends outterly),py/c api就是利用cpython src进行重开发的sdk,cpython本身整理得很好,这成为它本身的src能很好被用于重开发的关键,这就是对python的扩展,因为可扩展性正是python的努力的目标之一,任何一个程序,如果它以源码形式发布,其本身就是一个库(可复用的前提是能用),然而,只有经过事先设计的源码体系,才是一个真正可供更好复用的库]