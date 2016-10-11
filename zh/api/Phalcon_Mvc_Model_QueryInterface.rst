Interface **Phalcon\\Mvc\\Model\\QueryInterface**
=================================================

.. role:: raw-html(raw)
   :format: html

:raw-html:`<a href="https://github.com/dreamsxin/cphalcon7/blob/master/phalcon/mvc/model/queryinterface.zep" class="btn btn-default btn-sm">Source on GitHub</a>`

Phalcon\\Mvc\\Model\\QueryInterface initializer


Methods
-------

abstract public *array*  **parse** ()

Parses the intermediate code produced by Phalcon\\Mvc\\Model\\Query\\Lang generating another intermediate representation that could be executed by Phalcon\\Mvc\\Model\\Query



abstract public *mixed*  **execute** ([*array* $bindParams], [*array* $bindTypes], [*unknown* $useRawsql])

Executes a parsed PHQL statement



