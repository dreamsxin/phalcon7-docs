Abstract class **Phalcon\\Socket**
==================================

.. role:: raw-html(raw)
   :format: html

:raw-html:`<a href="https://github.com/dreamsxin/cphalcon7/blob/master/ext/socket.c" class="btn btn-default btn-sm">Source on GitHub</a>`

A simple wrapper for PHP's socket functions


Constants
---------

*integer* **AF_UNIX**

*integer* **AF_INET**

*integer* **AF_INET6**

*integer* **SOCK_STREAM**

*integer* **SOCK_DGRAM**

*integer* **SOCK_RAW**

*integer* **SOCK_SEQPACKET**

*integer* **SOCK_RDM**

*integer* **IPPROTO_IP**

*integer* **IPPROTO_IPV6**

*integer* **SOL_SOCKET**

*integer* **SOL_TCP**

*integer* **SOL_UDP**

*integer* **SO_DEBUG**

*integer* **SO_REUSEADDR**

*integer* **SO_REUSEPORT**

*integer* **TCP_NODELAY**

*integer* **TCP_QUICKACK**

Methods
-------

public *resource*  **getSocket** ()

Gets the socket



public *int*  **getSocketId** ()

Gets the socket id



protected  **_throwSocketException** ()

Throws an socket exception



public *boolean*  **setBlocking** (*int* $flag)

Set the socket to blocking / non blocking



public *boolean*  **isBlocking** ()

Checks the socket blocking / non blocking



public *boolean*  **setOption** (*int* $level, *int* $optname, *mixed* $optval)

Set the socket to blocking / non blocking



public  **close** ()

Close the socket



public  **isClose** ()

Check if the socket close



public  **__destruct** ()

Cleans up the socket and the resource



