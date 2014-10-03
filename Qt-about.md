# Qt-about
　
关于Qt，Qt/E，Qtopia Core, Qtopia这些版本之间的区别和联系，似乎没有看到一个比较有价值
的讨论，本人现在总结一下个人的理解：

- Qt泛指Qt的所有桌面版本，比如Qt/X11，Qt Windows，Qt Mac等。由于Qt最早是在Linux中随
  着KDE流行开来  的，因此通常很多人说的Qt都指用于Linux/Unix的Qt/X11。

- Qt/E（Qt/Embedded）是用于嵌入式Linux系统的Qt版本。Qt/E去掉了X Lib的依赖而直接工
  作于Frame Buffer上，因而效率更高，但它并不是Qt的子集，而应该是超集，
  部分机制（如QCOP等）不能用于Qt/X11中。

- Qtopia是一个构建于Qt/E之上的类似桌面系统的应用环境，目前看来就是
  Qtopia Phone Editon(QPE)。相比之下，Qt/E是基础类库。

- Qtopia Core：就是原来的Qt/E，大概从Qt 4开始改名，把Qtopia Core并到Qtopia的产品线
  中去了。但实际上Qtopia Core就相当于原来的Qt/E，仍然作为基础类库。

- 另外，似乎奇趣最近又把Qtopia Core改名叫做Qt for Embedded Linux了，不知道是不是因为
  Qtopia Core搞得大家都很糊涂，没人来买的缘故。

