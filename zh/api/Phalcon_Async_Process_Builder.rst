Final class **Phalcon\\Async\\Process\\Builder**
================================================

.. role:: raw-html(raw)
   :format: html

:raw-html:`<a href="https://github.com/dreamsxin/cphalcon7/blob/master/ext/async/process/builder.c" class="btn btn-default btn-sm">Source on GitHub</a>`

Constants
---------

*integer* **STDIN**

*integer* **STDOUT**

*integer* **STDERR**

Methods
-------

public  **__construct** (*unknown* $command, [*unknown* $arguments])

...


public static  **fork** (*unknown* $file)

...


public static  **shell** ([*unknown* $interactive])

...


public  **withCwd** (*unknown* $directory)

...


public  **withEnv** (*array* $env, [*unknown* $inherit])

...


public  **withStdinPipe** ()

...


public  **withStdinInherited** ([*unknown* $fd])

...


public  **withoutStdin** ()

...


public  **withStdoutPipe** ()

...


public  **withStdoutInherited** ([*unknown* $fd])

...


public  **withoutStdout** ()

...


public  **withStderrPipe** ()

...


public  **withStderrInherited** ([*unknown* $fd])

...


public  **withoutStderr** ()

...


public  **execute** ([*unknown* $arguments])

...


public  **start** ([*unknown* $arguments])

...


public  **daemon** ([*unknown* $arguments])

...


