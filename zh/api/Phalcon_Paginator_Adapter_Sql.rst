Class **Phalcon\\Paginator\\Adapter\\Sql**
==========================================

*implements* :doc:`Phalcon\\Paginator\\AdapterInterface <Phalcon_Paginator_AdapterInterface>`

.. role:: raw-html(raw)
   :format: html

:raw-html:`<a href="https://github.com/dreamsxin/cphalcon7/blob/master/phalcon/paginator/adapter/sql.zep" class="btn btn-default btn-sm">Source on GitHub</a>`

Pagination using a SQL as source of data  

.. code-block:: php

    <?php

     $sql = "SELECT * FROM robots WHERE type = :type LIMIT :limit OFFSET :offset ";
     $sql2 = "SELECT COUNT(*) rowcount WHERE type = :type FROM robots";
    
     $bind = ['type' => 'google'];
    
     $paginator = new \Phalcon\Paginator\Adapter\Sql(array(
                     "db" => $this->db,
                     "sql" => $sql,
                     "total_sql" => $sql2,
                     "bind" => $bind,
                     "limit" => 20,
                     "page" => $page
     ));



Methods
-------

public  **__construct** (*array* $config)





public *stdClass*  **getPaginate** ()

Returns a slice of the resultset to show in the pagination



public :doc:`Phalcon\\Paginator\\Adapter\\Sql <Phalcon_Paginator_Adapter_Sql>`  $this Fluent interface **setLimit** (*int* $limit)

Set current rows limit



public *int $limit*  **getLimit** ()

Get current rows limit



public  **setCurrentPage** (*int* $page)

Set current page number



public  **getCurrentPage** ()

Get current page number



public :doc:`Phalcon\\Paginator\\Adapter\\Sql <Phalcon_Paginator_Adapter_Sql>`  $this Fluent interface **setDb** (:doc:`Phalcon\\Db\\AdapterInterface <Phalcon_Db_AdapterInterface>` $db)

Set query builder object



public :doc:`Phalcon\\Db\\AdapterInterface <Phalcon_Db_AdapterInterface>`  $db **getDb** ()

Get query builder object



