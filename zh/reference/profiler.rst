性能分析器（Profiler）
======================

层次式性能分析器（Hierarchical Profiler）
-----------------------------------------
:doc:`Phalcon\\Xhprof <../api/Phalcon_Xhprof>` 在数据收集阶段，它跟踪调用次数与测量数据，例如运行经过的时间、CPU 计算时间和内存开销：

.. code-block:: php

    <?php

    function print_canonical($xhprof_data)
    {
        if (!is_array($xhprof_data)) {
            throw new \UnexpectedValueException("print_canonical expects an array, but %s given.", gettype($xhprof_data));
        }

        ksort($xhprof_data);
        foreach($xhprof_data as $func => $metrics) {
            echo str_pad($func, 40) . ":";
            ksort($metrics);
            foreach ($metrics as $name => $value) {
                $value = str_pad($value, 4, " ", STR_PAD_LEFT);

                echo " {$name}={$value};";
            }
            echo "\n";
        }
    }

    function bar() {
        return 1;
    }

    function foo($x) {
        $sum = 0;
        for ($idx = 0; $idx < 2; $idx++) {
            $sum += bar();
        }
        return strlen("hello: {$x}");
    }

    Phalcon\Xhprof::enable(Phalcon\Xhprof::FLAG_MEMORY | Phalcon\Xhprof::FLAG_CPU);
    foo("this is a test");
    $output = Phalcon\Xhprof::disable();
    print_canonical($output);

手动性能分析器（Manual Profiler）
---------------------------------
:doc:`Phalcon\\Profiler <../api/Phalcon_Profiler>` 一个性能分析组件，可以实现多层嵌套：

.. code-block:: php

    <?php

    $profiler = new Phalcon\Profiler();

    $profiler->startProfile('one');

    $profile = $profiler->getCurrentProfile(); // 'one'
    $profile = $profiler->getLastProfile(); // 'one'

    $profiler->startProfile('two');

    $profile = $profiler->getCurrentProfile(); // 'two'
    $profile = $profiler->getLastProfile(); // 'two'

    $profiler->stopProfile('two');

    $num = count($profiler->getProfiles()); // 1
    $profile = $profiler->getCurrentProfile(); // 'one'

    $profile = $profiler->getLastProfile(); // 'two'

    $profiler->stopProfile('one');
    $num = count($profiler->getProfiles()); // 2

DB 性能分析器（DB Profiler）
----------------------------
 :doc:`Phalcon\\Db\\Profiler <../api/Phalcon_Db_Profiler>` 组件，它被用于分析数据库的操作性能以便诊断性能问题，并发现瓶颈：

.. code-block:: php

    <?php

    use Phalcon\DB\Profiler as DbProfiler;

    $profiler = new DbProfiler();

    // 设置性能分析组件
    $connection->setProfile($profiler);

    $sql = "SELECT buyer_name, quantity, product_name "
         . "FROM buyers "
         . "LEFT JOIN products ON buyers.pid = products.id";

    // 执行SQL
    $connection->query($sql);

    // 获取最后一个分析结果
    $profile = $profiler->getLastProfile();

    echo "SQL Statement: ", $profile->getSQLStatement(), "\n";
    echo "Start Time: ", $profile->getInitialTime(), "\n";
    echo "Final Time: ", $profile->getFinalTime(), "\n";
    echo "Total Elapsed Time: ", $profile->getTotalElapsedSeconds(), "\n";
    echo "Total Usage Memory: ", $profile->getTotalUsageMemory(), "\n";

或者通过自己监听事件来实现性能分析：

.. code-block:: php

    <?php

    use Phalcon\Events\Manager as EventsManager;
    use Phalcon\Db\Profiler as DbProfiler;

    $eventsManager = new EventsManager();

    $profiler = new DbProfiler();

    // 监听所有数据库的事件
    $eventsManager->attach('db', function ($event, $connection) use ($profiler) {
        if ($event->getType() == 'beforeQuery') {
            // 操作前启动分析
            $profiler->startProfile('db', ['sqlStatement' => $connection->getSQLStatement()]);
        }
        if ($event->getType() == 'afterQuery') {
            // 操作后停止分析
            $profiler->stopProfile();
        }
    });

    // 设置事件管理器
    $connection->setEventsManager($eventsManager);

    $sql = "SELECT buyer_name, quantity, product_name "
         . "FROM buyers "
         . "LEFT JOIN products ON buyers.pid = products.id";

    // 执行SQL
    $connection->query($sql);

    // 获取最后一个分析结果
    $profile = $profiler->getLastProfile();

    echo "SQL Statement: ", $profile->getSQLStatement(), "\n";
    echo "Start Time: ", $profile->getInitialTime(), "\n";
    echo "Final Time: ", $profile->getFinalTime(), "\n";
    echo "Total Elapsed Time: ", $profile->getTotalElapsedSeconds(), "\n";
    echo "Total Usage Memory: ", $profile->getTotalUsageMemory(), "\n";

你也可以基于 :doc:`Phalcon\\Profiler <../api/Phalcon_Profiler>` 或 :doc:`Phalcon\\Db\\Profiler <../api/Phalcon_Db_Profiler>` 建立你自己的分析器类。