Final class **Phalcon\\Async\\Network\\UdpSocket**
==================================================

*implements* :doc:`Phalcon\\Async\\Network\\Socket <Phalcon_Async_Network_Socket>`

.. role:: raw-html(raw)
   :format: html

:raw-html:`<a href="https://github.com/dreamsxin/cphalcon7/blob/master/ext/async/network/udpsocket.c" class="btn btn-default btn-sm">Source on GitHub</a>`

Constants
---------

*integer* **TTL**

*integer* **MULTICAST_LOOP**

*integer* **MULTICAST_TTL**

Methods
-------

private  **__construct** ()

...


public  **__wakeup** ()

...


public static  **bind** ([*unknown* $host], [*unknown* $port])

...


public static  **connect** (*unknown* $remote_host, *unknown* $remote_port, [*unknown* $host], [*unknown* $port])

...


public static  **multicast** (*unknown* $group, *unknown* $port)

...


public  **close** ([*Throwable* $error])

...


public  **flush** ()

...


public  **getAddress** ()

...


public  **getPort** ()

...


public  **setOption** (*unknown* $option, *unknown* $value)

...


public  **receive** ([*unknown* $size])

...


public  **send** (:doc:`Phalcon\\Async\\Network\\UdpDatagram <Phalcon_Async_Network_UdpDatagram>` $datagram)

...


