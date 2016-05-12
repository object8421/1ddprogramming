web是一种集成化的mod开发部署方案，主要体现在，

它分成了BS二端，强调thin client

在服务端是cgi

在客户端仅是app player，将一切逻辑放在服务端。客端仅负责GUI logic，回显和响应。

在开发上，可以将logic designer与gui designer(admin)和开发设计(editor)集成在一端。在发布上，仅发布一个端。

而且它一切都形成了规范，如客端html5规范，服端j2ee规范，提出这种规范的好处是可以通吃桌面VM编程，移动端。

当然，有web这种bs cloud，也就有以及虚拟机的p2p cloud

像微软wcf,wpf，就是极大化了的apache,mysql等等

这样的好处是可以促成不需要p2p，却可以同时得到data p2p和logic p2p的好处。

但也有像qt5基于组件的peer2peer cloud，这样的好处不但是三端合一，而且可以以自然的方式(本地应用api不需要虚拟机接口化)跨三端开发。

具体可见《脚本与编程编程.md》的尾端，可持续集成的逻辑与p2p cloud logic

