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
