
If I want to make a game within a couple years then would it be worth my time to learn how to use the UDK? I¡¯m sure it would seem like an obvious ¡°yes¡± but I¡¯m just not sure if I should learn to use the UDK or if I should learn a language like C++ or Java or something else. In the future I would like to make a game that is a combination of Minecraft (in the aspect that you will be able to construct things) and well basically a lot of stuff I don¡¯t want to explain it but basically is the UDK worth my time or should I just make my own game engine many years from now if I learn C++? I need help deciding whether the UDK will become obsolete soon or not basically.

you should get yourself understood in the top over-alls when regarding ¡°udk intergrated way of game creating,little programming,most scripting needed¡± and ¡°cpp,computer graphic game programming step by step up,fully programming needed¡± way for a comparsion.in which:

1) cpp,graphic lib is the traditional way of ¡°natvely programmingly building up a game¡±:

it happens mainly on a solo programmer or in a team in which people master well a kind of native languages (c,cpp) and computer graphics knowledges to get started.( some bit of 3d math knowledge needed ,or even heavy 3d math knowledges to dive deeper into the graphic issues to support programming game apps better).

when he works,he reuses wildmagic,ogre(which is based on ogl,dx ¨C the api interface for the native hosting os and its language encapsulations,targeting at the game domain as the engine.)

in a sentense:above is finished in a ¡°native game programming¡± way focusing on the engine-creation (the render engine,the game graphic engine)

2) the large UDK game toolkit package districtly differs from cpp + native graphics programming way,it at least deals with 2 things:

a) The usage of scripting languages:
infact,vm language popups up firstly as the language for distributed languages like in web development domain.
But soon people find that it could be useful too when wrappering the underlayer native lib as the vm modules to use them under the vm language envirments,even taking the disvantage of vm system for consideration.and the development could become more mangerable,and easily like in web programming manner.so it was adpoted.

b) The usage of integrated game IDE.
Infact,the udk ide minus the game effect in the way ¡°Spring,Hibrate¡±to the ¡°web programming¡±in the ¡°appmodel framework¡±level with a visual manner (don¡¯t list the vb ,Delphi rad tools here,they just focus on the development lvl not the overall appmodel dev+deploy lvl) to help with the ¡°game logic configing¡±¡£

usually,you will be reminded that,game is not only a graphic app except for its graphic related parts.it also a app covering all native programming aspects(the io,thread,network,db,filesystem ,audio parts,even the AI parts),and heavly relies on the engine architecture (that means,to reuse a good engine well,you should master good cpp OO design knowledges within the engine).

Main differs :
1) Requires more on native and 2) less on native and game knowledge more on product output.could show advantages for unprofessional game makers and modders (MOD is UDK app like web app for lamp,this is also the differ between Delphi,vb VS UDK IDE in overall appmodel senses).

