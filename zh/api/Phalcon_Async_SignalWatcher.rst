Final class **Phalcon\\Async\\SignalWatcher**
=============================================

.. role:: raw-html(raw)
   :format: html

:raw-html:`<a href="https://github.com/dreamsxin/cphalcon7/blob/master/ext/async/signalwatcher.c" class="btn btn-default btn-sm">Source on GitHub</a>`

Constants
---------

*integer* **SIGHUP**

*integer* **SIGINT**

*integer* **SIGQUIT**

*integer* **SIGKILL**

*integer* **SIGTERM**

*integer* **SIGUSR1**

*integer* **SIGUSR2**

Methods
-------

public  **__construct** (*unknown* $signum)

...


public  **close** ([*Throwable* $error])

...


public  **awaitSignal** ()

...


public static  **isSupported** (*unknown* $signum)

...


public static  **raise** (*unknown* $signum)

...


