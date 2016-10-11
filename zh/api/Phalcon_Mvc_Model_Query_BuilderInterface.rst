Interface **Phalcon\\Mvc\\Model\\Query\\BuilderInterface**
==========================================================

.. role:: raw-html(raw)
   :format: html

:raw-html:`<a href="https://github.com/dreamsxin/cphalcon7/blob/master/phalcon/mvc/model/query/builderinterface.zep" class="btn btn-default btn-sm">Source on GitHub</a>`

Phalcon\\Mvc\\Model\\Query\\BuilderInterface initializer


Methods
-------

abstract public *int*  **getType** ()

Gets the type of PHQL queries



abstract public :doc:`Phalcon\\Mvc\\Model\\QueryInterface <Phalcon_Mvc_Model_QueryInterface>`  **compile** ()

Compile the PHQL query



abstract public *string*  **getPhql** ()

Returns a PHQL statement built based on the builder parameters



abstract public :doc:`Phalcon\\Mvc\\Model\\QueryInterface <Phalcon_Mvc_Model_QueryInterface>`  **getQuery** ()

Returns the query built



