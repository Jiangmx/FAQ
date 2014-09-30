# 什么是EABI?

Embedded application binary interface, 即嵌入式应用二进制接口，是描述可连接目标代码，
库目标代码，可执行文件影像，如何连接，执行和调试，以及目标代码生成过程，和c, c++语言接口
的规范，是编译连接工具的基础规范，也是研究它们工作原理的基础，可惜arm的EABI迄今为止没有
完全订好。作为EABI的组成部分有过程调用规范，可执行文件格式规范，c/c++ ABI规范和调试格式
规范。

内核里面谈EABI,OABI,其实相对于系统调用的方式，当然我们所说的系统限于arm系统。


# 什么是ABI

ABI，application binary interface (ABI)，应用程序二进制接口。既然是 接口，那就是某
两种东西之间的沟通桥梁，此处有这些种情况：

  - 应用程序 <－> 操作系统；
  - 应用程序 <－> （应用程序所用到的）库
  - 应用程序各个组件之间

类似于API的作用是使得程序的代码间的兼容，ABI目的是使得程序的二进制（级别）的兼容。

# 什么是OABI 和 EABI

OABI中的O，表示“Old”，“Lagacy”，旧的，过时的，OABI就是旧的/老的ABI。

EABI中的E，表示“Embedded”，是一种新的ABI。

EABI有时候也叫做GNU EABI。

OABI和EABI都是专门针对ARM的CPU来说的。

# EABI的好处 ／ 为何要用EABI

  - 支持软件浮点和硬件实现浮点功能混用
  - 系统调用的效率更高
  - 后今后的工具更兼容
  - 软件浮点的情况下，EABI的软件浮点的效率要比OABI高很多。

# OABI和EABI的区别

两种ABI在如下方面有区别：

  - 调用规则（包括参数如何传递及如何获得返回值）
  - 系统调用的数目以及应用程序应该如何去做系统调用
  - 目标文件的二进制格式，程序库等
  - 结构体中的 填充（padding/packing）和对齐。
  - 还有

        OABI：
        * ABI flags passed to binutils: -mabi=apcs-gnu -mfpu=fpa
        * gcc -dumpmachine: arm-unknown-linux
        * objdump -x for compiled binary:
        
        private flags = 2: [APCS-32] [FPA float format] [has entry point]
        * "file" on compiled Debian binary:
        ELF 32-bit LSB executable, ARM, version 1 (ARM), for GNU/Linux 2.2.0, dynamically linked (uses shared libs), for GNU/Linux 2.2.0, stripped
        * "readelf -h | grep Flags""
        Flags: 0x0
        
        EABI：
        * ABI flags passed by gcc to binutils: -mabi=aapcs-linux -mfloat-abi=soft -meabi=4
        * gcc -dumpmachine: arm-unknown-linux-gnueabi
        * objdump -x for compiled binary:
        private flags = 4000002: [Version4 EABI] [has entry point]
        * "file" on compiled binary (under Debian):
        ELF 32-bit LSB executable, ARM, version 1 (SYSV), for GNU/Linux 2.4.17, dynamically linked (uses shared libs), for GNU/Linux 2.4.17, stripped
        * "readelf -h | grep Flags""
        Flags: 0x4000002, has entry point, Version4 EABI
    

