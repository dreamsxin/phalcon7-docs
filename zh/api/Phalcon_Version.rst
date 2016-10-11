Class **Phalcon\\Version**
==========================

.. role:: raw-html(raw)
   :format: html

:raw-html:`<a href="https://github.com/dreamsxin/cphalcon7/blob/master/phalcon/version.zep" class="btn btn-default btn-sm">Source on GitHub</a>`

This class allows to get the installed version of the framework


Methods
-------

protected static  **_getVersion** ()

Area where the version number is set. The format is as follows: ABBCCDE A - Major version B - Med version (two digits) C - Min version (two digits) D - Special release: 1 = Alpha, 2 = Beta, 3 = RC, 4 = Stable E - Special release version i.e. RC1, Beta2 etc.



public static *string*  **get** ()

Returns the active version (string) 

.. code-block:: php

    <?php

     echo Phalcon\Version::get();




public static *int*  **getId** ()

Returns the numeric active version 

.. code-block:: php

    <?php

     echo Phalcon\Version::getId();




