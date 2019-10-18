Final class **Phalcon\\Async\\Network\\TcpServer**
==================================================

*implements* :doc:`Phalcon\\Async\\Network\\Server <Phalcon_Async_Network_Server>`, :doc:`Phalcon\\Async\\Network\\Socket <Phalcon_Async_Network_Socket>`

.. role:: raw-html(raw)
   :format: html

:raw-html:`<a href="https://github.com/dreamsxin/cphalcon7/blob/master/ext/async/network/tcpserver.c" class="btn btn-default btn-sm">Source on GitHub</a>`

Constants
---------

*integer* **SIMULTANEOUS_ACCEPTS**

Methods
-------

private  **__construct** ()

...


public  **__wakeup** ()

...


public static  **bind** ([*unknown* $host], [*unknown* $port], [:doc:`Phalcon\\Async\\Network\\TlsServerEncryption <Phalcon_Async_Network_TlsServerEncryption>` $tls], [*unknown* $reuseport])

...


public static  **listen** ([*unknown* $host], [*unknown* $port], [:doc:`Phalcon\\Async\\Network\\TlsServerEncryption <Phalcon_Async_Network_TlsServerEncryption>` $tls], [*unknown* $reuseport])

...


public static  **import** (:doc:`Phalcon\\Async\\Network\\Pipe <Phalcon_Async_Network_Pipe>` $pipe, [:doc:`Phalcon\\Async\\Network\\TlsServerEncryption <Phalcon_Async_Network_TlsServerEncryption>` $tls])

...


public  **close** ([*Throwable* $error])

...


public  **getAddress** ()

...


public  **getPort** ()

...


public  **setOption** (*unknown* $option, *unknown* $value)

...


public  **accept** ()

...


public  **export** (:doc:`Phalcon\\Async\\Network\\Pipe <Phalcon_Async_Network_Pipe>` $pipe)

...


