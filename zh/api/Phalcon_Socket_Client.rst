Class **Phalcon\\Socket\\Client**
=================================

*extends* abstract class :doc:`Phalcon\\Socket <Phalcon_Socket>`

.. role:: raw-html(raw)
   :format: html

:raw-html:`<a href="https://github.com/dreamsxin/cphalcon7/blob/master/ext/socket/client.c" class="btn btn-default btn-sm">Source on GitHub</a>`


.. code-block:: php

    <?php

    $client = new Phalcon\Socket\Client('127.0.0.1', 8989);
    if ($client->connect()) {
        $client->write('Hello world!');
        while($ret = $client->read(1024, PHP_NORMAL_READ)) {
              echo $ret;
        }
    } else {
        echo 'connect fail'.PHP_EOL;
    }



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

public  **__construct** (*unknown* $address, [*unknown* $port], [*unknown* $domain], [*unknown* $type], [*unknown* $protocol])

Phalcon\\Socket\\Client constructor



public *boolean*  **connect** ()

Connect to a socket



public *string*  **read** (*unknown* $legnth, [*int* $type])

Reads a maximum of length bytes from a socket



public :doc:`Phalcon\\Socket\\Client <Phalcon_Socket_Client>`  **write** (*string* $buffer, [*int* $length])

Write to a socket



public *string*  **recv** (*unknown* $legnth, *int* $flag)

Receives data from a connected socket



public :doc:`Phalcon\\Socket\\Client <Phalcon_Socket_Client>`  **send** (*string* $buffer, *int* $length, *int* $flag)

Sends data to a connected socket



public *boolean*  **keepAlive** ()

Enable keepalive



public *boolean*  **shutdown** ()

Shutdown



public  **close** ()

Close



public *resource*  **getSocket** () inherited from Phalcon\\Socket

Gets the socket



protected  **_throwSocketException** () inherited from Phalcon\\Socket

Throws an socket exception



public *boolean*  **setBlocking** (*int* $flag) inherited from Phalcon\\Socket

Set the socket to blocking / non blocking



public *boolean*  **isBlocking** () inherited from Phalcon\\Socket

Checks the socket blocking / non blocking



public *boolean*  **setOption** (*int* $level, *int* $optname, *mixed* $optval) inherited from Phalcon\\Socket

Set the socket to blocking / non blocking



public  **isClose** () inherited from Phalcon\\Socket

Check if the socket close



public  **__destruct** () inherited from Phalcon\\Socket

Cleans up the socket and the resource



