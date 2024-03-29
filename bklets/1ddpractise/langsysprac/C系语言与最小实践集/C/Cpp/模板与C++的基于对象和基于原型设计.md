﻿/*!

\page 模板与C++的基于对象和基于原型设计.html

============= 模板与C++的基于对象和基于原型设计


什么是基于原型呢？ 基于对象不是基于原型,基于对象是语言使用UDT的方式,而基于原型是一种advanced oo 范式。

Todo:修改这里


>元编程,OOAOOD设计体系[2. OO不单是OO,它本身,以及基于OO的后面的设计手段,面向接口,切口,等,使得OO成了一个设计体系],policy based design[3. 基于策略的编程,指,只要在调用模板时,用一种方式(比如指定typedef激活其内的某个type)这种只提供一个策略方案,就可以激活模板预定义的策略定义,的方式,类似给一个函数指定实参的过程,就称为基于策略的编程,它强调策略驱动编程,策略本身又往往是很小的,策略跟策略之间往往是正交的.这样基于策略的编程就可以达到最大的设计效果.],允许语言使用来自用户的抽象手段.整合进语言本身有的设计体系.

实际上,**不该有纯粹的关于编译语言与解释语言,动态与静态语言之间的比较,因为这其实是某一个本质下的现象**,真正的对语言的分类是:面向设计期,预设计期的语言和面向运行期的语言. 就目标来说,编程不应分为对本地编程和对VM编程,应改为:对系统编程(执行)和对应用(逻辑)编程.主要以执行体和应用作为编程的分类点. 基于对象是什么意思呢,,这个基于对象不是指"不能从中定义出对象的类本身这种ADT",(不是数据抽象),,这里的基于对象,,就是指通过运态语言中通过"接口"实现的对象多态这种编程泛式,是动态语言中除了OO范式之外的另一种更为高级的编程泛式.. 什么是基于原型呢,,就是说,事物是什么样的就是什么样的,如果它动起来像一只Y子,那么它就是一个Y子,,于是我们就提出一个原型,(具体到一门OO语言中,这实际上是说,我们通常从对象拥有什么方法组合上去判断它是什么对象,而不是从它错综复杂的继承关系入手),比如Y子动的动作,(这就是二进制级的接口,对象行为集,而通常情况下,基于类的OO语言中都是单根继承,语义上的,实际上这种继承是不符合现实的,因为“类别”都是人为加上的概念,class 这个字眼与其说是一种ADT,,事物原型,不妨说它更像是一种偏离原型的分类即classification,在编译型语言中,class偏指类型,而在解释型语言中,class偏指“原型”),实际上运行期的行为集接口实现的原型才是事物的本质,,,而编译期事先由单根定好的继承,这种早就分好类,并在运行期泛出来的对象反而是不符合事物原来本质的.. 原型继承中的原型，是设计模式中的用词，属于产生对象方式的模式中的一种，建议翻一本设计模式方面的书籍。类型在运行期可以被动态改变,,像Y子一样灵活地编程,那么在编译期类型就得不到被检测,,这极大地放宽了一门语言对于类型的检测机制,要知道如果是对于系统编程的话,类型机制是多么多么地重要,虽然动态类型语言编程灵活,但是其安全性没有一个保障..这就是安全性和灵活的矛盾之处.

上面的基于对象,实际上也就是基于原型,,C++只有运行期的面向对象,却没有类似RUBY的基于对象开发泛式了吗?用C++的模板技术可以办到!!

"C++模板实现的基于对象"是十分可贵的,第一,它提供了类RUBY的基于对象编程的机制(提供了类型多态,),,保证了编程的灵活性,第二,这种基于对象的多态是在编译期被栓测的,,一方面又保证了语言的类型安全性

一个是二进制运行时级的多态,一个语义级的多态

那么这样说,C++的运行期多型可以被抛弃了(我觉得作为系统语言的C++只需要基于对象和模板就够了,虽然C++可同时作为应用开发语言,但是它的运行期实现的OO实在是给系统问题引入了过多的人类OO思维,使系统问题变得多解,很多时候,我要求去掉C++的OO,当我只是希望用C++开发系统相关的逻辑的时候),,因为基于对象的方式提供了编译期多态就够了..而且同时提供了类型在编译期多变了灵活性和安全性不幸的是,理解STL深层的原理是需要懂与模板相关的设计的,比如仿函数的本质,迭代器,配接器的本质,模板导致的泛型开发与它提出的这些设计相关的东西可以另外写成一本书.学习STL首先是学习这些设计手法,再学习其数据结构和算法的实现. 泛型有二层意思,第一,基础泛化,它把泛型参数化,用于动态产生关于不同型别组合的相同逻辑(可以联系函数声明和函数定义来理解),这也就是一般泛化了,第二,它把一切设计中可能出现的因素都类型化(template class化),即在template class这个字眼中不主要强调template泛化而是class类型化,(只不过它也会用到泛型的第一层基础泛化作用而已)比如,迭代器,仿函数实际上都是(模板)类,这其实更像是C++的概念而不是泛型的概念.(因为class是c++的而stl及它导致的template手法是另外一个人发明的) 为什么需要把指针,函数封装为class呢,这是因为在C++中,class几乎就是一种逻辑粘剂(即将数据成员和函数成员,,当然在模板中也可以是模板成员数据和函数,封装为ADT),在这里并不强调这些Class运行于runtime的那些特征,比如多态,等,而是强调class封装逻辑成 adt并提供private,public,protect修饰机制的能力(相比之下C++的struct太简陋因为它只能提供全public,而且不能成为adt,因此没有adt的诸多好处,比如C++的只对class有效的运算符重载,,而class+oper overloading+template class你呆会会看到,,这在泛型设计中是多么有用处的东西.),,所以在C++中,相比面向对象来说,这些基于对象的开发范式也需要被重视.. 一句话,class化可以获得语义级的value, 只要给该class一个copy ctor就可以复制并传统它,给它一个重载的括号就可以成为跟函数动作一样的东西出现在C++语法相容的东西(虽然语义实际跟标准的对应物不一样),,, template class是泛型设计中的重头武器,因为: 函数+oper () overloading+template class化 = function objects,这就是stl中的仿函数. pointer+oper * overloading(和-&gt;)+template class化 = smartpointer,这就相当stl中的interate. Multiple inhert + template class作为另一个template的参数=policy,即loki中的策略. Struct+template=nested type,,内欠型别.. 元编程里的metafunction

模板特化与实例化是不一样的,,,其实任何一个模板,都存在二套参数,一套是泛用的,在tempalte关键字后面,另一套是特化或偏特化用的,在具体的模板后.特化与实例化的区别在于实例化不需要人去干预..
静态类型指派

[code lang="cpp"]
#include
#include

using namespace std;

template
struct _if
{
//当a为真时，X变得有效
typedef X type;
void couts()
{
cout&lt;&lt;"当a为真时，X变得有效"&lt; }
};

//通过指定一个特化体，隔绝了这二种情况，上面的模板主体即为true的情况，下面的，即为false的情况。
template
struct _if
{
//如果b为假,Y变得有效
typedef Y type;
void couts()
{
cout&lt;&lt;"当b为假,Y变得有效"&lt; }
};

int main()
{
_if my;
my.couts();
_if her;
her.couts();
return 0;
}
[/code]





------------- Generic template VS pure OO的优点:


OO太小,在表逻辑方面,它的底层是数据和代码.Template generic 手法以OO为底层,可以很容易跟OO结合.而且,它提倡可巨可细的策略化设计,并用concept表达设计.所以在表逻辑大小上,比OO大,又并且它是一种“自动化”技术(只需提供关于类型的策略,就可以得到一个类),所以复用能力比OO要强大,而且,这一切都发生在编译期,不给运行期负担.而且,用 concept表达,比用OO表达,更能符合“类型是编译器反映给人类的一种概念”的信息. 当然,它也是有缺点的,如调试不便,可能造成编译时间过长,代码膨胀,入阶曲线过高,不能实现corba这样的运行期依赖逻辑. 另外,在开发库方面,使用OO跟写OO可以很容易统一,而写模板跟使用模板的曲线却截然不一样.往往使用模板简单,而写面向复用的模板却需要懂高阶的template设计手法.

判断一个类的成员是不是能被继承,,最终的途征是看它是静态绑定的还是动态绑定的,如果动态的,就可以,(static 成员) 要深克明白这个绑定与实例化的意义所在,, 推迟绑定时间到编译期(设计期),就是元编程的意义所在的一个重要方面 元编程就是设计期实现和运行期实现的结合(也即在编码时同时进行设计期和运行逻辑的工作) 因此它是语法导向的,而不是虚拟函数集导向的如果这个层面被提出来,它甚至不占用到运行的时间,,即增加这项抽象,并不耗费运期间任何成本(因为它只发生在编译期)

*/