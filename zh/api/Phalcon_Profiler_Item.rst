Class **Phalcon\\Profiler\\Item**
=================================

*implements* :doc:`Phalcon\\Profile\\ItemInterface <Phalcon_Profile_ItemInterface>`

.. role:: raw-html(raw)
   :format: html

:raw-html:`<a href="https://github.com/dreamsxin/cphalcon7/blob/master/ext/profiler/item.c" class="btn btn-default btn-sm">Source on GitHub</a>`

This class identifies each profile in a Phalcon\\Profiler


Methods
-------

public  **__construct** (*unknown* $name, [*array* $data])

Constructor for Phalcon\\Profiler\\Item



public *string*  **getName** ()

Returns the name



public  **setData** (*array* $data)

Sets the data related to the profile



public *array*  **getData** ()

Returns the data related to the profile



public  **setInitialTime** (*double* $initialTime)

Sets the timestamp on when the profile started



public *double*  **getInitialTime** ()

Returns the initial time in milseconds on when the profile started



public  **setFinalTime** (*double* $finalTime)

Sets the timestamp on when the profile ended



public *double*  **getFinalTime** ()

Returns the initial time in milseconds on when the profile ended



public *double|null*  **getTotalElapsedSeconds** ()

Returns the total time in seconds spent by the profile



public  **setStartMemory** (*double* $startMemory)

Sets the amount of memory allocated on when the profile started



public *double*  **getStartMemory** ()

Returns the amount of memory allocated on when the profile started



public  **setEndMemory** (*double* $endMemory)

Sets the amount of memory allocated on when the profile ended



public *int*  **getEndMemory** ()

Returns the amount of memory allocated on when the profile ended



public *int*  **getTotalUsageMemory** ()

Returns the total time in seconds spent by the profile



