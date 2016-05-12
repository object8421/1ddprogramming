CG Based Game VR
=============

一定要分清render和cg的界限，也要分清cg和gamevr的界限，比如场景管理就是属于CG的，而视景剔除就是属于Render的。虽然这二个字眼间看似相似度很大。

GAME VR就是发明一些基于CG的图形世界组织（角色，地形，特效等虚拟现实的东西），GAME SR就是发明一些基于AI的社会世界组织（智能体，甚至智能世界本身如路径，智能物品）

就像AI和ai based game sr一样，在game[^1]级，game vr主要不管通用的CG逻辑，而关注于从CG引擎中发展而来的VR逻辑，比如用图形事物展现的事物（模型，地形，特效等），在game级,game sr不必关注通用的智能，而只应实现智能世界和智能事物(情景依赖的game sr logics)。







程序上的游戏中有什么：作为图形程序的部分- 游戏的场景系统(模型)
-------------

xx

再来看game vr中的地形：

程序上的游戏中有什么：作为图形程序的部分- 游戏的场景系统(混合了室内室外的大规模场景组织与管理)
-------------

地形算法应属于图形学算法中的“大规模网格建模与渲染”,它也是引擎程序上的抽象[^4].

它涉及到大规模网格的生成[^5],地形的细分subdived与tellsation

室内与室外场景关于渲染和建模的要求截然不同，比如，室内甚至不要求有地形，而地形，它是一个最难解决的问题。

从这里开始，就是作为game.graphic级别的cg了，这与前面说的那个章节，是cg与vr级别的cg的区别是对应的。
>一个大意义上（程序意义上）的scene是指“世界,world models”，地形只是一个跟mesh[^6]同级的概念，可以跟mesh一样作为场景图的一个节点[^7]。地形跟水是平等的game级对象(它是虚拟游戏世界过程中出现的对自然物的虚拟)，或作为引擎的scene nodes实现。 在偏游戏的引擎中，actor models 和 world models都是model,但是一般world models只简化称作为terrain model，但是，一般，世界这个概念，其实也包括地形上的任何东西，或者自然景观的定义与渲染。。所以，不光包括地形，它还是个综合性的问题。 即现在，场景这个概念，不单是综合考虑渲染一个网格模型的事，而是渲染一个“称为世界模型”的综合事宜，这个“世界”，用渲染的观点来看，它是一个“模型”，所以，除了网格模型之外，这个“世界场景”已被扩充指代其它更多的东西（程序上的集合体），比如“地形，天空，自然景观，粒子，角色模型，网格”，甚至“字体”，“GUI对象”，“Billboard对象”。。。在低层渲染的观点里，这些都没有分别，但是在高层的“世界场景中”，体现在低层渲染上，这些粗粒的东西是细粒地分为几个pass来进行渲染的（在高层只能粗略地渲染，而不能做到跟低层一样）
在渲染上,它涉及到,1.Culling,即基于某一种场景树图的scene manage,2.Lod,即判断是否在必要时选择渲染更多的三角形的问题.

地形的生成,往往用到了曲面理论,这取决于地形几何块是基于mesh(是先提出一张大mesh,然后由这张mesh细分而来的)的还是mipmapping(先定义几何块,然后组合成整个terrain)的,在不同的情况下,涉及到的问题是不一样的.

>对于“能利用计算机图形学能解决的任何问题”，有如何建模和如何渲染的问题[^8]。 利用计算机图形学解决地形问题，要达到什么样的效果要得出什么样的解决手段，这首先取决于我们所要的“地形”是什么样的，然后我们才能在建模和渲染算法上和程序上有所取舍，有的“地形”是对真实世界地理的模拟(数据量大)，只要在显示时现出一张静态图片就可以，有的“地形”却只是对“虚拟现实”的一种描述，在显示时要求能动态高速导航(实时游戏世界的地形大都如此，接下来我们要谈的就是这种实时地形)。 从数学的眼光来看，构成地形的网格是绝对规则的，高程数据然后附在网格点上， (网格上每个顶点都根据不同的高度在网格的法线量方向进行位移.)形成地形。这是通用的地形建模方案(modelling[^9],not rendering)，，，在这种观点下，“地形”只是一块2D面片或曲面，通过细分(比如基于lod要求，这是渲染要求)形成最终的地形tile based terrain[^10]。游戏世界或虚拟现实世界中的其它物体，比如植物，建筑，可以直接放在地形上。 (程序上地，解决地形问题，还要解决地形上的阴影产生，路径定义，障碍定义，水定义等，于是地形问题就变成了“地面”问题，在游戏中，这就是map，等再加上寻路，资源，单位，玩家，等东西后，map变成了world)

有一些“世界”是mesh based的，地形有时并不存在(它只是普通mesh)，因为整个世界只是meshs在世界空间里的组合。 当然，用多边形计算机图形学来解决的“地形问题”和“世界问题”，在最终都会变成多边形(具体到管道中，是顶点和像素)。以待渲染。 只是，用面片细分解决地形，继而解决map，甚至world的方法(tile based terrain)，和直接用mesh 解决地形，map,world的方法，同规模的东西，在渲染时，二者所用的遮盖和lod(注意遮盖和lod不是同一个意思，虽然都是加速渲染的方案)不尽相同，付出的代价也不尽相同。因为前者是面片.网格结构非常规则.所以不适合利用通常的合并顶点等方式来改变它的多边形数量.常用的LOD算法是ROAM和QuadTree等，而后者，可以直接用遮盖 这（对于“地形”来说）其中，细分面片所形成的地形还是主流，这其中有一种基于像素误差判断来LOD的方案，它其实是一类算法，有各种不同的衍生算法，基本原理都是对视点距离的判断和对局部地形表面的曲率的判断，然后程序上决定一个局部的地形在什么时候应该改变网格结构.

关于地形/地图场景管理是体现一个图形程序/引擎场景管理的重要部分，比如WOW的WDT(World Data Type)，ADT(Area Data Type)等Data Struct充其量只是场景组织，而不是场景管理，跟渲染效率相关的场景组织才是场景管理，比如WOW中对WMO(World Model Object)的渲染（以及WMO内部的场景组织结构）才能看出场景管理。

程序上的游戏中有什么：作为图形程序的部分- 游戏的场景系统(特效动画)
-------------

xx

程序上的游戏中有什么：作为图形程序的部分- 游戏的场景系统(ingame gui)
-------------

为什么说3dgameui与outgameui是本质不同的呢？raster image or video scene ?raster ui or video ui ?

3d scene is not a playback able mutilpmedia,,just renderable,,it needs inputs from the user
requires real rendering,,,,,,2


3 d 其实是一种video ui技术。

我们平常使用的ui只是位图显示系统，显示器加光珊能显示颜色就能显示界面，没有（预）渲染的成分，而视频系统d3d， 或视频界面，需要显卡功能和缓存，就是所谓的加速了，所以这两者根本不同

video ui它bypass了os的窗口机制。所以在DX节图时，我们有时看到的是一张黑图片。


游戏的抽像最高点，和工程最高点就是处理好表示与非逻辑的绘制的关系，可以类比界面范式和界面编程范式。面向对象统一了，并显式化了，抽象和工程。

video ui现在在手机平台上也越来越流行了，比如iphone的基于gpu加速的gui,,,还有qt5.0开始的基于gl es的ui scenegraph
css 完备吗，做为语言完备吗，选择符什么的够用吗
每个文件格式都是一个压缩档，，里有至关重要的xml描述
war3 gui worldeditor的原理是不是将scriptable elements用一种可拖拉的方式实现。like vtk designer 的scriptable object property,methods...
ffxi的场景是一块的,monlitch,而2d game的maps是一块一块的,逻辑上相连的地图,,2d游戏仅用过门点连接,物理上并不连接,而ffxi写真的超大型地图,,则逻辑上相连的也物理上相连,,这就会这样一种效果,,人物与地图比例永远一致,,而且,透过天花板上的洞可以看到楼上的人物的动作.
故意为了清希化,易于反工程, 和教育演示用的file formats，甚至没有加入安全，你还要做的
一门脚本语言应提供最为简便的，自动化的。类qml tagging out qtcpp logics 2 qml logics的东西
js不纯是web front language,,它其实是web common language,,,web framework language
web dev is framewoked by template engine,,,,,,,,,,which forms a common web sheduma
in a senser,,,web programming is true programming ,,casuse of its easy...
nnovative and seamless interaction between player and non-player characters is a hallmark of Source-powered games.
以及ai as gamelogic-----the virtua world social logic
world geometry,,model geometry,,,went through a different rendering and lighting path

quake2 的换client是怎么回事
quake2的logic engine和non logic engine，，以及quake3的qvm游戏逻辑体，，都是对整个游戏开发方式，，以及领域逻辑的创新！！
quake2中，modding a game，实际上是modding a gamelogic engine

a map is a channel，比如，聊天频道常以一个地图为单元，势力范围更新,data downloading，是总服务器logics的一个单元，，所以有以map为单元的map based gamelogic server，，，单机游戏常以map为一个mod -- mapsetups，多人mmrpg中也可以map为一个mod server
mpge is only codebase - shared mixedgameengine??
or with a archiet in it?

基于消息分布订阅的OO系统，本来就是为了代替传统CPP的虚函数表OO系统，所以完全可将一切逻辑利用QT obj system构建于其上。
模板的编译期，就是在最终进入运行时前，在从设计写代码到进入运行时阶段，由编译器对源程序进行了预处理，比如模板实例化，，而这些其实与编译器前端的那个代码生成不同，，是编译器级的，叠加在编译前端对代码的处理结果之上，，所以是二级过程。


[1.game主要是一种vr程序]