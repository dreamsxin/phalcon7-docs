WebSocket 组件
===============
提供 WebSocket 服务端和客户端类。

WebSocket 服务端类
-------------------
:doc:`Phalcon\\Websocket\\Server <../api/Phalcon_Websocket_Server>` 可以等待客户端的连接请求以及接收客户端发送的数据。

.. code-block:: php

    <?php

    $server = new Phalcon\Websocket\Server(8080, Phalcon\Websocket\Server::WRITE_TEXT);
    $server->on(Phalcon\Websocket\Server::ON_ACCEPT, function($server, $conn){
        echo 'Accept'.PHP_EOL;
        $conn->send('Hello world!');
    });
    $server->on(Phalcon\Websocket\Server::ON_CLOSE, function($server){
        echo 'Close'.PHP_EOL;
    });
    $server->on(Phalcon\Websocket\Server::ON_DATA, function($server, $conn, $data){
        echo 'Data '.$data.PHP_EOL;
        $server->broadcast($data, [$conn->getUid()]);
    });
    $server->on(Phalcon\Websocket\Server::ON_TICK, function($server){
        echo 'Tick'.PHP_EOL;
    });
    $server->run();

WebSocket 客户端类
-------------------
:doc:`Phalcon\\Websocket\\Client <../api/Phalcon_Websocket_Client>` 可以发送数据给服务端以及接收来自服务端的数据。

.. code-block:: php

    <?php

    $client = new Phalcon\Websocket\Client('127.0.0.1', 8080, NULL, Phalcon\Websocket\Server::WRITE_TEXT);
    $client->on(Phalcon\Websocket\Client::ON_ACCEPT, function($client, $conn){
        echo 'Accept'.PHP_EOL;
        $conn->send('Hello Server!');
    });
    $client->on(Phalcon\Websocket\Client::ON_CLOSE, function(){
        echo 'Close'.PHP_EOL;
    });
    $client->on(Phalcon\Websocket\Client::ON_DATA, function($client, $conn, $data){
        echo 'Data '.$data.PHP_EOL;
    });
    $client->on(Phalcon\Websocket\Client::ON_TICK, function($client){
        $data = 'Hello Tick!';
        echo $data.PHP_EOL;
    });
    $client->connect();
