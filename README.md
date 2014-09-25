FAQ
===

Question and Answer

当一个问题没有统一的答案时，你可以根据实际需求按自己的理解方式给出你的答案，无论
对错，只要能解释你的疑问，就是可参考的答案。

--------------------------------------------------------------------------------
# tty是什么？
    
    1. tty(终端设备的统称):
    tty一词源于Teletypes，或者teletypewriters，原来指的是电传打字机，是通过串行线
    用打印机键盘通过阅读和发送信息的东西，后来这东西被键盘与显示器取代，所以现在
    叫终端比较合适。
    
    终端是一种字符型设备，它有多种类型，通常使用tty来简称各种类型的终端设备。
    
    tty也是一个Unix命令，用来给出当前终端设备的名称。
    
    2. pty（伪造的tty):
    远程telnet到主机或使用xterm时不也需要一个终端交互么？是的，这就是pty(pseudo-tty)
    
    3. pts/ptmx(pts/ptmx结合使用，进而实现pty):
    pts(pseudo-terminal slave)是pty的实现方法，与ptmx(pseudo-terminal master)配合使用实现pty。
    
    
