
>��̸��ʲô�Ƿֲ�ʽ��
��̸OS�����ʱ��̸���ֲ�ʽ����ʵ�ֲ�ʽ�ڲ�ͬ��ν����ͬ�����⡣

�ֲ�ʽPC�ֲ�ʽ����ֲ�ʽӦ�ó���ϵͳ���������ߵĽ�����ʲô����eachӦ����ʲô���޵Ĺ���

��ô����������Ҫ̸�ľ���APPSVR��APPMODEL����ġ��ֲ�ʽ��


>�ֲ�ʽ����


weakly-linked (across network boundery,process boudry,machine boudry,,�����칹boundry,by msgsys) parallel process/svr framework--------�ֲ�ʽ���ص��������ӡ�ͨѶ˫���͸�IO˫��һ�������Ǽ��䲻����ֻ������Ϣ���ֺͼ��������Ⱥ���ֲ�ʽ��Ȼ���Ǹ�msg oriented sys(�ֲ�ʽIO��Ȼ���Ǹ�asio event oriented sys),,,so how build a appmodel for it-------io��Ҫ��Э�鹤���ġ�Э�鶼��һ��msg,msg����һ��event

�����ֲ�ʽ����ʵ���ǹ��ڸ��ָ���svrs���¡������ϵĳ������svr������һ������(lpc,rpc svr)��Ҳ������һ��tcpsvr(network io svr)����������msgsvr(a system dealing with presenting the procal buffer and processing the event io)-----------event:socket buffer read/write io invacation resulted notiy event mapped into appmodel eventsys domain,,,����msg io deplex��appmodel eventsys��һ�������Ȿ��һ�����������Թ��ܡ�����ߵ�ӳ�����Ϲ�ϵ��

������cs��p2p.�Ƕ�����ߵ��ۺϿ��ǡ�

��νp2p������based on tcpsocket�£��û��ռ�����·�ɵ�һ��Э��ջ��svr��Ⱥ�ṹ��

>�ֲ�ʽ����Ϣ

�� Ϣ����ָ���ǳ���֮��ͨ������Ϣ�з������ݽ���ͨ�ţ�������ͨ��ֱ�ӵ��ñ˴���ͨ�ţ�ֱ�ӵ���ͨ������������Զ�̹��̵��õļ������Ŷ�ָ����Ӧ�ó���ͨ�� ������ͨ�š����е�ʹ�ó�ȥ�˽��պͷ���Ӧ�ó���ͬʱִ�е�Ҫ��

However, most application protocols are based on the idea of "messages";��һ��distributed appmodel��msg����based on the idea of event,,this is what libio dealt with-------tcp stream->ingoingoutgoing buffer->packet->msg


ͨ��highlvl local/dist IO��ʾ��IO���� lib...t general local/dist io present and process lib:gippl


>�ֲ�ʽ������ֲ�ʽ

���->lpc->rpc->����ͳһ��socket-msg-like based svr appmodel.��������lpc�ǲ���Ҫsocketlike msg��(idlֻ�ǵ���Э�鲻����·Э��)������Ϊ��ͳһ���ǲ����˸�socket svrһ����msg��ʾ�봦�����as the�ϲ�Ӧ�ÿ����ۣ�ͳһidl��socket protal

com server or socket server framework or hybird,com shouldt come accross network boundary(or it brings lateny,and i dontlike proxy/stub,or idl lang trans binding),local com is a transport w/o protocal(vs network socket,תЭ�����Ϊͨ��ipc,rpc������������http->soap����ȥ��)----distrubted com appsvr,or distrubuted msgqueue appsvr(msg brings�ֲ������������壬GUI��Ӧ�ÿ�������grapch/view,,,network����msg)msg����com msg��network msg

so ,a question will be,,y wanna use compent based servers or (non com based)msgqueue based libs as the dustributed appmodel frk---------as i mentioned b4,com shouldnt happen across netowk boundry,so com rpc based unform distributed appmodel is not acceptable?gcf has one implentment,zeromq has impentments 2 for rpc.
--------rpc works at programming lvl(the method recovery and invocation services),not only the compentlvl.
----------com lib is exec time loadable and linkable,while common lib is compiler time loaddable or prelinked.

>�ֲ�ʽappmodel

msgquene����һ���ֲ�ʽappmodel�����ѹ֡���.net����Ϣ�淶wcf-msmq��j2ee��jms��

�ֲ�ʽӦ��(inc the appmodel)�ı���������ʲô��the overviews engineering fullsocpe��1����ɢ�Ŀͻ��ˣ�2�����ݱ��ֹ��������û���ͬһ��Ӧ����ۡ�--------tech atleast involes asio,eventsys,worker queue,mutithread,big data trans,msg serinal,msgframing,mutilsvr payload banlance/commucation,centraledsvr or p2p corpor,urliz(ͨ��URL����Ϊ��ʲô�ܴﵽʲôЧ��),


��ͳ������򿪷��У�������ͨѶ��ص����񽻸��˳���Ա��ʵ�����ǲ��õġ�

web��������socket network��������Ϊ�����������翪���ĸ����Խ������ɿ��(j2ee��jboss,etc..)����Ӧ�÷�������Ͷ�(lamp+browswer)����Ȼ��ֻ�ж���Э��,���ң�˵ʵ������η���Ϣ����װ��Ϣ����α�֤��ճ������֤ͨѶ���������Ҹ�Ч��������Щ�������������Ȿ���Ͳ����û���̹ܵ��¡�Ӧ�ø�web����һ�������м����������


tcp���ﴫ�������Ӧ�㣬������ͬ�������߼��������д��������ơ�

msg format,proctal encode,the present
msg queue,the event io process

protocol buffer ���ԣ�����ZeroMQ��������Э���sql������Э���ʽ��Ϊ�������Ժ����������


���翪����ҵ���߼�Ӧ�ò�����δ��������Ԫ�͹�����ϢIO��Ϊ�ȣ���ЩӦ�ɿ����ɣ����ǹ�������Ӧ������β����ص�Э���ʾ��Э�鴦��

http,ftpЭ��ʵ��@cppee����generaldevkit�еģ�����appmodel�еġ�

�κ�dist appmodel���������÷�����Ⱥ����Ϣ��������




>zeromq

zeromq is a userlvl tcpstack implemnt?like fuse??

zeromq has 2 layer,the socket and socketio abstract layer,,,and the msg pattern queue layer.

what about zeromq's persist for the proctoal buffer to disk?

zeromq's "m fan in n fan out" is fact the io event deplex.zeromq is based on traditonal tcpsocket but not meant for replacing it.it developt it. to "m fan in n fan out"(vs tcpsocket's 1:1)taking whole a svr a "endpoint" but not socket binding port or connecting port.


zeromq�б�ʾ�㣨Э���ʾ���־û�������㣨router��������㣨socket pattern�������û�����network app model(protocal stack). if peers work in c/s manner then it became cs network appmodel frk,if peers work in euqal-join manner then the p2p appmodel frk.


zeromq is infact a metasvr framework�����ڽ����������ӷ�������Э��·�ɣ����ˣ��ʹ�����������ɵļ�Ⱥ����svr frasture framework���Ҵ���һ��cross svr comucation,load balancing��no singel point failure��Ч����������ʵ���û��ռ�����繤�̣������ں˵��Ǹ�tcp protal stackһ����

���ӷ����� in zeromq is the router,,,zeromq is the metasvr lib(svr's svr,,or svr based on svr),zeromq endpoint comucates not by portocals but by svr unit.

zeromq with m:n io,,,it can archives to a p2p decenternizd effect. is a server archiet framework based on a asio network lib.and a protocal marsh-customable lib(procing the msg buffer).,,,,in the biggest overall,,,its a msg framework(for msg based network appmodel).with lpc/rpc is msg based dist appmodel

zeromq��������ͻ���Ǹ�msg����msgqueueʵ���Ϻܲ��ã���Ϊof the biggest view,,,is a svr oriented lib.not msg oriented,msgֻ�����ʾ��Ķ������ﴫ�������Ӧ�еı�������appmodel��Ҳ�Ǳ�ʾ��Ķ�����not logic essinal ones.Ҫ˵����Ҫ�������ܱ�����������lpc,rpc,network io into 1: the msg oriented present and process system,event driven distributed appmodel system

>engitor dist

libsvr:asio+wlsfasio,,wlsf:weaklinked svr frastruste,,,mixed rpc+socket linked svr fransturste, ,in engitorm2 implentment,,,in proc svrs(peered ones) will use rpc,,,,,,,,,,cs svrs will use socket ones.to bkreadmes
--------------
engitor shouldnt only be appsvr,,in fact its a os and appsvr,it includes in connectsvr,like vpnd,,safesvr like ..then the appsvr..turnning os_stack_lvl_svr to distos svr,,infact its a appsvr.
