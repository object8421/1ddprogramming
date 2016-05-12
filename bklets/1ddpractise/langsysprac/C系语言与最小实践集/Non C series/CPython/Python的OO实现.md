/*!

\page Py的OO实现

============= Py的OO实现

要明白py这类VM+BYTECODE语言系统的主打精神，那就是，它们对待源码文本（编译时，运行前）是静态的，而对待执行编译后的字节码（运行时）是相当自由的，这种二皮脸特性常表现在，它们往往是静态代码结构，静态词法作用域，加动态执行结构，动态名字空间。

作用域指明了约束－或称约束发生（一个名字与它背后所指事物的对应关系）所在的范围，采用静态词法作用域的语言如py,往往用约束所在的源码行跨度表示作用域，约束往往基于赋值语句被建立，其后，它的意义不断变化。是词法层面动态的。不是绝对绝对静态的。

名字空间是名字基于作用域效果后在运行期表现的动态约束行为（py中主要使用动态名字空间找名字，因为名字是py在运行期唯一能找得到的东西），它并不局限于源码表示，而有它所属的动态运行期的活动表示（判断名字之于名字空间的所属性依赖于此），这就是执行践。Codeframework

践背后的函数调用关系是递归的，践间相连（as datastruct）的内存结构却是链表的。故每个践都是一帧帧的（在总体的践空间增长或消减－这个践空间指os为程序模型分配的用于维持践帧活动的内存空间－可能链很长，并非帧内空间）两个动态指针指示当前践帧（只有一个）所在总体践空间的位置

py虚拟机执行模型主要靠由践空间（活动执行场地）内含代码结构（静态编译时获得的字节码序列）的方式组成，然后，在不定的运行时逻辑驱动下，不断对情景依赖的名字约束求值（编译时代码结构中，已包含名字空间逻辑。），完成名字的挂接，于是，名字处理这个意义下的所有工作得于完成。


PY编译器跟其它冯氏类型语言编译器的区别在于它一开始就在内部用OO来表达类型,是OO的编译器,比如内部的类型都是用OO表达的,所以开发中也充斥着纯OO的味道,当然,这种OO本质是C的动态类型系统,所以不要跟一般的OO理念混淆,甚至编译器方面的OO跟开发中的OO也是不一样的,编译器方面的OO一切即objects,这就是说,在编译时就存在了,所以在编程时也决定了它纯OO的开发理念,不过,objects这个概念是严格优于 class的,编译器是用C的objects来开始构建整个type系统的,是一种meta type,即类型的原型(不叫类型的类型是因为我不想混用它),它是所有型的本质,即只是一种C的object表达的OO型.

在Python中,有二种类型的数据,value的和referrence的,List又有frozenset,tuple的和可变动的类型. 其实Python的那些数据类型是编译器内置的,是用C的代码实现的语法与语义(这就是classic class,它实际上是Python里面的struct).所以它跟真正的库意义上的类型都不一样(它们是new style class)

要注意,Python中OO的你一定要跟C++的OO这样的声明语言分开,**Python中的class是object,是一个value而非一个interface,而c++中是一个interface而非object**,Python中一切皆对象,只有极少数的东西是类,比如元类




python lib

当有一天你转战到py下，你会发现那里的开发动不动就是利用某个框架，如web框架，模板引擎框架，这是因为这类语言本来就面向领域适应， 
专门性很强，集成度很高，这根桌面开发库各自为证，且针对不一，是不一样的 


PY的应用都是作为sitepakage存在的。 这符合linux等操作系统作为面向开发者的特点，迥异于windows把什么都做成面向一般用户的特点。

由于py是把源码当库，再把库直接当应用（连发行包都省了）的语言，所以，从cpython到py本身，存在很多跨语言跨库（横在它们中间的是薄薄的封装层）进行互操作的手段和途径，比如，甚至可在PY中操作字节码的生成，执行。查看执行饯信息。

py有web framework,game framework,等等，基本上，那种既当爹（开发用的库）又当妈（又能作为应用）的角色（一句话，库即应用），就是框架。人们可以在这个框架下直接开发应用，避免无用劳动。




------------- Python的类型系统:动态类型与动态代码



对Python这类动态语言来说,名字的意义远比其对C这样的静态语言的意义大,因为名字是Python在运行时能够找到其所对应的东西的唯一途径. 特别是python有名字空间的设施，一个对象的名字空间中的所有名字都称为对象的属性 。

首先,类型无须声明再使用,不必再出现int myintvar;这样的东东了,因为变量可以直接脱离声明(编译器才需要声明获得类型信息)而被定义出来,而运行期的变量一定是某个类型的某个值对象,所以可以直接用. 其次就代码结构来说,类的方法成员等可以在运行期被替换..
在Python中,赋值语句(更确切地说,是具有赋值行为的语句)是一类相当特殊的语句,原因很简单,它们会影响名字空间[1. 名字空间与作用域似乎都指某种空间,准确的说法是“名字空间的作用域”]. 而名字空间就是与作用域对应的动态的东西,一个由程序文本定义的作用域在Python程序运行时就会转化为一个名字空间,一个内存中的 PyDictObject对象.也就是说,在函数f执行时,Python会为f创建一个名字空间,这一点在以后剖析函数机制时会详细介绍.
对于作用域这个概念,至关重要的是要记住它仅仅是由源程序的文本决定的，即所谓的词法作用域.在Python中,一个约束在程序正文的某个位置是否起作用,是由该约束在文本中的位置是否唯一决定的,而不是在运行时动态决定的.因此,Python是具有静态作用域(也称词法作用域)的.
这就导致了一些分辩上的问题,比如对某个声明或代码结构所处的作用域的分析要首先判断其处于编译期(词法范畴)还是运行期的,因为这二者对同一个声明会产生不同的结果(有pyc的pvm码作证,pyc有二重意义,py c语言实现,或pycode byte)

名字空间是一组字典,可以用del删去某个名字.对名字空间里名字的引用都是在这个字典里查询一个记录的动作.它是静态的,而作用域是动态的,任何时候,都有一个相对的三个作用域的组合.

作用域代表找名字的规则.任何时候,程序的执行流都会产生三个作用域(本地,中间和最内),在某个作用域里找到某个名字,叫做“名字在那个作用域进行了一次binding”

模块是程序的逻辑单位,内置模块,内置名字,内置对象,内置函数,都在interepter启动时可见,被放在一个叫__main__模块的地方(它包含业已被引入的sys modules),虚拟机找寻任何一个函数,包括该函数中的任何数据和状态,进入虚拟机时,虚拟机都会为其分配内存初始化它们和它们所在的模块.在这个函数发挥作用的整个过程中,又要为它们维护引用计数.以及产生一个异常系统.

但是,有时,在欠套作用域规则(scope stack)中,最内欠套原则不但用于判断是否可见,当内外出现“重复名字”的时候,它还要能处理“屏蔽”其中一个.实际上,这二个问题,都是一个本质: 即要判断内外二套名字中,谁更优先,只不过当名字发生重复的情况下,需要去用一方屏蔽另一方而已.

动态作用域,就是那些词法和静态语义不能表现的,用动态语义呈现出来的关于作用域的逻辑.

也即,编译期,也就是形成中间字节码之前,只是把常量跟字符串这样的东西,和简单的类型信息编译到了中间码,更多的动作需执行引擎来处理.
在cPython实现中,那些实现机制会影响到Python后来的编程方式.这是很自然的道理.CPython在实现中用到了hash建立 Python的dict(而且在一些语言机制的实现中,直接用到了dict,比如下面谈到的赋值),用c的某些东西实现了Python对象的多态,等,这些都会由因而果到延续到Python后来的编程方式.

比如“def f()”也是一个赋值语句,它的作用是首先创建一个函数对象(参见剖析函数机制的章节),然后将这个函数对象“赋给”名字f.
在赋值语句被执行之后,从概念上讲,我们实际上得到了一个(name,obj)这样的关联关系,所以说,Python在语言实现里就采用了高级的概念(数据结构的关联),一开始就用高阶的概念穿插起了代码,所以在后来的Python编程中,也会涉及到这些高阶的概念,因为这是它的实现..

###### 动态性

Python模拟了函数式编程,和实现了一个OO,由于Python强大的内省能力,它可以动态改变程序元素(type,udt class,module)的结构,,比如替换类方法,当然,这全部都是在运行期完成的.

总之,派森动态性主要在三个方面: 一,变量不声明二,内省三,单行函数lamada etc..

内省就相当于C++的rtti,它提供动态能力,即运行时的那些可变动性支持以什么样的方式和逻辑编程的能力.

当然内省是一套机制,而非Python的一种机制.它侧重指执行系统的功能,而且是一种给于py编程的服务.

###### python OO

Python的OO系统是它特有的,就跟C++也有它特有一套OO一样,Python的OO系统的二大支柱和特点是1,元类系统,2属性优先级系统,我们先来说这个元类系统:

在 cPython中首先在C的层次实现了一个动态对象系统,它的对象全部继承来自pyobject*(我们知道cPython用c的指针把 pyobject*实现成为了一个泛型指针,于是它可以多态地表示一切从它继承的对象,这也就是Python“一切即对象”的开始源发之处,一切子类都可以通过调用它获得一致的pyobject*结构,当然这不同于“C++中严格的多态”),包括那些用来实现cPython自身的内部对象都是从这个 pyobject*对象,这个pyobject的C原型非常简单,只有短短的几个成员(它只完成描述性的信息和引用计数功能,基类Pyobject通过它的一个成员字段决定它的子类会是什么具体类型),大多数的事情全部被分配到了它的子类,比如 pyintobject,pystringobject,pyListobject,pydictobject, 如果说pyobject就是泛型,那么它的子类们就是某种具型了

以上都是型,当然还有cPython的内置型比如pycodeobject,它们不跟pystringobject等是用来被使用的,而是用来实现cPython本身的.无一例外地,它们都泛来自于pyobject.

基于以上这些型,cPython运行时能支持的对象有:数值对象(int,float,complex,long),内部专用对象 (buffer,type,frame,code,cell),容器对象(List,dict,string,tuple),复合型 (class,function,module,file,method)

Pycodeobject在python中有对应,即code object和codeop模块,peephole这样的东西,也用codeop进行优先,所以,peephone是python的模块?

Pyframeobject在python有对应,即frame object和sys.__getframe()这样的东西

Pyint

**元不是类的类型,而是类的原型**(此时没有type,即类型的概念),实际上,在现实生活中,这些都是被混用的,类,类型,原型,都是被混用的,但是,在这样的一本书里 (origanized programming basics),我将严格从字眼中去指代它们,以使读者能不混淆这三者,我想,在没有实践的初学者面前,这是唯一好的向他们说明这三者之间区别与联系办法.
首先,我们要分清,类和类型,我们用class表示类,用type表示类型(其实类型是没有引入UDT系统之前的语言用的,那时,所有的东西,都是类型,在引入UDT系统后,用class专指那些OO中派生的类型,python统一了type和class,c++ template,中,typename和class可以混用,,在这里,我们严格分开这二者,以后谈到类型的时候,用type,表示这是一种语言内置的简单类型,或语言内置的UDT类型所派生自的class,用class,专指,在语言外,使用的UDT类型)

而class和metaclass,我们称metaclass,实际上是metatype,是类的原型(这里将类改为类型,或原型改为类型都严格不能),

我们发现在python中有一个class myclass(object)这样的东西.换言之,这个object是python级的.它在cpython src中的对应是pytype_object

从过程式到OO,如何自然相连,在某种语言的历史上,到底提供了什么样的方法来过渡

python 中的类是第一级公民的元类吗?它的property是不是元属性???python怎么样达到一种跟template一样的元编程的范式?它跟范型编程有什么相比之处?难道由此可以发展出python独有的元编程技术?或者由python可以很容易实现一个设计模式体系?用python的List实现数组之类的东西,是不是有些“过设计”的味道?

python中类方法导出为普通方法,静态方法根本就可以当一个普通方法使用

A property is always a data-descriptor, but not all arguments are required when defining it.

data-classes

其实,内置类型str,int,dict,List等的类型,是metaclass,在python shell下打入:type(int) 会出现type,type,这即是metaclass,

>如果我们在py3.0以上的版本中打入type(int),会出现class type,这说明,class这个词本来就是表类型的意思,只不过它是udt的type,__class__可以返回一个对象的类型,__bases_-可以返回上层类

以上说明,这些动作首先是发生在python级的,内置类型int的类型(type)是一个叫type的类型,这说明,在内置类型上面的这个类型,是不是python中最顶级的类型呢,的确,它是然而,它不是python级,最顶点的对象.在python shell下打入type(object) 会出现type,type,这即也是metaclass

这就是说,metaclass是metatype,即统一了简单类型与udt类型的综合类型,meta,是综合类型,metatype(metaclass), object,typeobject,classobject,是四个层次(它们是isinstance也是issubclass,因为所谓派生与实例化,本来就是同一个概念的不同意义,在编译器看来,都是从数据模板到具体数据,即从抽象数据到具体数据),metatype从上面对应着 typeobject和udttype object即classobject,而meta,才是一个真正的类型,其它的三层是用object模拟的类型,(它们是对象,却作为类型的意义存在).

可见,int,str,dict,List等与object并齐, 你可以这样理解,在python中,一切都是对象, 连类型都是对象,对象这个东西object(它提供最最通用的关于数据模板的定义,甚至为class提供模板),是优先class的..即在python 中对象是优于类型的,,唯一例外的,是那个最顶层的类型metaclass…故,python中其实只有一种真正的可以不是对象意义的,独立的类型,即 metaclass

新风格的class是这样定义的,,class(object),旧风格的是这样的object.class 对pycodeobject,pycodeframe的讨论起,我们就进入了执行引擎的内部.这首先要谈一下Pyc的结构,它保留有经编译后持久化形成后的全部静态信息.因此讨论时是一个很好的参考.

后续..

>Todo:这段移走饰符函数是一种descriptor对象,这意味着函数的类中实现了__get__操作.函数还有类? 千真万确,在Python中,所有的一切都是对象,所以函数也是一种instance,它的类在Python的源码中对应的是 PyFunctionObject.通过下面的代码,我们可以观察到这个PyFunctionObject确实是一个descriptor.

------------- python的OO(1):metaclass类型系统


dsf

------------- python的OO(2): 属性方法分流机制


属性机制:

属性的分流,是python独有的OO的第二部分,property attribute(它们只能是方法method,回想一下c++,java中的get(),set()),data attribute--------**set(),get()来源于“冯氏函数，就是对内存的副作用修改器”这个事实，get,set是属性机制抽象可始由作为对象一级附属的地位慢慢提升上来为一种更高地位的表现**,这些都是python中的属性,对于这些属性中的一种,某一个class都有mro属性显示其多继承时的找属性顺序. Python 对待它的data attrib和function atrrib的方式在__dict__查找方式上是不一样的.如果由一个类定义出一个对象,从这个对象的字典里查找一个key,如果这个key的 value是个数据,那么这个对象和它的类的字典里都有这么一个数据.它们共享着一套数据.

而对于function(它们最终成为某种 bound or unbound method,注意方法跟函数不一样)对象和类的字典里并不共存着同一个东西.因为bound和unbound的存在,有时在类里存在的函数并不能被独立作为一个method,而所谓bound,和unbound,其实只是有没有从中定义出对象的问题,,,所以,function要独立成为method, 必须从它的某个对象去获取..这就是所谓的mro

在单继承下,找属性有其一套法则,多继承下,涉及到多个bases,也有,,二种情况下的实质,是对object,class,bases中的__dict__中进行排序,选择的结果.

property attributes,(注意,property只有新风格的类才有.)从这种说法中,我们可以看到,它是一种特殊的属性,
而 property又是用descriptor实现的,它是编译器内置的descriptor,作用为:link an attribute to a set of methods(也即fget,fset,fdel)所以,只有属性arrtirb和property才是真正存在的东西,所谓descriptor,只是某种“借助它,可以将属性链接到特定方法的手段”,descriptor是中间临时品,三者的关系就像欠套函数,闭包和decator一样.欠套函数和 decator才是真正存在的东西,闭包只是实现用的“踏脚石”

Descriptor是那些实现了__get__()方法的对象,调用这个descriptor的__get__方法,可以从中找到(它链接的)具体的函数对象attrib(形成为method)..从一个类的函数(它们关乎一个descriptor但不是一个descriptor,这使得从这个类派生的实例,查找它们的data和查找function attrib的__dict__时显示完全不同),,这个类的字典中只包含跟这个函数对应的descriptor.它有一个__get__方法,但是从 __dict__中并不返回这个descriptor本身作为一个bound or unbound method(因为它终久不是函数attrib本身),而是调用这个descriptor的__get__方法,找到具体的函数对象..注意,,函数本身并不是descriptor

------------- duckingtype


duckingtype是一种基于OO的语义类型，跟advoo一样

Duking type:强语义类型和导出类型,而非编译器的一级类型,基于原型,实际上仍是OO的一种变体,面向接口,切口编程,也是如此.

在一门动态类型语言如Ruby,Python这样的应用语言而非系统语言中,可以很容易duking type(利用动态类型实现糖衣类型),C++那样的虚表机制实现运行期多态是不需的,因为duking type这字眼已经是多态了,而且接口继承这样的东西根本是没有的,因为在Python这样的语言中,根本就没有对类型的声明.

**ducing type实际上是要避免的tricks**


这二种技术,语言本来就有的,就叫builtin type,扩展的类型或设计手段,就叫ducking type.

*/