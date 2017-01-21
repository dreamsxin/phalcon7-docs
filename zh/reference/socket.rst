套接字类（Socket Class）
========================
Socket 类为网络通信提供了一套常用的方法和属性。

套接字服务端类（Socket Server Class）
-------------------------------------
:doc:`Phalcon\\Socket\\Server <../api/Phalcon_Socket_Server>` 可以等待客户端的连接请求以及接收客户端发送的数据。

.. code-block:: php

    <?php
    $server = new Phalcon\Socket\Server('127.0.0.1', 8989);
    $server->run(
        function(Phalcon\Socket\Client $client){
            // Connect
        },
        function(Phalcon\Socket\Client $client, $mssage){
            // Read
            echo $mssage.PHP_EOL;
        },
        function(Phalcon\Socket\Client $client){
            // Send
            $client->write("Welcome!");
        },
        function(Phalcon\Socket\Client $client){
            // Close
        },
        function(Phalcon\Socket\Client $client){
            // Error
        },
        function(){
            // Timeout
        }
    );


套接字客户端类（Socket Client Class）
-------------------------------------
:doc:`Phalcon\\Socket\\Client <../api/Phalcon_Socket_Client>` 可以发送数据给服务端以及接收来自服务端的数据。

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
