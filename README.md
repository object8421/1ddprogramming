
1ddprogramming : one devstyle, one domainsolution abstractness

Writen By Minlearn
Frequently Updated @ http://minlearn.shaolonglee.com/

---------------------------------
intro
---------------------------------

新书学编程，第一件事怕的就是怕看不到编程的全貌，这种由未知带来的信息恐慌是很真实的，因为编程这个字眼，实际上并不能带给人们太多认识上的帮助，，它直接带给人们的认识是某种语言和学习和软件的编制，然而，实际上编程是如此之大每一个领域都是一个小世界存在多种方案，除非先道尽一切与此有关的东西否则这个问题会因为太多的准入者的言语论变得太多声音，恰恰巧在一个专家一本书的声音中我们恰恰甚至道不尽与某个语言选择相关的应用方案工程的全部所以我们还在讨论着(这绝对是个不大不小的“大”问题)，直到把它变成一门宗教。。编程的宗教，，所以在学习中，我们一遍遍为纠缠一些非实质相关的问题，诸如“怎么样去学编程，C，C++之争，要不要学习J2EE,怎么展开设计”之类的问浪费时间，这些都是因为不能从具体应用和采取的具体方案这样的大角度去思考问题。这些对于初学者和入门一段时间的人都是平等发生的，

而在实践的时候，他们又往往找不到足够详细的参考资料，埋没在互联网上的资料（他们大都非常优秀）需要重新整理。它们需要被整理加入缺失的至关重要的某些内容，以求得一个全面详细的，领域可查的，经过整理组织的理论+实践过程,,而且，而且如果可以，需要同时提供一个理论知识网与之搭配。来求得一个最佳实践的教学方式，而市面上一些对新出的API大力铺陈的书，它并不能教会人从上及下的思考。只会使我们变成工具小子。在实践和阅读一套稍微大型的源程序中，我们找不到一套标准，搞不清一套源码的类栈，为什么要出现这样的类逻辑使用了什么第三方组件，这些都是因为学到的实践不能有效用于实际。

----------------------------------------------------------------------
part 1ddtheory: direct,full,and detailed cutting-edge theory

深入浅出学理论:
基于这些，我一直以为，知识的框架是重要的，，只要先完成对编程科学体系中最基本的认识落实化，，才能最终能做到深入浅出，始于编程而跳出编程 ，换言之，它是理清编程学的主线和基本常识性的东西，在这些基本正确的全局观下，才能迅速确定正确的理论枝节主线区别和实践的方向 。继而具备真正的实践能力理解大型应用逻辑，独立公平地看待业界出现的各种现行的方案和不足。

----------------------------------------------------------------------


1）先理论后实践的直线式学习路线科不科学？行得通吗？

虽然先理论后实践是流行的学习方法，但如果理论先行指导得正，直线式学习反而比先实践来得更好。一切都是因为市面上少那样一套东西存在而已。

虽然学习强调实践先行，但在学习上宜先分开再结合，理论使他们把握编程的全貌，而且在把握全图的同时，能够培养读者的实践能力（爱好或者工作）。与理论部分提倡的从上而下的科普式的教学效果有着紧密的对应，而只有站在科学的高度，深入学习理论再学习尾端的简单应用开发，才会觉得编程简单，就达到了深入浅出，就达到了最佳实践。

虽然人们正常的学习规则是边理论边实践，但如果能在实践和学习之初能够让人们有这些基本常识和框架观，那么这个作用无疑是巨大的。

2）我们需要什么样的理论？怎么样才讲得清编程？怎么样串联这些理论才能达到教学的最大化？

只有计算机科学，抽象科学，平台，语言，方案，应用，，这些字眼，，才是我们要在意识里要首先存在的。因为它指出高于编程的那个世界的所有主体，指出了人们在铺设编程的总过程中提出的工程元素，只有在这里看待编程，带来的认识才最具有指导性和无争议的全面意义
比如这其中广为争议的语言的选择问题，语言的选择可以是一条编程实践界的主线，因为它涉及到学习开发过程中的应用方案铺设，，产品如何适应人一系列问题，始于开发而终于开发，由此带来的讨论甚至可以深入到平台选择，语言机制支持，应用设计，设计方案范式的方方面面。只有先完成这些，才能带来基本正确的语言选择认识和实间。

而这些应该还是最简单的科普知识，大众编程应是科普前提下的艺术活动。任何负责任的编程教学系统应是科普下的艺术，能讲清编程的唯一途径是将其自然部分即科学部分和人为部分即艺术部分分开。 比如系统开发是一种强计算机科学的东西，应用编程更多偏接口艺术。编程的科学就是数据类型(及冯氏原理类型机制)与算法。艺术就是封装(数据结构)和抽象。这迅速就为初学者分开了数据结构与软件抽象的区别。而软件抽象就是编程初学者要接确到的第一个概念。这二条主线几乎是理论学习的总框架，整书正是在把握大框架的同时细化了对框架内部各重要知识网点之间的讲解与串联，做到了理论教学的最大化。

3）最全的开发教育过程要涵盖什么？

有1-6种编程分别代表6代语言和应用需要，如果说(1),(2)，（3），（4）指定了cppware用于开发和发布，（5）（6）即属于用户编程，使用的同一种语言和泛式，这极大地简化了学习曲线，而且自始至终只有一种角色，（1）-（4）支持程序开发程序员级扩展的那些设计支持，即引擎开发和引擎扩展(第一级第二级)就可以使用统一的qtcpp，属于编程，那么这第三级（5），（6）的用户配置就属艺术和设计，也使用qtcpp的visual assambly代替dymic scripting，配合使用面向用户的qmlxml的标识描述语言和工具输助的自动生成qmlxml(like war3we)，，是一种微小的开发和配置式的开发，属于产品艺术不算编程。而且engitor使这一切上升到应用架构上的engine/mod/editor方式。 every soft should finally leads to a "engitor"(productlvl devcompent and democompent),,but not a half-finished executeables,or some libs..(engitor, engitor=engine+tool,语言和框架是机制，还必须提供策略性的工具，如IDE),也是同一种角色。

《直线学编程》理论部分巧妙地对应了这些过程， 整个系列的亮点在于描绘了一个事事巨细的知识点框架，最佳理论的方式，和一套从根本上体现桌面编码基础的逻辑体系：

理论篇构架了一个从平台原理到软件工程的整个网络，使新手能够全面地看待整个编程；这本书主要的亮点在于构建了一个科学，事事巨细的知识点网络(top concepts)。完美地把理论与实践的字眼串连成以作为语言应用问题设计抽象重新整合过程历史的大网络并加以系统解释，使读者在know what的基础上how，真正具备独立解决至关重要的那些障碍的能力,,从而更利于以后的学习，无论有无基础，如果用它来进行理论学习和实践前教育，将会事半功倍。

故：我力求建立这样一套理论实践合一的知识体系(toppestconcepts)，特别是要将对语言的选择这个惯彻始终的问题展开，，,，这些都被做在了一本叫《新手看编程》的blogs会编中,这是一本教授新手级编程理论,win32,cpp及qt,系统应用开发实践的技术类书籍但远远不止定位于这些。更多请参阅《关于minlearnprogramming》。

----------------------------------------------------------------------
part 1ddpractise:the full domain?solutions of?phc common, phc web and phc game : the desiging abstractness dict ref?and?the coding and debuging example base

《浅入深出学实践》

先进可以导致另一种倒退，抽象会导致复杂，而强大复杂性只能面向人只能透露它足够抽象简单的一面。
最新语言和web开发使用越来越多的设计哲学，软件VM，框架组件中间件复杂化了开发本身。学习只能是浅入深出，绝不能是深入浅出。。因为我们需要一个低门和一根进门的杖。人类能掌握的复杂性最有利的情况下是2到3个。最有效的拐杖是可视化。稍后会解释whyphp及它装备visual widget for dev in delphi vcl way和装备有serivces as paas container in j2ee jeanbeans way的优势和改造。

----------------------------------------------------------------------

应用开发实践与语言实践是个必经的，去疑的live终端体验过程，一门具体语言语言的掌握与熟练度，具体方案的编程实现与应用问题的解决，框架的发明与使用，甚至问题超越文档信息的获得，实践方法论都是实践。

1）一本负责的实践书至少要让我们看到什么？什么是实践的壳什么是质？

书面上的书大都是语言教学和实例详解，但恰恰没有讲解如何去实践，它们是静态的，而中间那个领域实践点和抽象法列举是体现动态过程的关键和实践核心所在。

试想一下，编程即翻译，转译。只有讲完了源和目标。才能一步一步桥接起目标和源之间的转化，

大工程的模块划分粒度大部分是依照software domain solutions划分的，比如comon,native,domain speficed（比如,web,game,etc..），这三大抽象逻辑栈。内部小粒度则有业界对问题的不同定界各各划分。这样在阅读或设计大工程/大源码体系时我们才能不迷失。

语言技术法是最基本的细节，然而情景抽象转化术，和习惯用法，就像英语翻译一样。。那些用已知的模式去替代，整修，适配轮子，定位接口，也是细节，这个具体到类级抽象惯用法。还有，debug（基于ide和软件调试器）跟coding一样重要，是c+native os programming时代的testing，，是工程上必须透露出来的查错手段，就像会编时代的中断。。以上都建立在构筑一个可查的领域抽象字典上，就像MSDN，都必须要讲到。才能算是完成了实践教学。而有了之前的理论部分，这部分才能形成框架。

2）实践要到什么份上？编码能力？

如何OO,就像如何写作文，在业界通用抽象习惯的情况下，大家都可以有一个自己的用法。但绝不好天马行空。弄得后人看不明白。
抽象方面，理解了语言细节，领域细节，有勇气自行OO抽象，理解轮子抽象，理解业界实现抽象，你就能面对工作了。

3)现有的编程还能再简单些吗？这就是1dd：the uniform dev and domain abstractiz和engitordd

如何安排细节逻辑的能力？在没有任何提示hint的情况下，我们需要一根拐棍，不需要知道天机也可走下去。只要跟着拐棍走。效果指引的编程。强大的东西是可视和效果。初级的用户只能看到这些东西。如果他们能够在这种指引下直接编程来慢慢学习更深的东西，这个作用是巨大的，而可视编程只做了初步。即界面方面的工作。

如何为一个大逻辑作一次设计类图，且这个类图可重用。先选型找轮子找到了能类设计。就是整个抽象能力。类图设计要domaineasy..将编程由书写的思维形式真正变成艺术极大化的可操作行为。

这就是ezdd,easy d:dev,d:domain
和engitor : devware,demoware统一

如果说最终的软件是domainlvl appware,那么一般的库，小库，就是devware,而那种大中型的middlelvl framework，就是demoware或near-demo ware了，这就是库与框架的区别，框架是对语言，问题，应用的综合解决，已经可以从中简单地泛出一个’demo”，，，
engitor就是使一切框架变成实实在在的，显式的demoware,,,为每个应用建立一个engitor,而不是一个面向appmodel，stdlib存在的大型框架，engitor已经具体到应用了。
为框架提供一个逻辑提取前端，生成目标高级语言代码，且可形成可运行的demo, for初学者，以语义的方式。就是engitor的原理和工作方式。




《直线学编程》实践部分巧妙地对应了这些过程，整个过程提供了对语言实践的讲解(src/general)，直到领域逻辑，直到appmodel的源码基础，完成了全面展示了一个涵盖全面，源码清希，技术点突出的最小练习集:

———— 作为与《新手看编程》最佳理论部分top conecepts部分相配合的最佳范例， 它展示了一个从general programming到win32 app(engine)lvl dev的全部抽象体系和源码实现,产品实现过程（arranged progs and codebase）——– 如果说bk top concepts部分指的只是指导实践的理论通例，一份bookaddon src源码只是静态的设计范例，那么，这部分就解释了具体语言(c/cpp)和方案(本地开发与封装逻辑栈)，未来可能做一个框架，并设立一个bcxszy part3 提供这个CPP framework的全部理论原理，和使用它们进行开发实践全程指导 – 它相当于bk addonsrc组成的的框架库的”msdn”(design,implant details,and api practise,refs)。 学完此系列，读者应对win32列的c runtimes有深刻理解，并对c/cpp有实际的编程体验，而且对win32项目也有实践，这样，就形成了一个完善的教学体系，就能使读者把握编程的基本全貌的同时(top concepts formed best theroy)，实际培养他们进行通用app编程，并使用c/cpp/cpp framework进行编程的实践能力(withthe help of these docs from design and implant details to apirefs ,readers canget a review of minumaled general and game programming best practise)。 

以上所有这些，对于上升到通用非game engine,game dev(一般游戏开发就是game dev ,game engine based dev)这样的抽象模块情况也是一样的.
为了最小实践，本部分着重了对langprac的章节铺陈,整书没有任何高级语言语法例子，以降低门槛。整书都是简单例子。故整书可作为引导你日后进一步不断学习的开山之作而且allinone，bcxszy始于编程而且最终给出一条让你跳出编程的路,不必到处找资料。回到语言选择和开发方向的最初讨论，这也说明呈现一条编程教学清希线索和选材可以变得尤为其重。

----------------------------------------------------------------------
the toolset used:1ddphp - one dev style, one deploy
----------------------------------------------------------------------

以前1 minqw/cppware：
cppware它将这一切集成到自身(the cppeelib)，使用的是工业标准的C系语言，完美地整合了C的系统和CPP的应用编程支持方面为一套系统，上面说到，将其上升到语言组件支持的境界与组件直接相连，就可以从开发上直接支持变得可持续集成，这一切的背后即pme模型。pme是平台。语言，框架，应用，设计，使这些方面得到统一的，真正的平衡机制。比如上面由组件到RPC到分布式的一条龙讨论，所有这些是开发也是教育的必要，因为这样，它才能呈现一个all-in-one, but focusing on the core bestpractise parts的实践点集，形成一个平直开发与平滑过渡的开发学习文化，并做到教育和工业上的统一化。--------- 由于中心稳定，扩展不会触及到基础的改变而推倒重来或叠加太多复杂性，在这种体系下，我们才能做到平直，有限的学习和实践，使读者在编程实践和练习时有简单全面，但清希的脉络可依。再辅于精细的知识点日后练习，实践就能达到最佳。

以前2 yahpcee：
1ddphp源码集，用来讲解的1ddengitor加1ddpaas和,它增强了php的必要部分。使之保持一个固定的语言核心。综上，整个1dd项目集目标还是那个目标：提供一门C或类C，组件可视开发和部署运行，力求不采用云端docker等paas，将一切封装在语言级和vm级。并使之保持一个有限，足够简法的语言核心。

现在 lzc：
继2，用sandbox代替vm,用户可自定义sandbox环境，以纯开发式组建（基于组件）自己的用户环境定义文件。上传自己的应用运行。


1) 技术选型是很重要的。why php?，因为php有鲜明的浅入深出特征。

除了它的基础语法像c以外，c还可以binding——————，c系与php有如此大的相似性以致于php几乎不用专门入门，难怪会c/c++的都说自己是php程序员。。。

5.3开始增加了类java的phar，语言特性方面PHP5.4提供的namespace，phar打包，composer依赖管理，Trait，完整的面向对象编程语法，强大的魔术方法和常量，字符串与函数类对象直接转换，闭包和匿名函数等丰富的语言特性。在后端开发方面强大到堪比Java，C#。。

但是，其实学习php，学到object就可以了（再附带学一些与dp紧密有关的generator,closeure），其它的像interface,pme都是开发库的langtech技术，一般开发应用学到object就完了。在这个层面上，其它一切都可以是api.所以php简单。

php的扩展模块大都只是thin dll from c,因此作为一门慢慢添加上去的语言系统，它保持了与c的承接性和可辨认的脚本历史特征，不像java,.net一上来就是大而整合，而且php鲜明的cli/cgi的appmodel区分，这二者保证了其学习典线很平滑。

当一种语言的参考手册全是类时，就比较麻烦了，所幸php的全是函数。这样测试与学习曲线较低。C是程序语言初学者能掌握的最小集。

2）codebase as prac refs: 框架集和散例，使整个教学深入浅出。

除了讲解语言实践，还需不需要讲解框架编程来讲解通用编程实践？

前面解释了理论学习中的框架,,一门语言的能学会使用是最基本要完成的必须先行的，这样在实践和学习过程中的一些东西才能得到沉淀形成经验，然后才是问题的解决，甚至开发文化的东西，具体游戏方案域，有具体到细节的实践，

而框架，是对语言的增强，对API的封装，对CPP的增强和对os api的封装，对domain appmodel api的实现,对最终用户逻辑app model的对接，尤其对于应用开发，一个framework是很重要的，对其作源码分析或作应用开发实践是最好的过程。

全书用了散例，也极力在phc框架下进行各个技术点的教学.

---------------------------------
以上基本是《关于本文集初衷-Focus on最小理论教学，最佳实践探索》的简版，更多请参阅那里。
---------------------------------


www:

online reading: see <a href="http://www.shaolonglee.com/wiki/toc/">http://www.shaolonglee.com/wiki/toc/</a>
and <a href="http://www.shaolonglee.com/wiki/toc2/">http://www.shaolonglee.com/wiki/toc2/</a>

src:

<a href="http://github.com/minlearn/1ddprogramming/">http://github.com/minlearn/1ddprogramming/</a>

down the offline: see bcxszy


