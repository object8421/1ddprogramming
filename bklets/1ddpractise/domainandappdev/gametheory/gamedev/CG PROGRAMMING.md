cg programming

domain cg算法和应用域分析之一：media.3d基础(to be fulfilled)

cgprogramming 根本抽象在于viewing a scene

3D space完全是用数学和几何来表达的，不仅modeling用到它，连rendering（比如texture
mapping）也用到它，viewing(镜头逻辑)也用到它，（我们知道cg的抽象范式，编程范式，和应用范式，都是先建模，后渲染得到结果了事，是一种状态机）。
>>modeling与rendering其实是CG状态机的二个方面，，这就跟PC是存储和计算的状态机一样，如果modeling多一点(空间方面)，那么rendering(时间方面)就会少一点，，，是一对矛盾。
作为cg的基脚概念，这个space承载了3d,anyd空间的建设,它首先是科学的事情，决不是空间二字这么简单，历史上，几何上对空间这个数学概念的阐述是经历了艰辛的探索过程的，甚至一度将空间探索到了抽象空间的概念（这种空间在现实中并不能找到对应，不是绝对不可能，是[来源：GameRes.com]目前不能，是纯数学概念的空间），，甚至它与物理学结合，产生哲学上的讨论。
>>其实，无论是soft,or realtime nativeprogramming level rendering(dx
runtime,ogl runtime
etc..这就是被称为固定渲染管道的平台，，说它固定是因为相比可以组合shading中细节的几何和图元操作获得更灵活的“渲染过程”来说，它可以显得很灵活，说它是平台级的作用，是因为它在软件上提供了CG的状态机本身–是固定的先user
modeling后render
rendering的过程，，而shading直接用GPGPU作状态机—是灵活的无序无状态的过程不能单单称为渲染过程的过程),,还是，(based
on dx runtime或ogl runtime的)gpu scriptingprogramming level
rendering，，，都是数学的问题。。因为建模和渲染，大部分都涉及到数学。。所以CG领域的算法，只要不是特别简单的，都要向数学寻求它的答案借助数学手段来解决。是一个重数学和算法，（框架本身却很简单的编程领域，因为它处在PC编程以前处在的初级阶段，借PC的平台来完成提供一个可编程平台的任务）
>>CUDA这样的东西，强调C+脚本，在anriod这样的系统中，CPP几乎不用到。

