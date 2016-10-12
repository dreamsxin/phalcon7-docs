Class **Phalcon\\Queue\\Beanstalk**
===================================

.. role:: raw-html(raw)
   :format: html

:raw-html:`<a href="https://github.com/dreamsxin/cphalcon7/blob/master/ext/queue/beanstalk.c" class="btn btn-default btn-sm">Source on GitHub</a>`

Class to access the beanstalk queue service. Partially implements the protocol version 1.2


Methods
-------

public  **__construct** ([*array* $options])





public  **connect** ()

...


public *string|boolean*  **put** (*string* $data, [*array* $options])

Inserts jobs into the queue



public *boolean|\Phalcon\Queue\Beanstalk\Job*  **reserve** ([*unknown* $timeout])

Reserves a job in the queue



public *string|boolean*  **choose** (*string* $tube)

Change the active tube. By default the tube is 'default'



public *string|boolean*  **watch** (*string* $tube)

Change the active tube. By default the tube is 'default'



public *boolean|array*  **stats** ()

Get stats of the Beanstalk server.



public *boolean|array*  **statsTube** (*string* $tube)

Get stats of a tube



public *boolean|\Phalcon\Queue\Beanstalk\Job*  **peekReady** ()

Inspect the next ready job.



public *boolean|Phalcon\Queue\Beanstalk\Job*  **peekDelayed** ()

Return the delayed job with the shortest delay left



public *boolean|Phalcon\Queue\Beanstalk\Job*  **peekBuried** ()

Return the next job in the list of buried jobs



protected *array*  **readStatus** ()

Reads the latest status from the Beanstalkd server



protected  **readYaml** ()

Fetch a YAML payload from the Beanstalkd server



public *string|boolean Data or `false` on error.*  **read** ([*unknown* $length])

Reads a packet from the socket. Prior to reading from the socket will check for availability of the connection.



protected *integer|boolean*  **write** ()

Writes data to the socket. Performs a connection if none is available



public *boolean*  **disconnect** ()

Closes the connection to the beanstalk server.



public  **__sleep** ()

...


public  **__wakeup** ()

...


