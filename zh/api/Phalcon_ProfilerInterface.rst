Interface **Phalcon\\ProfilerInterface**
========================================

.. role:: raw-html(raw)
   :format: html

:raw-html:`<a href="https://github.com/dreamsxin/cphalcon7/blob/master/ext/profilerinterface.c" class="btn btn-default btn-sm">Source on GitHub</a>`

Phalcon\\ProfilerInterface initializer


Methods
-------

abstract public :doc:`Phalcon\\ProfilerInterface <Phalcon_ProfilerInterface>`  **startProfile** (*string* $name, [*array* $data])

Starts the profile



abstract public :doc:`Phalcon\\ProfilerInterface <Phalcon_ProfilerInterface>`  **stopProfile** ([*string* $name])

Stops the active profile



abstract public *double*  **getTotalElapsedSeconds** ()

Returns the total time in seconds spent by the profiles



abstract public *int*  **getTotalUsageMemory** ()

Returns the amount of memory allocated spent by the profiles



abstract public *Phalcon\\Profiler\\ItemInterface[]*  **getProfiles** ()

Returns all the processed profiles



abstract public *Phalcon\\Profiler\\ItemInterface*  **getLastProfile** ()

Returns the last profile executed in the profiler



abstract public :doc:`Phalcon\\ProfilerInterface <Phalcon_ProfilerInterface>`  **reset** ()

Resets the profiler, cleaning up all the profiles



