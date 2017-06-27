Class **Phalcon\\Profiler**
===========================

*implements* :doc:`Phalcon\\ProfilerInterface <Phalcon_ProfilerInterface>`

.. role:: raw-html(raw)
   :format: html

:raw-html:`<a href="https://github.com/dreamsxin/cphalcon7/blob/master/ext/profiler.c" class="btn btn-default btn-sm">Source on GitHub</a>`

Instances of Phalcon\\Db can generate execution profiles on SQL statements sent to the relational database. Profiled information includes execution time in miliseconds. This helps you to identify bottlenecks in your applications.  

.. code-block:: php

    <?php

    $profiler = new Phalcon\Profiler();
    
    //Set the connection profiler
    $connection->setProfiler($profiler);
    
    //Get the last profile in the profiler
    $profile = $profiler->stopProfile();
    
    echo "Data: ", $profile->getData(), "\n";
    echo "Start Time: ", $profile->getInitialTime(), "\n";
    echo "Final Time: ", $profile->getFinalTime(), "\n";
    echo "Total Elapsed Time: ", $profile->getTotalElapsedSeconds(), "\n";



Methods
-------

public  **__construct** ([*unknown* $unique])

Constructor for Phalcon\\Profiler\\Item



public *Phalcon\\Profiler\\ItemInterface*  **startProfile** (*string* $name, [*array* $data])

Starts the profile



public :doc:`Phalcon\\Profiler <Phalcon_Profiler>`  **stopProfile** ([*unknown* $name])

Stops the active profile



public *double*  **getTotalElapsedSeconds** ()

Returns the total time in seconds spent by the profiles



public *int*  **getTotalUsageMemory** ()

Returns the total time in seconds spent by the profiles



public :doc:`Phalcon\\Profiler\\Item <Phalcon_Profiler_Item>` [] **getProfiles** ()

Returns all the processed profiles



public :doc:`Phalcon\\Profiler\\Item <Phalcon_Profiler_Item>`  **getLastProfile** ()

Returns the last profile executed in the profiler



public :doc:`Phalcon\\Profiler\\Item <Phalcon_Profiler_Item>`  **getCurrentProfile** ()

Returns the current profile executed in the profiler



public :doc:`Phalcon\\Profiler <Phalcon_Profiler>`  **reset** ()

Resets the profiler, cleaning up all the profiles



