进程管理（Process Manager）
===========================
PHP >= 7.4 本模块弃用，请使用 Async 模块。

启动进程（Start Process）
-------------------------

.. code-block:: php

    <?php

    $process = new Phalcon\Process\Proc('ping localhost', __DIR__.'/run.pid');
    $process->reStart();
    $ret = $process->handle(function($pipe, $data) {
        // on read
        echo $data;
    }, function($pipe){
        // on send
    }, function($pipe, $error){
        // on error
    }, function(){
        // on timeout
    });
