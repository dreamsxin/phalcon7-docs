服务类（Server Class）
=====================
提供了一些常用的服务类。

TCP 服务端类（TCP Server Class）
-------------------------------
:doc:`Phalcon\\Server <../api/Phalcon_Server>` 可以等待客户端的连接请求以及接收客户端发送的数据。

.. code-block:: php

    <?php
	class Server extends Phalcon\Server {
        public function onConnect(int $fd) {
        }
        public function onReceive(int $fd, string $data){
        }
        public function onSend(int $fd) {
        }
        public function onClose(int $fd) {
        }
	}
	$server = new Server(array('host' => '127.0.0.1', 'port' => 8989));
	$server->start();


HTTP 服务端类（HTTP Server Class）
---------------------------------
:doc:`Phalcon\\Server\\Http <../api/Phalcon_Server_Http>` 可以等待客户端的连接请求以及接收客户端发送的数据。

.. code-block:: php

    <?php
	class App extends Phalcon\Application {
	        public function handle($uri = NULL):Phalcon\Http\ResponseInterface{
	                return new Phalcon\Http\Response('hello');
	        }
	}
	$app = new App;
	$server = new Phalcon\Server\Http(array('host' => '127.0.0.1', 'port' => 8989));
	$server->start($app);
