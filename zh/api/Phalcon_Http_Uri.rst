Class **Phalcon\\Http\\Uri**
============================

.. role:: raw-html(raw)
   :format: html

:raw-html:`<a href="https://github.com/dreamsxin/cphalcon7/blob/master/ext/http/uri.c" class="btn btn-default btn-sm">Source on GitHub</a>`


.. code-block:: php

    <?php

    $uri1 = new Uri('http://phalconphp.com/foo/bar/baz?var1=a&var2=1');
    
    $uri2 = $uri1->resolve('/last');
    echo $uri2->build(); // http://phalconphp.com/last?var1=a&var2=1
    
    $uri3 = $uri1->resolve('last');
    echo $uri3->build(); // http://phalconphp.com/foo/bar/baz/last?var1=a&var2=1
    
    $uri4 = new Uri(array(
        'scheme' => 'https',
        'host' => 'admin.example.com',
        'user' => 'john',
        'pass' => 'doe'
    ));
    
    $uri5 = $uri1->resolve($uri4);
    echo $uri5->build(); // https://john:doe@admin.example.com/foo/bar/baz?var1=a&var2=1



Methods
-------

public  **__construct** ([*mixed* $uri])

Phalcon\\Http\\Uri constructor



public *string*  **__toString** ()

Magic __toString method returns uri



public  **__unset** (*string* $key)

Magic __unset method



public  **__set** (*string* $key, *unknown* $value)

Magic __set method



public *string*  **__get** (*string* $key)

Magic __get method



public *boolean*  **__isset** (*string* $key)

Magic __isset method



public *array*  **getParts** ()

Returns parts



public *string*  **getPath** ()

Retrieve the URI path



public *string*  **build** ()

Returns uri



public  **resolve** (*unknown* $uri)

...


public  **extend** (*unknown* $uri)

...


public  **extendQuery** (*unknown* $param)

...


