AsAns
=====

Ask and Answer

当一个问题没有统一的答案时，你可以根据实际需求按自己的理解方式给出你的答案，无论
对错，只要能解释你的疑问，就是可参考的答案。

--------------------------------------------------------------------------------

# 嵌入式TCP/IP协议栈

  - lwip
  - uIP
  - uC/IP
  - FNET
  - Cyclone TCP
  - TinyTCP


# ESP8266较差工具链的问题：

  sudo dpkg --add-architecture i386

# Linux下启动xampp时提示另一个apache在运行,另外一个服务已经启动....

    我估计刚才是删除了lampp文件夹，并没有停止服务，问怎样才能删掉第一次安装时的服务，如mysql,apache,
    [root@localhost lampp]# /opt/lampp/lampp start
    Starting XAMPP for Linux 1.7...
    XAMPP: Another web server daemon is already running.
    XAMPP: Another MySQL daemon is already running.
    XAMPP: Another FTP daemon is already running.
    XAMPP for Linux started.
    
    用下面方法解决：
    
    查看这些服务到底有没有运行
    lsof -i:80
    lsof -i:3306
    lsof -i:21
    
    找到哪个在运行后用下面命令：
    
    pkill httpd
    pkill mysql
    pkill ftp
    
