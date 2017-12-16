Interface **Phalcon\\Paginator\\AdapterInterface**
==================================================

.. role:: raw-html(raw)
   :format: html

:raw-html:`<a href="https://github.com/dreamsxin/cphalcon7/blob/master/ext/paginator/adapterinterface.c" class="btn btn-default btn-sm">Source on GitHub</a>`

Phalcon\\Paginator\\AdapterInterface initializer


Methods
-------

abstract public  **setCurrentPage** (*int* $page)

Set the current page number



abstract public *int*  **getCurrentPage** ()

Get the current page number



abstract public  **setLimit** (*int* $limit)

Set current rows limit



abstract public *int*  **getLimit** ()

Get the current rows limit



abstract public *\stdClass*  **getPaginate** ()

Returns a slice of the resultset to show in the pagination



