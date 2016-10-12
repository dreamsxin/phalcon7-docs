Class **Phalcon\\Mvc\\Model\\Query\\Status**
============================================

*implements* :doc:`Phalcon\\Mvc\\Model\\Query\\StatusInterface <Phalcon_Mvc_Model_Query_StatusInterface>`

.. role:: raw-html(raw)
   :format: html

:raw-html:`<a href="https://github.com/dreamsxin/cphalcon7/blob/master/ext/mvc/model/query/status.c" class="btn btn-default btn-sm">Source on GitHub</a>`

This class represents the status returned by a PHQL statement like INSERT, UPDATE or DELETE. It offers context information and the related messages produced by the model which finally executes the operations when it fails  

.. code-block:: php

    <?php

    $phql = "UPDATE Robots SET name = :name:, type = :type:, year = :year: WHERE id = :id:";
    $status = $app->modelsManager->executeQuery($phql, array(
       'id' => 100,
       'name' => 'Astroy Boy',
       'type' => 'mechanical',
       'year' => 1959
    ));
    
     //Check if the update was successful
     if ($status->success() == true) {
       echo 'OK';
     }



Methods
-------

public  **__construct** (*boolean* $success, [:doc:`Phalcon\\Mvc\\ModelInterface <Phalcon_Mvc_ModelInterface>` $model])





public :doc:`Phalcon\\Mvc\\ModelInterface <Phalcon_Mvc_ModelInterface>`  **getModel** ()

Returns the model that executed the action



public *Phalcon\\Mvc\\Model\\MessageInterface[]*  **getMessages** ()

Returns the messages produced by a failed operation



public *boolean*  **success** ()

Allows to check if the executed operation was successful



