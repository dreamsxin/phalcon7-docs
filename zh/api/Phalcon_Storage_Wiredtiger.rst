Class **Phalcon\\Storage\\Wiredtiger**
======================================

.. role:: raw-html(raw)
   :format: html

:raw-html:`<a href="https://github.com/dreamsxin/cphalcon7/blob/master/ext/storage/wiredtiger.c" class="btn btn-default btn-sm">Source on GitHub</a>`

It can be used to replace APC or local memstoraged.


Methods
-------

public  **__construct** (*string* $home, [*string* $config])

Phalcon\\Storage\\Wiredtiger constructor



public  **create** (*string* $uri, [*string* $config])

Create table



public  **open** (*string* $uri, [*string* $config])

Open table



public  **alter** (*string* $uri, [*string* $config])

Alter table



public  **drop** (*string* $uri, [*string* $config])

Drop table



public  **begin** ([*string* $config])

Open a transaction



public  **commit** ([*string* $config])

Commit a transaction



public  **rollback** ([*string* $config])

Rollback a transaction



public  **sync** ([*string* $config])

Transaction sync



