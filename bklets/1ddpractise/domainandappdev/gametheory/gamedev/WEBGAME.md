webgame

webgame是个为娘

我一直想发明个webgame,,,至少类webgame的为娘webgame也好，，，可是，，，发明问题不止那么一二个：
1，WEB协议（我说的不是云计算机下通用WEB协议，比如SOA等等，而仅指传统HTTP）不是实时的。即使实时，它强调的是客户端对服务器的主动作用，，这听起来很顺理成章，难道不都是客户端要求服务器给数据的吗？
问题就出在这，，它使用的是只发生一次的request/reponse
TCP子协议（任何应用TCP族的应用级协议都是TCP或UDP的子协议），是瞬间短连接，，客户端和服务器建立连接后（往往谁也不知道这个连接存在，因为它靠COOKIE维持一个会话状态供追究，，以后，我们再也不能获到得这个连接的任何情况），不可能在这里传大量数据。效率是个问题。
所以，需要专门适用于GAME的实时协议。(基于UDP或TCP，或混合UDTCP)
2，WEB服务器环境不可能作为一[来源：GameRes.com]套标准的游戏逻辑服务器存在，，iis还是apache,lamp,还是.net
vm
web环境（带专门WEB组件支持）所支持的WEB程序(web程序都是页面为单位的小粒度程序)，页面程序(任何WEB程序都是被作为最终要被转换为HTML的界面逻辑，和着后台数据参入其中的数据逻辑)的发行和制作分B/S二端，，，都没有其中任何一个地方加入游戏逻辑，，而且，无论在哪，都不可能展现复杂多变的游戏内容(as
game art content playback device)。
都这样了，，我还能怎么样呢？难道我在发明了一套realtimegameprotol的同时，还发明一套render,再改造下web服务器？
还是珍惜生命吧

qt救赎下的webgame client player

web浏览器终归不是common
explorer(比如OS的filesytem外壳),它不能支持local://,,sql://,smtp://,,它只支持http://,https://
富网页技术(js way or flash way)只是将web浏览器增加了一个外挂（在客户端，页游一般是个java
的swt或activex,它使用js与宿主web浏览器控件交互 ）
而html5 2d
canvas,websocket,,web3d,,3d加速flash或IE，等技术，做的也无非以上路线，它们将webgame
client想象成web game content player
>>在提倡云端技术的今天，很多技术尝试把3d scenes
stream技术做成服务端push到客户端的编码了的压缩流(只要网速够快，那么游戏就成了玩家点播的可交互式游戏电影，就跟放在线电影一样)，好像HTC买了一家这样的公司来着。
——————————————————————–
WEB是一种应用架构规范和开发架构规范的统称，在应用架构上，它有一切应用该有的一切，db(服务端)，gui(服务端生成，客户端渲染的htmls)，network(http,,soap)[来源：GameRes.com]，logic(pages,一共三种，想象一下用delphi开发网页程序，，第二种是在大量使用.net和java的今天的C#,JSP逻辑—–虚拟机内的web组件，要么是显式的高级组件，如java
enterprise beans)

在开发架构上，，我们在服务端写gui htmls,,写pages logic。
在发布架构上，服务端发布pages.
———————————————————————
总结：将一切做成一个狭窄的WEB浏览器（一旦要求明显，用于游戏根本就不适用），而增强技术冶标不冶本，无疑是死路一条（即使死得那么不难看，现在的网页游戏也很火）。
必须要改造浏览器，脱离它作为http web专用浏览器的原义，使之成为“general web
player”—云计算通用客户端
qt提供了所有可用的组件，甚至是产品

Re:qt救赎下的webgame

web作为应用平台，最明显的例子，，就是每个公司都有它们自己的WEB界面作为门户，，而且可以提供API供别人来开发web
apps，，这就是它们称为web os的东西

Re:qt救赎下的webgame

电视网游只是为web云计算平台增加了一个media stream server的东西

Re:qt救赎下的webgame client player

未来将以mpge为基础，以player plugin—for
web为src/main/products/player，，发明一个webgame demo :mywar @web

webgame的正确出路

首先要知道什么是框架，在我的《qt救赎下的webgame
player》和《web不是云，也不是浮云》和《我的nativecloud平台设想》三文中，我提到web是一种平台，，而框架，就是使web成为平台的那个东西，比如mvc框架的传统web,使web成为集native的dbserver,webkit之类的渲染的加模板语言控制的htmlserveir，再加作为控制器的应用领域事物server,,,这一切，都组织在django之类的框架实现所支持的page
apps中，而django这样的东西，包括zend,j2ee，都是框架的实现作为页面容器服务器存在提供服务。在这种框架下，我们可以实现很多的web
apps———used as appengine or appframework engine。

>>由于web上的传输的东西都很小，htmls,sql,都是很小的东西，语义级的逻辑，故http这样的东西可以胜任，其实http本身，也是一种语义级的逻辑。善于处理非实时的传输，，至于领域逻辑，即集成在web
server中的logicserver，，往往是事务性的逻辑，比如传输几张图片，验证几个密码什么的（不可否认的事，我们不经常用WEB协议作流媒体应用，那有专门的协议，专门的流媒体服务器，和服务技术，但却不是WEB显示界面传输SQL数据能管到的，善于管的）
由此看来，传统WEB仅是通用分布式平台，它仅将本地的三大基础应用搬上了cloud，这就是上面说到的db,gui
show（再加一个domain spefied logicsserver
这三个足于组成一个所谓的appserver了，这就是我们传统WEB到现在为止还在使用的模式）,甚至都没有为媒体传输和文件系统服务设置专门的server（web页面上欠入的图片直接用HTTP例外），，而这是不可思议的，因为如果按现行WEB的“强服务端，瘦客户端”，，如要将一部电影以点播支持交互的形式做成远程应用（这样就必须要求服务器作streaming），再比如，要做一个微端游（就要求服务器不断将客端的文件系统推送到客端，，业界纯粹用2d页游的方式来解决游戏画面的问题，，，这是传统WEB页面拉图片的方式，但不是3D大型微端游戏拉大量文件系统的长久之法），，都需要专门的“将它们做到cloud的servers”，，，
>>再比如，要做一个支持3D加速的微端游，比如业界像“云电影游戏”一样，，将游戏逻辑纯粹放在服务端生成media流，客户端仅成为一个realtime
media
player，，这种方式也是欠考究的（这就要求客户端也参与云计算，，使传统WEB提倡的强服务端瘦客户端的模式变成非服务端独大的端，），，并不需要将DX
server这样的native rendering logic也做成cloudserver（比如阿里巴巴的blender
rendering server，，不知道能用于游戏不。。）。

———————————————————————————————————————————

故，，webgame要做到与native的效果大致相同，，以一种科学合理的方式呈现，，，形成应用，，必须要[来源：GameRes.com]考虑以下这二个方面：
1，，将越来越多的本地逻辑cloud server化，，并做成框架，比如将native文件系统做成streamer
server。并设置专门的传输协议。而不仅仅是HTTP，而且可能要强化MVC，或换用别的框架。
2，，必须把一些不能做到cloud形成server的东西留在客户端，比如native rendering logic。。
3，，其它更多的事，，大部分是事务性的，，都不必做成servers。。。。这点跟传统WEB一样。。。

