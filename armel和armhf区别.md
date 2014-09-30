# armel和armhf区别

 - 来自：<http://blog.csdn.net/yuanlu837/article/details/12502313>

--------------------------------------------------------------------------------


# 什么是armhf

在Ubuntu 12.04和Debian里，除了arm, armel，还出现了一个名为armhf的版本。这个东西是
什么？

众所周知，armel是目前主要的ARM ABI。armhf则是armel的一个变种，主要区别在浮点计算上。

在armel中，关于浮点数计算的约定有三种。以gcc为例，对应的-mfloat-abi参数值有三个：soft,softfp,hard。soft是指所有浮点运算全部在软件层实现，效率当然不高，适合于早期没有浮
点计算单元的ARM处理器；softfp是目前armel的默认设置，它将浮点计算交给FPU处理，但函数参
数的传递使用通用的整型寄存器而不是FPU寄存器；hard则使用FPU浮点寄存器将函数参数传递给
FPU处理。

需要注意的是，在兼容性上，soft与后两者是兼容的，但softfp和hard两种模式不兼容。默认情况
下，armel使用softfp，因此将hard模式的armel单独作为一个abi，称之为armhf。

# 价值

使用softfp模式，会存在不必要的浮点到整数、整数到浮点的转换。而使用hard模式，在每次浮点
相关函数调用时，平均能节省20个CPU周期[1]。对ARM这样每个周期都很重要的体系结构来说，这
样的提升无疑是巨大的。

在完全不改变源码和配置的情况下，在一些应用程序上，使用armhf能得到20——25%的性能提升[2]。
对一些严重依赖于浮点运算的程序，更是可以达到300%的性能提升[3]。

# 使用

armhf的开启需要硬件的支持，在Debian的wiki上要求ARMv7CPU、Thumb-2指令集以及VFP3D16浮
点处理器[4]。

在gcc的编译参数上，使用-mfloat-abi=hard -mfpu=vfp即可。

在工具上，CodeSourcery最早支持hard模式。也可已自己编译工具链[5]。

linux with armfp的历史

2010年5月20日，Konstantinos Margaritis发文称将Ubuntu Larmic移植为hard模式[6]。这
一消息后来在powerdeveloper上引发关于性能提升的讨论[7]。

2010年7月6日，Hector Oron将他与Konstantinos的邮件讨论记录发往debian-arm邮件列表[8]，
将其称之为armelfp，引起社区重视，并得到armhf这个正式名称。

2010年7月18日，非官方的debian-armhf移植工作开始[9]。

2011年11月24日，该移植开始成为debian官方活动。

目前，debian仓库中超过90%的软件已经移植完毕[10]。

Debian预计在Wheezy (7.0)发布armhf的正式版。而Ubuntu也计划在Precise Pangolin 12.04 LTS
中发布一个armhf版。

此外，对此前提到过的Toshiba AC100，目前已经有了armhf的debian和ubuntu镜像可以安装试用[11, 12]。

 

# armel和armhf

指得是arm体系中有fpu（浮点运算单元）的，有的arm没有fpu，则不能有armel和armhf两种使用
fpu的方式了。

armhf比armel硬件要求（确切的是指fpu硬件）高一点。

如果fpu硬件，达到要求的标准了就可以通过gcc的选项-mfloat-abi来指定使用哪种，

如下三种值：

soft是不用fpu计算，即使有fpu浮点运算单元也不用。

armel是softfp，用fpu计算，但是传参数用普通寄存器传，这样中断的时候，只需要保存普通寄存
器，中断负荷小，但是参数需要转换成浮点的再计算。

armhf是hard，用fpu计算，传参数用fpu中的浮点寄存器传，省去了转换性能最好，但是中断负荷高。

Kernel、rootfs、 app在使用gcc编译的时候，必须指定的一致才行。

--------------------------------------------------------------------------------

# 本文到此结束！

--------------------------------------------------------------------------------
