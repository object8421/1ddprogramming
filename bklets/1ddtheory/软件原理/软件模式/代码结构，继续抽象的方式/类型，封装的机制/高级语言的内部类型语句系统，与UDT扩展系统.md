

内部类型
-------------

**任何语言都有一个“类型系统”**, BCPL作为C语言的始祖(汇编语言是没有变量和类型的,类型是一门高级语言的基础,用来表示为程序所用的内存的抽象,即多少内存,可以在这个类型上执行什么操作),它是没有数据类型的,实际上一切都是抽象,C语言中的基本类型正是抽象了“以何种方式使用内存(更确切地说是使用内存的位,因为这是汇编语言和机器逻辑最终要考虑的问题,在高级语言中得抽象一下不能直接用位组)”,使用内存的方式就成了基本类型[9. 语言封装了机器的类型,就表明:它能被用于开发系统本身(硬件,或软件)作为一门系统实现语言(因此Ｃ这样的语言可用于OS开发).要分清机器的类型和语言对机器类型的封装,这二者哪个是决定性的.],这是一种抽象.类型关系到变量表示这种类型,关系到编译期类型安全和转换机制,关系到一门语言组织更大数据抽象的能力与语法特性.关系到与它相关的表达式的属性.比如赋值与表达式求值,而且还关系到代码的表达方式。
内置类型是一种语义和运行期设施.是语言能直接认识的数据及一套语义.是所有语言其它语义的基础,它的语法基础是名字声明与定义.编程就是扩展内置语义.可以产生其它的语法与语义(赋值,表达式求值,函数返回值).(类型是基于指称语义科学的,它指明一个用来表示数据的名字,与程序员能看到的程序中的名字即变量,而且它还指示内存的位置).
运行时中的类型设施是一个编译器首先要完成的事,对类型的进一步抽象是很多高级语言在做的事情,比如动态类型语言,比如类,范型,数据结构等..特别是类的提出,是一种通用类型,这使得类型不仅仅只表示数值和字符,还可以表示更抽象的概念,这种编程也叫ADT和UDT编程.这种工作甚至做到了代码层.我们将从内置类型谈到各种其它复杂类型的情况. 类型与对象数据,然后才是那些通用的语法设施[10. 在冯氏编程中,从来都是数据和类型的设计,主导语句,,这反映了冯氏机器底层是一种IO的本质,在这种IO中,指令是受数据主层的,这个我们在前面就已经讲过.所以,对于结构式和过程式是“控制模式编程,和行为编程”的说法是错误的,即使在一个C程序里,类型,类型定义,新类型产生,类型之间的语义,从来都是主体,它主导着语句.比如赋值语句,赋值行为是次要的,它影响了左值的值,对冯氏机作了一次IO,才是这个动作的主要意义.](比如语言中,都是由“类型:数据”来定义出数据,然后才在这个基础上运用通用的语法设施,比如赋值,或表达式求值)变量为对象是一种高级数据,这充分说明,PY以对象而非普通数据plain old变量为数据,简单类型对应普通变量,类类型对应对象变量,赋值类型也是用OO来表达的,跟作用域有关,一切在所有语言中都能看到的类型与语言设施,这是冯氏类型语言的通用内容,也就是说,类型,表达式,操作符,四大结构化流程语句,这是冯氏语言通用的解决方案,所有语言都是这套系统这根本上是由语言本身决定的. 为什么在一门语言中总会有控制结构,数据类型这样的通用概念呢,有控制结构是因为如果你在汇编下编过程,就会知道这其实是所有机器(比如堆栈机啊)和虚拟机进行处理的基本方式(源于离散数学的计算模型),是由硬件的指令系统决定的,简单数据类型(primate type而非oo wrapper datatype---也即ADT)是因为CPU也就只能按二进制的方式表达整型啊,浮点啊这些东东 即,语言的过程性语法是对平台的指令系统在高级语言的层面进行封装并加入自己的一些机制形成的通用语言机制. 语言的语义可以是ADT系统组成的那一整套逻辑(这样就成为ADT编程,UDT编程),只要后端支持,语义提供书写形式,程序员就可以利用这样的一门语言进行编程.

需要注意的是: 1.类型相关的表达式语句,比四大结构化语句,更能代表“程序句子”的意义. 2.语义,比语法,更能代表“语言构成的逻辑”的意义.

编译器的实现中,它能直接支持的类型是这门语言最重要的first class,比如C++直接支持类(UDT)为它的First Class,,Lisp这样的语言支持直接传递函数指针(因为函数是它的类型),,,就C来讲,,它支持primitive types,即普通的Char,Char *,Int,Int *,Float,Float *,Void类型.. 将基本类型发展为Struct记录类型,union类型,可递归类型,又是一种抽象,,将数据类型封装为ADT(同时封装了可施加其上的操作)就更是一种抽象了..基本类型中为什么会有数值,字符就知道了,这完全是一种趋向现实的抽象,这是每一种语言的每一个程序,每一个现实问题最能广泛体现到的抽象,当然,基本类型完全也可以是函数,如Lisp语言,,只要是一门语言直接支持的类型,那么它必定在内存中有一个位存储模式,汇编器规定了什么样的操作可以施加在这个位组合上.



对用户类型和抽象类型的支持

<b>一门语言的类型系统分内置在编译器中的type system和这种语言对user type defining的支持,如果有可能,使builtin type和user define type之间产生联系也是很好的</b>,即,编程作为对内置类型的一种扩展动作,如果允许程序员从builtin type派生user define type也是很不错的,比如Python的userdict,userstr等等.


------------- c语言的UDT语法语义支持系统


C的数组[ 一般来说,数组指代某种数据结构而不是data type,但是,正如也可把它当成一种复合了其它类型的类型.即ADT.抽象的data type.C语言这样的系统语言,一般只内置primitive types以对应系统中的类型,它在语言内对数组这种data type的集成是个例外.],指针与字符串
(我这里讲的都是C标准)
	C只直接支持简单的数据类型,只有简单的Int,Float,Char,Void,这样的数据类型可以直接定义使用(并可作为函数参数传送,但数组就不能直接被传送,需要转成它的指针形式 — 一个32位长整型数被传送,,因为它不是First Class),,其它的高级数据表示比如字符串,数组,都是在简单数据类型之上模拟得到的,,,是库级的逻辑,,编译器并不直接支持..(C编译器没有提供对字符串String的Built-in支持,只有Char和Char *,C把它作为库级逻辑的String来抽象)
C99在库级新增了_Image,_Complex,_String这些数据抽象(相对C++来说)．．
所以C的指针类型几乎跟数组,字串这样的逻辑同胞共母,字串本质是Char * 数组,,数组是内存相续的同型数据,用指针变量来表达数组和字串几乎浑然天成(数组名就是指向第一个数组元素的指针,类型为:＂(基类型)指针变量名＂这样的形式,,而且字串直接被定义成char[]的形式,,数组大小一定要程序员方面保证容纳字串大小+一个/号的大小,字符串函数大量涉及到指针比如strcat,C有一个标准的字串实现,cstring.h,C++有一个STL版的字串,C++还有一个原生版的string.h,特定的编译器也有特定的字串实现),,,C就这样把所有的东西统一于简单的＂简单类型＂．．
当然C也提供了union,struct这样的结构体来表达比简单的类型来抽象一级的类型,
**以数据抽象动作为中心的设计,以类型为中心进行设计工作的语言.这是冯氏下编程的特点**
有没有注意到呢,无论是那一种语言,编程首先是将概念进行数据化[虽然Python这类语言在这方面有些隐晦,那是因为它不是没有类型及数据,而正是这些类型是动态的向程序员隐藏的](冯氏编程都是DT编程,抽象了的冯氏编程是ADT编程),以至于将那些不是实体的抽象概念都数据化 — 比如设计STL时将迭代器Template Class化,,还比如指针其实是一种企图把数据和代码整合成统一的数据的手段.即code handle数据类型,脚本语言的变量中,数值可直接表示科学运算用到的元素,其它UDT和ADT可表其它高级的DSL抽象表示..也即类型.
**类型就是数据(的模板),编译语言严格这个过程,直接使用类型本身,脚本语言提倡类型即数据.直接使用值无须显式声明,它们对类型的侧重使用点不同**,我们可由类型定义出子类型,,也是一种数据类型..比如Typedef int myint,,,这在C,C++中广泛使用.当然,typedef并没有实际定义出新的类型,struct,union,sometype*这样的东西可以.
我们知道内置类型是编译器的事,提供了类型化设计手段的编译器将这种机制过继给程序员,于是他们可以进行UDT编程.
类型即内存中编码了的“计算机数据”,即设计者眼中的“数据”(UDT),(即“OO设计”实际上=“用ＵＤＴ表达设计,用数据描述设计”)
我们知道,冯氏机是数据主导代码的,**冯氏语言除了抽象化类型之外,它还抽象化代码**, 比如class,注意,**OO的类型化绝对不能说成对象化**,OO定义成面对对象是极其错误的译法,,OO是应该一开始是类型抽象(它为一种语言提供用户自定义类型的那些语义,这才是class的出发点),然后我们才关注它导出的对象值类型,所以O这个字眼只能是“类型化”的“类型”,而不能译成对象,,因为对象一开始是实现里面,不是OO设计的原义所在[ 你在后面的章节会看到Python中的类就是对象,而它的真正的接口类,是metaclass].
到这里为止前面写的都是属于抽象化数据,那么从表达式和流程控制开始,讲解的就是冯氏语言如何抽象代码的问题了.



抽象冯氏开发中的数据与代码-从平铺,过程的代码到预置,类化的对象代码(ADT&UDT类型与运算系统)(C++,C井)

objsys统一类型。


==================




/*!

\page 抽象了的数据产生模式,代码产生模式:(C++,Python).html

============= 抽象了的数据产生模式,代码产生模式:(C++,Python)


初识OO,我不过认为那只是一种编程语言支持的工具,,这就是类.OO产生的初衷是将设计加入过程式,因此对设计中的1:更好抽象事物,它弄成一个adt 封装过程的函数和数据,对于设计中的2:为了维护而加入对人类思维的靠扰,就是public这些访问符.所以这二方面实际上就是对应一个class.

总结起来，它不过是一种更新的型而已，那么,OO的类如果是一种新的代码模式,数据类型,那么它是较原来简单类型下什么样的增强类型呢? 比起OO语言之前的类型来说,在数据类型的眼光上看,有二大改变,

+ 以前的简单类型现在可以杂合数据与代码,所以是一种既不能称为数据或代码的ADT或UDT,面向对象的方法成员广泛上的意义就是“对数据的操作”,也即计算机指令,,狭义上的意思就是“表示对象的主动或被动性作用的方法或函数”,,,面向对象的数据成员就是“数据或变量”,也即计算机要操作的数据,,这对应于面向过程中的函数跟变量,,,而面向对象将它们推入一个更泛化的境界(一切计算机数据都可成为数据,特别是OO对象).

+ 类与类之间可以发生联系,这种ADT与UDT通过组合或继承来构造整个系统,程序员之间只需共享对于这些ADT的理解. 对于OO中的class,它可用来派生子类型也可用来产生对象(我们用措词上的区别来区分这二者),派生的子类型subclass,此时它也是一个 class,,产生的object,我们称一个对象为class的instance.class为object model

这其中存在一些特例,比如纯抽象的class(用来实现C++版本的interface),,或者静态类,,

为了产生逻辑,我们可以继承,也可以组合,继承就是从相对基类中(除了单根继续的语言,基类都是严格相对的)单层继承或多层继续,产生新的类,这样的子类在抽象上继续了父类的所有属性,在底层实现上其实是叠加了子类的代码在基类上的组合代码,是发生在类间的逻辑.也可以由类产生对象以产生逻辑,是发生在类和对象之间的逻辑,,,注意多层继续在现代OO中是不受鼓励的..

而发生在对象之间的逻辑呢,是采用将一个对象作为另一个对象的数据成员来作为产生逻辑的方式,,对象之间交互的方式就称为消息,C开发的函数范式在这里被消息所代替,实际上我们知道消息也是函数调用,只不过这里的函数是加了访问控制和多态的特殊性函数..

>所以，冯氏上的编程都是数据编程和对其的抽象化，存在三种：

一是汇编编程，它只是指令的组合，就跟3d渲染机一样，它的特点在于设置其状态后一直开机工作，重叠切换，以影响其工作方式，一切在于用户如何组合指令；

而C过程式编程将指令抽象成了数据，基于OS的编程也就变成了数据编程，这时是plain old data programming；

然后是OO，它将data programming变成了adt programming；
实际上还存在着第四种冯氏数据编程：这就是基于OO上的高级OO，比如用OO表现的interface based programming,它将adt programming变成了interface based programming.；这些在文尾有述。





------------- 抽象语言层的数据代码 － 对象 : 类型不仅仅是类


###### 私有,保护和公有

权限修饰出现在二个地方,1,在一个类内部对成员的修饰,,2,用基类派生子类时,对基类作何修饰,,这是修饰派生方式的修饰,,这二个因素共同决定了外界以如何权限组合,,读写一个类的成员(这才是我们最终要访问的目标,但是有二重门要过),当这个相对基类是.

>一般的OO实现只实现三种级别，即其实这三种访问方式不妨称为“公共级(对应公有)，私有级，和特权级（对应保护级）”，其中特权是公共和私有的折中。

###### 重载与复写

重载与引用是一对互逆过程，因为这是对名字处理的二个相反过程(从编译系统的符号表的眼光来看)，重载是多态的简单形式,其实对OO来说, 要谈到重载就要淡到多态,Overroad与Override,重载是根据已有事物定义新事物(这个新事物是与已有事物貌合神离的,通俗来说就是在一个具体类中,可以定义多个函数名相同但参数不同的成员函数,前面可以用Virtual或没有这个关键字),覆写是将旧事物升级为新事物,因此重载时的旧事物与新事物都有效的而覆写时的旧事物作费(通俗来说,就是在一对具有基类与派生类的二个类中,派生类中可定义一个与基类成员函数名和参数均相同的成员函数,此时基类函数前必有Virtual关键字),诚然覆写可让基类同名函数作费,然而在C++中还存在其它函数作费规则,这里“作费”是指派生类的函数屏蔽了与其同名的基类函数,规则如下: 如果派生类的函数与基类的函数同名,但是参数不同.此时,不论有无virtual关键字,基类的函数将被隐藏(注意别与重载混淆). 如果派生类的函数与基类的函数同名,并且参数也相同,但是基类函数没有virtual关键字.此时,基类的函数被隐藏(注意别与覆盖混淆). 覆写跟复写不一样,这两者都会导致多态,然而,覆写会导致“父类在调用它的一个成员函数时,实际上在调用子类的一个成员函数,因为它被子类覆盖了”,这也就是c++著名的“用虚函数实现运行期多态”, 而复写仅会导致简单的“在父类和子类之间存在同名但参数不一的成员函数”这种结果

###### 继承

继承本质上是一种什么样的过程呢?继承分接口继承(此时它继承了基类不可变的东西)和实现继承(此时它继承了基类可变的部分), 我们已经知道，**程序大都是从上而下的层次式的，因此OO最善于处理这种抽象结构**，子类可以处理能处理的事情，高于子类的类就作为架构的上上层部分，而设计,一个至关重要的处理的就是**封装可变部分.这样,我们就从抽象角度理解了继承这种语言机制**.

OO的继承迎合了抽象的得到是一个从已有代码（泛化）到新代码（具化）的过程，，，数据结构和算法，以及过程式，系统类型可以产生基本抽象，然后OO从这些抽象中产生用户适用的新抽象，所以他们的出发点不一样，过程系统面向功能抽象，OO系统面向用户扩展抽象

>>所以得到抽象时我们不需要OO，因为不是所有代码都是供复用的，操作系统内核实现只要导出函数级的可复用单元就就行了，而不是一个库体系,,开发的层次跟复用起点密切相关，从raw api，，还是用户抽象的有机库体系（api族），，还是什么轮子都不用，，都存在复用（代码内复用，已有代码外复用）

------------- 脱离语言层抽象概念


真正稍微懂得它，并明白OO首先是一种思想时,我发现我走入另一个迷惑,只不过这次是一个更高层次的迷惑,,如果OO是一种思想,,,所以我要怎么联系具体语言并理解它?而其实,正如我从书一直写到这里所秉承的,只有从抽象角度和去理解一门语言机制,只有认识OO的程度到了把它跟抽象和应用拿来讨论,你才能真正开始理解了OO.

>**抽象是如此的重要，要想在编程中描述抽象，最好的手段无非是“将抽象内置在语言中”，这首先从类型着手，**，过程式的类型只是简单类型，经过抽象的不同阶段（抽象数据，抽象代码，抽象概念），OO语言于是变成了“抽象导向语言”，能直接在某个层面描述抽象（更高的OO手段能工作在更高的抽象层面）

首先,比如为什么会有OO的出现呢?最初步的理由,OO可以很好地用来抽象，因为OO类似编程界对应于现实世界“Object(物体)”的抽象(不可否认我们周围的世界的确是一个一个的对象,注意这是用OO眼光看待问题域进行系统设计),我们可以在抽象的基础上构建抽象,进而发展出大型的系统(由土和石到房子,由房子到,不可否认我们一直在做这些的事和思想上的活动),而表现在OO语言和设计过程中,我们用Class来表示一个 Objects(注意这是应用领域,虽然这种Class对于表达现实的确显得有点单位过小-----而且是运行时不可控的抽象,但我们可以通过不断地包装抽象和组合抽象,或者通过策略---设计期可控的抽象来达到更大的抽象),,Class的出现是历史必然的,以前编码时是分开代码和数据的,整个代码被硬生生分成了代码和数据二部分,一个CLASS就是对于代码和数据的整合抽象(这样就需要只面对一种代码模式了)

>OO化并不强求以靠近现实的模型来设计应用,即OO不一定要应用于抽象，而更多地是利用OO的访问控制以同一种方式看待代码与数据(设计代码,定义数据)

抽象使高层置为顶端,面向对象就是一种抽象,这种抽象使我们看不到我们不想用到的事物的一些方面,而把那些我们能用到的事物的方面用来作为描述此对象的全部,,(即抽象了的对象根本不能完整地反映对象本身而且压根就不能),

其次，OO不但是抽象的手段,而且是复用的手段[1^],并并且,还是接口的手段.OO,还是代码跟数据在语言端的体现体, OO还可以是模块机制，故谓,OO是一个多面手,它同时代表着抽象,复用,代码方面的几重意义.所以绝对不是三重机制那么简单.
最后,面向对象的确带来了效益,面向对象并不是一种凭空冒出来没有根据的概念,相反,,没有它的存在倒是很令人不自然的,面向对象和基于面向对象的设计模式使软件设计进入了一种高速发展的状况,甚至个人独立开发体系复杂的软件都成可能[^2],这就是面向对象的作用之一所用所在,,,因为本质上,面向对象是符合现实生活的,,,那就是:正如上面一段所讲,面向对象特别类似于建筑学的过程,需要不同的原料并组合它们才能构成最终的软件或建筑,我们只要发明了砖和水泥这样的原料,就有可能发明楼房,但在不必首先一开始就得造出一大幢房子的需求下,我总可以慢慢积累砖吧,否则,一切细节都在开始被考虑,这不太现实(往往有时候,,,开发一个程序是一个真正工程规模级的活动,不是指那种声明几个类,创建几个对象就完事的开发过程,,而是指那种预计到未来扩展的需要而预留了很多发展余地的大型开发过程)

**综上所述，面向对象语言提出的OO,,,一方面既是抽象机制,,,一方面也是接口机制..**[^3]

在抽象应用上，OO为逻辑与事物定义了一套流转分派,查找与等级系统,符合为事物划分的道理,按等级(class:类别,等级)划分。

**在开发范式上，你要转变顺序编程和过程编程的理念,接受这种层级化编程的方式.**

既然OO是抽象又是设计，所以，它又是存在着高低层次的。有语言级的也有高于语言级的比如设计模式级的模式和接口编程中的接口等。这就是第四种冯氏上的advance oo 数据编程。

比如我们知道在C++实现的OO机制中,存在class,class=type,即template中的type,但是我们知道template更像是一种建立在C++类型机制上的脚本语言,其语法古怪,不接近C++本身,,C++用class作为派生type的类型,用type作为 template中的类型. 而设计上的学习往往要求你掌握关于此问题的所有细节(在目前的科学技术水平下对该领域的现解),和与此问题有关的很多周边问题,所以要从原语领域去看待此问题和进行基于对象拆解此事物并构造这些对象之间的逻辑的系统活动,
基于OO之上的设计模式的学习也是很重要的,对设计模式的学习是无比重要的,只有掌握了设计模式,才能不会让思想局限于现有的代码,才会在一个更广泛的领域里去拆解对象并进行设计(原语领域去看待事物,因此程序设计实际上是一个反映你心智和哲学水平的活动),往往有些时候,,,真正的再编程能力不再是语言细节和问题细节,,而是在掌握了语言细节和系统细节之上的高层构架的学习(设计上的学习).

接口是关于如何应用对象提供的服务的全部抽象,如果说面向对象和接口是代码级复用的机制,那么构件是二进制级真正的复用机制,接口把一个系统的可用部分按不同的形式透露给复用者。

当然，还存在很多其它类型的advanced oo。这些在以后都有述

[^1]: 计算机界的事物从来都是相承的,而不是新事物埋葬老事物的一个结果,OO的出现,并不等于过程式语言的消亡,实际上,一门具体的语言,总是有我们常看到的过程式的元素,这是因为,OO都是建立在结构化语法上面的.

[^2]: 比如,OO+MFC使”软件组合”成为可能，程序员成为了装配工人，而不是兼顾设计的个人艺术英雄。

[^3]: 抽象也是一种设计,接口机制是软件机制(中间件设施),而抽象机制,是设计机制.这是二个不一样的范畴.这就是设计跟软件的关系表现.

*/





==================	

> 银弹[ 什么是银弹问题:请参照《人月神话》,作者相信没有银弹:即,在未来十年内,没有任何软件或工程上的技术,能使软件生产效率提高一个数量级,而到现在为止,这个论题据说还是正确的]问题思考(1)

以数据为中心的设计的缺点
在很多地方,类型化正是设计的死敌,因为它规定了目标对象的产生模式,在整个设计中充满着错综复杂的对象头文件引用.数据间的声明含义进入设计一旦被固化,用数据表达的设计容易造成偶合.
而这正是泛型范型产生的最佳替代[ 后面会谈到范型其实是对冯氏模型抽象类型和抽象代码机制的一种突破,它不像OO是正面抽象类型,而是努力降低类型的作用.比如动态化它们,或把它们弄为一种非类型相关的设计抽象,比如traits].,范型将设计中出现中的数据默认为一个空的占位符(比时类型被”Generic”了,所以泛型是有别于类型化和使用值类型的一种特别方式,我们后来会谈到).无论是OO还是泛型开发,都是以数据封装动作为中心的.而过程化设计是以函数封装为模块为中心的.
即第一点:OO以数据封装为中心,这会造成偶合.
第二点:OO容易产生过度OO化的负影响,因为极容易将那些不显式的设计元素封装为对象,这反而带来了负面影响.
第三点:而OO的三重机制中的继承,更是
在抽象类型作为设计手段的方法上,OO和模板是差不多的,然而不同的是模板是“泛化”类型OO是纯粹只用“类型化”来实现设计(对即逻辑的抽象逻辑,我们知道,实现中也离不开设计,设计库的设计就更离不开设计了),,所以OO的设计手段不足,而设计模式是一种新的设计理念,语言并不直接支持,,C++用STL作为语言的数据抽象,,用LOKI作为语言的设计能力(OO,模板相比来说是小规模的设计手段).
于是人们提出了以方法集为中心的抽象设计工作,即面向接口的编程,面向接口编程就是面向程序如何被使用（为了这个目的，为软件提出一套接口）而编程.这将在以后进行讲解.


类这个东东来源于结构体,其实一个结构体也有它们的构造函数,在这种意义下,类与结构体很接近.

