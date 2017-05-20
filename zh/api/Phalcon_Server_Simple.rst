Class **Phalcon\\Server\\Simple**
=================================

.. role:: raw-html(raw)
   :format: html

:raw-html:`<a href="https://github.com/dreamsxin/cphalcon7/blob/master/ext/server/simple.c" class="btn btn-default btn-sm">Source on GitHub</a>`


.. code-block:: php

    <?php

     class App extends Phalcon\Application {
         public function handle($data = NULL) {
             $data = trim($data);
             if (empty($data)) {
                 return 'Please input'.PHP_EOL;
             } else {
                 return '>>> '.$data.PHP_EOL;
             }
        }
     }
     $server = new Phalcon\Server\Simple();
     $server->start(new App);



Methods
-------

public  **__construct** ([*string* $host], [*int* $port])

Phalcon\\Server\\Simple constructor



public  **start** ([:doc:`Phalcon\\Application <Phalcon_Application>` $application])

Run the Server



