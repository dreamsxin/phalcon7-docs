Class **Phalcon\\Db\\Profiler**
===============================

*extends* class :doc:`Phalcon\\Profiler <Phalcon_Profiler>`

*implements* :doc:`Phalcon\\ProfilerInterface <Phalcon_ProfilerInterface>`

.. role:: raw-html(raw)
   :format: html

:raw-html:`<a href="https://github.com/dreamsxin/cphalcon7/blob/master/ext/db/profiler.c" class="btn btn-default btn-sm">Source on GitHub</a>`

Instances of Phalcon\\Db can generate execution profiles on SQL statements sent to the relational database. Profiled information includes execution time in miliseconds. This helps you to identify bottlenecks in your applications.  

.. code-block:: php

    <?php

    $profiler = new Phalcon\Db\Profiler();
    
    //Set the connection profiler
    $connection->setProfiler($profiler);
    
    $sql = "SELECT buyer_name, quantity, product_name
    FROM buyers LEFT JOIN products ON
    buyers.pid=products.id";
    
    //Execute a SQL statement
    $connection->query($sql);
    
    //Get the last profile in the profiler
    $profile = $profiler->getLastProfile();
    
    echo "SQL Statement: ", $profile->getSQLStatement(), "\n";
    echo "Start Time: ", $profile->getInitialTime(), "\n";
    echo "Final Time: ", $profile->getFinalTime(), "\n";
    echo "Total Elapsed Time: ", $profile->getTotalElapsedSeconds(), "\n";



Methods
-------

public :doc:`Phalcon\\Db\\Profiler\\Item <Phalcon_Db_Profiler_Item>`  **startProfile** (*string* $name, [*array* $data])

Starts the profile of a SQL sentence



public *integer*  **getNumberTotalStatements** ()

Returns the total number of SQL statements processed



public  **__construct** ([*unknown* $unique]) inherited from Phalcon\\Profiler

Constructor for Phalcon\\Profiler\\Item



public :doc:`Phalcon\\Profiler <Phalcon_Profiler>`  **stopProfile** ([*unknown* $name]) inherited from Phalcon\\Profiler

Stops the active profile



public *double*  **getTotalElapsedSeconds** () inherited from Phalcon\\Profiler

Returns the total time in seconds spent by the profiles



public *int*  **getTotalUsageMemory** () inherited from Phalcon\\Profiler

Returns the total time in seconds spent by the profiles



public :doc:`Phalcon\\Profiler\\Item <Phalcon_Profiler_Item>` [] **getProfiles** () inherited from Phalcon\\Profiler

Returns all the processed profiles



public :doc:`Phalcon\\Profiler\\Item <Phalcon_Profiler_Item>`  **getLastProfile** () inherited from Phalcon\\Profiler

Returns the last profile executed in the profiler



public :doc:`Phalcon\\Profiler\\Item <Phalcon_Profiler_Item>`  **getCurrentProfile** () inherited from Phalcon\\Profiler

Returns the current profile executed in the profiler



public :doc:`Phalcon\\Profiler <Phalcon_Profiler>`  **reset** () inherited from Phalcon\\Profiler

Resets the profiler, cleaning up all the profiles



