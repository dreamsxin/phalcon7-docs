Interface **Phalcon\\Mvc\\Model\\Query\\StatusInterface**
=========================================================

.. role:: raw-html(raw)
   :format: html

:raw-html:`<a href="https://github.com/dreamsxin/cphalcon7/blob/master/phalcon/mvc/model/query/statusinterface.zep" class="btn btn-default btn-sm">Source on GitHub</a>`

Phalcon\\Mvc\\Model\\Query\\StatusInterface initializer


Methods
-------

abstract public :doc:`Phalcon\\Mvc\\ModelInterface <Phalcon_Mvc_ModelInterface>`  **getModel** ()

Returns the model which executed the action



abstract public *Phalcon\\Mvc\\Model\\MessageInterface[]*  **getMessages** ()

Returns the messages produced by a operation failed



abstract public *boolean*  **success** ()

Allows to check if the executed operation was successful



