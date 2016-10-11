安装（Installation）
====================
作为PHP C拓展形式的Phalcon，需要一个略微不同于传统PHP的库或框架的安装方法。你可以选择一个当前系统的一个二进制包下载，或者使用源代码构建它。

Windows
-------
Phalcon7 不支持 Windows 系统。

Linux/Solaris
-------------
在Linux/Solaris系统下，你能很轻易从源代码编译和安装这个拓展:

基本要求（Requirements）
^^^^^^^^^^^^^^^^^^^^^^^^
必要的包:

* PHP >= 7.0 development resources
* GCC compiler (Linux/Solaris)
* Git (如果不是已经安装在你的系统，且你没有从Github上下载这个包并通过FTP/SFTP上传到你的服务器上)

编译（Compilation）
^^^^^^^^^^^^^^^^^^^
创建扩展:

.. code-block:: bash

    git clone --depth=1 git://github.com/dreamsxin/cphalcon7.git
    cd cphalcon7/ext
    phpize
    ./configure
    make && sudo make install

添加扩展到你的php配置文件，然后重启Web服务器，如果你使用 php-fpm，则重启 php-fpm。

Mac OS X
--------
同上

FreeBSD
-------
同上

安装说明（Installation Notes）
------------------------------
常见Web服务器的安装说明：

.. toctree::
    :maxdepth: 1

    apache
    nginx
    cherokee
    built-in
