
game programming

本帖最后由 minlearn 于 2012-12-15 17:27 编辑

游戏编程首先不是一种游戏编程

在工业架构上，它首先是desktop programming,再是cg programming,然后才是game programming

webgame中，我们只采用web as client player as frontend,but not using
its backend server techs
我们谈到的游戏编程是桌面游戏编程，，提出这个非常重要，因为这使我们明白：游戏编程首先是桌面编程，只要弄明白了桌面编程的基础设施，，再明白作为桌面程序特例的游戏开发（它只是在桌面开发之上加了个CG
domain,ai domainlogic,,etc..），这个过程才是合理的。[来源：GameRes.com]
>>mpge的前身是2008年的gvwl，它是直奔game dev的，没有在前面提出一个general desktop
natives lib,而mpge有一个wtgl，然后才是mpge(中的game logic framework)

明白了桌面和桌面开发其实是一种平台和平台开发，那么页游，它本质是一种什么样的东西也就不难理解了，，它是以web player
as game player framework的桌面程序。
————————————
现今大部分页游都不是真正的WEBGAME，没有采用WEB的全部框架和实现，，它基本被分为前后二个端，后端sever可能不是webserver,前端player也可能只是web
explorer中的一个plugins，，，，现今的大部分页游仿佛大多数是rich ui desktop
game。而不是真正的严肃的web架构的game

cg programming,game programming

请先看我的《存不存在通用游戏引擎》一文获取前置知识
对于通用game engine的建设来说，可以为game建立一个design
level的frameworks，，但具体到算法部分，，实际上可以细分为几大子引擎的建设，对应的每个子领域都是相当巨大的，这就是:

1.game
vr（基于CG的游戏算法相关部分）:中的骨骼动画，地形，其它自然物模拟(粒子),,物理动画及效果，LOD,过程shading等等，，就算法规模来说，，可以为它们每个建立一个子引擎(用场景管理组织—-主要是高阶全局camera和LOD处理,以及全屏效果)。
2.game sr（基于ai的游戏算法相关部分）：中的robots ai techs(主要是annoted
envirment ai techs，，用来实现动作游戏中的行为AI),生物学模拟的ai
techs(主要是学术ai，用来实现策略游戏中的控制AI),可以为它们每个建立一个子引擎，用animator架构来组织(主要是agents,agents
behavier等高阶游戏[来源：GameRes.com]专用AI,,etc..)
3.game logic中的gameplay与gamesim(network based PLAYER，game sr
based NPC,,game vr based world这里面的算法几乎没有)
4.其它的game.systemprogramming(input,ingame,outgame ui,formats
parsing and loading,audio,etc..)，这里面的算法也几何没有
为了清希化起见（分开game programming的系统开发相关部分和领域逻辑部分），，把1,2,3做进一个game
engine中(通用游戏框架)，4不必特别体现出来。

游戏程序产品架构

编程，指出了程序设计和实现过程，软件，指出了程序产品和非程序产品(文档，，艺术资源。。)的产出过程。

可以用编程的方法直接提供产品。。不只是可复用品
而且，，自己应用中的东西，可以做到与OS接轨，比如explorer view自己引擎中的graphic view

游戏编程(工业界)，无非游戏程序设计（它是程序级对程序本身如何，主要是面向程序员的复用），，和游戏程序产品设计(它是脱离了程序级对程序外部应用环境的考虑，主要是面向不同用户体系的抽象)，，
软件产品设计，处在软件工业的最高层，，比如UML中最高级的设计就是组件设计，，程序产品是程序的二进制组件化形式，即是一些最终程序产品的产出，主要有：
0。引擎(游戏程序的主体部分)
1，内容创作工具（图元级，或模型级编辑与创作）
2，世界编辑器(游戏关卡，脚本逻辑写作)，比如，可视化的trigger编辑和生成
3，更多。。。
>>整合和分解在编程和软件设计中无处不在，，，上述游戏产品架构中，可以看出，内容创作，世界编辑，都可以整合为基于引擎的用户扩展，，实际上，它属于游戏程序的二级产品，所以，可以把，1，2再重新组织一下，这样就有：
0，将一切做到引擎（其它游戏产品是引擎的二级产品）
1，基于引擎产品的二级游戏[来源：GameRes.com]产品（gamemains:editorlogic,它面向用户体系中的内容创作者,moddable
logic,它面向用户体系中游戏关卡设计和发布，，playlogic,它是一些大厅逻辑，网络逻辑，面向用户体系中最终玩家），，所以往往用脚本语言完成便于动态调用，和减少编程困难。。
2，gameplugins
1,2都是产品级用户级的扩展，，0是面向程序员级的扩展。。


