FAQ
===

Question and Answer

--------------------------------------------------------------------------------
# tty是什么？

    基本概念：
    
    1. tty(终端设备的统称):
    tty一词源于Teletypes，或者teletypewriters，原来指的是电传打字机，是通过串行线
    用打印机键盘通过阅读和发送信息的东西，后来这东西被键盘与显示器取代，所以现在
    叫终端比较合适。
    
    终端是一种字符型设备，它有多种类型，通常使用tty来简称各种类型的终端设备。
    
    TTY设备包括虚拟控制台，串口以及伪终端设备。
    
    2. pty（虚拟终端):
    但是如果我们远程telnet到主机或使用xterm时不也需要一个终端交互么？是的，这就是虚拟终端pty(pseudo-tty)
    3. pts/ptmx(pts/ptmx结合使用，进而实现pty):
    pts(pseudo-terminal slave)是pty的实现方法，与ptmx(pseudo-terminal master)配合使用实现pty。
    
    
