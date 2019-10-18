异步调用（Asynchronous）
========================
通过 :doc:`Phalcon\\Async <../api/Phalcon_Async>` 我们可以异步调用方法。

异步调用（Called asynchronous）
-------------------------------
.. code-block:: php

    <?php
    // 默认使用 Phalcon 源码文件路径
    Phalcon\Async::setFilename('/tmp');

    $id1 = Phalcon\Async::call(function () {
        return 'one1';
    });
    $id2 = Phalcon\Async::call(function () {
        return 'one2';
    });

获取异步调用结果个数（Gets result count）
-----------------------------------------
.. code-block:: php

    <?php

    $num = Phalcon\Async::count();

获取异步调用结果（Gets asynchronous result）
--------------------------------------------
.. code-block:: php

    <?php

    $ret = Phalcon\Async::recv($id1);
    $rets = Phalcon\Async::recvAll();

协程任务（Coroutine Task）
--------------------------
.. code-block:: php

    <?php

    $task = Phalcon\Async\Task::async(function () {
        return 1;
    });
    $v = Phalcon\Async\Task::await($task);

异步进程（Async Process）
-------------------------

.. code-block:: php

    <?php

    $builder = new Phalcon\Async\ProcessBuilder(PHP_BINARY);
    $builder = $builder->withStdoutPipe();
    $builder->withStderrInherited();

    $proc = $builder->start(__DIR__.'/process.php');
    if ($proc->isRunning()) {
        echo "Running".PHP_EOL;
        $stdout = $proc->getStdout();
        try {
            if (null !== ($chunk = $stdout->read())) {
                echo $chunk;
            }
        } finally {
            $stdout->close();
        }
    }

异步 Socket （Async Socket）
----------------------------

服务器端监听：

.. code-block:: php

    <?php

    $server = Phalcon\Async\Network\TcpServer::listen('localhost', 8080);

    try {
        var_dump($server->getAddress(), $server->getPort());

        while (true) {
        $socket = $server->accept();
        if ($socket === false) {
            continue;
        }

        Phalcon\Async\Task::async(function () use ($socket) {

            try {

            $chunk = $socket->read();

            if (empty($chunk)) {
                $socket->close();
                return;
            }

            $sendchunk = 'Hello World';
            $sendchunk = \sprintf("HTTP/1.1 200 OK\r\nServer: webserver\r\nContent-Type: text/html\r\nTransfer-Encoding: chunked\r\nConnection: close\r\n\r\n%x\r\n%s\r\n0\r\n\r\n", \strlen($sendchunk), $sendchunk);
            $socket->write($sendchunk);

            } catch (\Throwable $e) {
                echo $e, "\n\n";
            } finally {
                $socket->close();
            }
        });
        }
    } finally {
        $server->close();
    }

客户端连接：

.. code-block:: php

    <?php

    $socket = TcpSocket::connect('localhost', 80);


    try {
        
        while (null !== ($chunk = $socket->read())) {
            var_dump($chunk);
        }

    } finally {
        $socket->close();
    }
