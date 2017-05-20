Class **Phalcon\\Websocket\\Server**
====================================

.. role:: raw-html(raw)
   :format: html

:raw-html:`<a href="https://github.com/dreamsxin/cphalcon7/blob/master/ext/websocket/server.c" class="btn btn-default btn-sm">Source on GitHub</a>`


.. code-block:: php

    <?php

     $server = new Phalcon\Websocket\Server(8080);
     $server->on(Phalcon\Websocket\Server::ON_ACCEPT, function($server, $conn){
         echo 'Accept'.PHP_EOL;
     });
     $server->on(Phalcon\Websocket\Server::ON_CLOSE, function($server){
         echo 'Close'.PHP_EOL;
     });
     $server->on(Phalcon\Websocket\Server::ON_DATA, function($server, $conn, $data){
         echo 'Data'.PHP_EOL;
     });
     $server->run();
    <／code>



Constants
---------

*integer* **ON_ACCEPT**

*integer* **ON_CLOSE**

*integer* **ON_DATA**

*integer* **ON_TICK**

Methods
-------

public  **__construct** ([*int* $port])

Phalcon\\Websocket\\Server constructor



public  **setEventLoop** (*Phalcon\\Websocket\\Eventloop* $eventloop)

Set external event loop



public  **serviceFd** (*unknown* $fd, *unknown* $events)

Service a socket (used with external event loop)



public  **run** ()

Launch WebSocket server



public  **stop** ()

Stop WebSocket server



public  **on** (*unknown* $event, *unknown* $callback)

Register a callback for specified event



public  **broadcast** (*unknown* $text, [*unknown* $ignored])

Broadcast a message to all connected clients



