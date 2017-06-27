Class **Phalcon\\Db\\Profiler\\Item**
=====================================

*extends* class :doc:`Phalcon\\Profiler\\Item <Phalcon_Profiler_Item>`

*implements* :doc:`Phalcon\\Profile\\ItemInterface <Phalcon_Profile_ItemInterface>`

.. role:: raw-html(raw)
   :format: html

:raw-html:`<a href="https://github.com/dreamsxin/cphalcon7/blob/master/ext/db/profiler/item.c" class="btn btn-default btn-sm">Source on GitHub</a>`

This class identifies each profile in a Phalcon\\Db\\Profiler


Methods
-------

public  **setSQLStatement** (*string* $sqlStatement)

Sets the SQL statement related to the profile



public *string*  **getSQLStatement** ()

Returns the SQL statement related to the profile



public  **setSQLVariables** (*unknown* $sqlVariables)

Sets the SQL variables related to the profile



public *array*  **getSQLVariables** ()

Returns the SQL variables related to the profile



public  **setSQLBindTypes** (*unknown* $sqlBindTypes)

Sets the SQL bind types related to the profile



public *array*  **getSQLBindTypes** ()

Returns the SQL bind types related to the profile



public  **__construct** (*unknown* $name, [*array* $data]) inherited from Phalcon\\Profiler\\Item

Constructor for Phalcon\\Profiler\\Item



public *string*  **getName** () inherited from Phalcon\\Profiler\\Item

Returns the name



public  **setData** (*array* $data) inherited from Phalcon\\Profiler\\Item

Sets the data related to the profile



public *array*  **getData** () inherited from Phalcon\\Profiler\\Item

Returns the data related to the profile



public  **setInitialTime** (*double* $initialTime) inherited from Phalcon\\Profiler\\Item

Sets the timestamp on when the profile started



public *double*  **getInitialTime** () inherited from Phalcon\\Profiler\\Item

Returns the initial time in milseconds on when the profile started



public  **setFinalTime** (*double* $finalTime) inherited from Phalcon\\Profiler\\Item

Sets the timestamp on when the profile ended



public *double*  **getFinalTime** () inherited from Phalcon\\Profiler\\Item

Returns the initial time in milseconds on when the profile ended



public *double|null*  **getTotalElapsedSeconds** () inherited from Phalcon\\Profiler\\Item

Returns the total time in seconds spent by the profile



public  **setStartMemory** (*double* $startMemory) inherited from Phalcon\\Profiler\\Item

Sets the amount of memory allocated on when the profile started



public *double*  **getStartMemory** () inherited from Phalcon\\Profiler\\Item

Returns the amount of memory allocated on when the profile started



public  **setEndMemory** (*double* $endMemory) inherited from Phalcon\\Profiler\\Item

Sets the amount of memory allocated on when the profile ended



public *int*  **getEndMemory** () inherited from Phalcon\\Profiler\\Item

Returns the amount of memory allocated on when the profile ended



public *int*  **getTotalUsageMemory** () inherited from Phalcon\\Profiler\\Item

Returns the total time in seconds spent by the profile



