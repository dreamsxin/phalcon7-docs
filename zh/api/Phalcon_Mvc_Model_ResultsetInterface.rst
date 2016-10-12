Interface **Phalcon\\Mvc\\Model\\ResultsetInterface**
=====================================================

.. role:: raw-html(raw)
   :format: html

:raw-html:`<a href="https://github.com/dreamsxin/cphalcon7/blob/master/ext/mvc/model/resultsetinterface.c" class="btn btn-default btn-sm">Source on GitHub</a>`

Phalcon\\Mvc\\Model\\ResultsetInterface initializer


Methods
-------

abstract public *int*  **getType** ()

Returns the internal type of data retrieval that the resultset is using



abstract public :doc:`Phalcon\\Mvc\\ModelInterface <Phalcon_Mvc_ModelInterface>`  **getFirst** ()

Get first row in the resultset



abstract public :doc:`Phalcon\\Mvc\\ModelInterface <Phalcon_Mvc_ModelInterface>`  **getLast** ()

Get last row in the resultset



abstract public  **setIsFresh** (*boolean* $isFresh)

Set if the resultset is fresh or an old one cached



abstract public *boolean*  **isFresh** ()

Tell if the resultset if fresh or an old one cached



abstract public :doc:`Phalcon\\Cache\\BackendInterface <Phalcon_Cache_BackendInterface>`  **getCache** ()

Returns the associated cache for the resultset



abstract public *array*  **toArray** ()

Returns a complete resultset as an array, if the resultset has a big number of rows it could consume more memory than currently it does.



