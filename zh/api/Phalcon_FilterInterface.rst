Interface **Phalcon\\FilterInterface**
======================================

.. role:: raw-html(raw)
   :format: html

:raw-html:`<a href="https://github.com/dreamsxin/cphalcon7/blob/master/ext/filterinterface.c" class="btn btn-default btn-sm">Source on GitHub</a>`

Phalcon\\FilterInterface initializer


Methods
-------

abstract public :doc:`Phalcon\\FilterInterface <Phalcon_FilterInterface>`  **add** (*string* $name, *callable|closure* $handler)

Adds a user-defined filter



abstract public *mixed*  **sanitize** (*mixed* $value, *mixed* $filters, [*unknown* $noRecursive], [*array* $options])

Sanizites a value with a specified single or set of filters



abstract public *object[]*  **getFilters** ()

Return the user-defined filters in the instance



