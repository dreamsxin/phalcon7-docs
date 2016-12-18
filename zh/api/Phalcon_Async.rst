Class **Phalcon\\Async**
========================

.. role:: raw-html(raw)
   :format: html

:raw-html:`<a href="https://github.com/dreamsxin/cphalcon7/blob/master/ext/async.c" class="btn btn-default btn-sm">Source on GitHub</a>`




Constants
---------

*integer* **NOWAIT**

*integer* **MSG_NOERROR**

*integer* **MSG_EXCEPT**

Methods
-------

public static *int*  **call** (*unknown* $closure)

Called asynchronous 

.. code-block:: php

    <?php

    $async = Phalcon\Async::call(function () {
    	return 'one';
     });




public static *mixed*  **recv** (*unknown* $async)

Gets asynchronous result 

.. code-block:: php

    <?php

    $id = Phalcon\Async::call(function () {
    	return 'one';
    });
    $data = Phalcon\Async::recv($id);




public static *array*  **recvAll** ()

Gets all asynchronous result 

.. code-block:: php

    <?php

    $id = Phalcon\Async::call(function () {
    	return 'one';
    });
    $data = Phalcon\Async::recvAll();




public static *int*  **count** ()

Gets result count 

.. code-block:: php

    <?php

    Phalcon\Async::count();




public static *bool*  **clear** ()

Destroy asynchronous 

.. code-block:: php

    <?php

    Phalcon\Async::clear();




