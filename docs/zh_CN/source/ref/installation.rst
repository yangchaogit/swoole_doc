.. _introduction.installation:

********
如何安装？
********

版本要求
------

php 5.4.* 以上


环境依赖
------


    仅支持Linux操作系统，核心代码兼容FreeBSD，需要调整某些编译的参数和细节才能通过
    
    Linux内核版本2.3.32以上
    
    PHP5.3.10以上版本
    
    gcc4.4以上版本。核心代码兼容clang，需要关闭CPU亲和设置特性
    
    cmake2.4+,编译为libswoole.so作为C/C++库时，需要使用cmake


PECL安装（推荐）
-------------

swoole已经在 pecl.php.net 发布了，所以要安装 swoole 很简单

.. code-block:: shell
   :linenos:

   /path/to/pecl install swoole
   
   echo "extension=swoole.so" >> /path/to/php.ini


编译安装
-------
Swoole扩展是按照php标准扩展构建的，作为一只勤劳的蜜蜂的你，也可以安装最新的开发版本


.. code-block:: shell
   :linenos:
   
   git clone https://github.com/matyhtf/swoole.git
   cd swoole
   /path/to/phpize
   ./configure && make && sudo make install
   echo "extension=swoole.so" >> /path/to/php.ini


开启某些特性
---------

--enable-msgqueue，使用消息队列作为IPC通信方式，消息队列的好处是buffer区域可以很大，另外dispatch_mode=3时，消息队列天然支持争抢。使用消息队列作为IPC时，worker进程内将无法使用异步，包括异步swoole_client，task/finish，swoole_event_add，swoole_timer_add

--enable-swoole-debug，打开调试日志，开启此选项后swoole将打印各类细节的调试日志。生产环境不要启用。

--enable-sockets，增加对sockets资源的支持，依赖sockets扩展。开启此参数，swoole_event_add就可以添加sockets扩展创建的连接到swoole的事件循环中。

--enable-async-mysql，增加异步mysql支持， 依赖mysqli和mysqlnd。


依然有问题？
---------

不要气馁，加入我们的开发组QQ群(321637118)，马上免费获取帮助。
