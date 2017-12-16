Class **Phalcon\\Process\\Proc**
================================

.. role:: raw-html(raw)
   :format: html

:raw-html:`<a href="https://github.com/dreamsxin/cphalcon7/blob/master/ext/process/proc.c" class="btn btn-default btn-sm">Source on GitHub</a>`

Pro for Phalcon\\Process procs


Constants
---------

*integer* **MODE_NONE**

*integer* **MODE_TTY**

*integer* **MODE_PTY**

*integer* **STATUS_READY**

*integer* **STATUS_STARTED**

*integer* **STATUS_STOP**

*integer* **STATUS_TERMINATED**

*integer* **STDIN**

*integer* **STDOUT**

*integer* **STDERR**

*integer* **SIGKILL**

*integer* **SIGTERM**

Methods
-------

public  **__construct** (*unknown* $command, [*unknown* $pidFile], [*unknown* $cwd], [*array* $env], [*unknown* $timeout], [*array* $options])

Phalcon\\Process\\Proc constructor



public  **__destruct** ()

...


public  **setMode** (*unknown* $mode)

Sets the mode.



public *array*  **getDescriptors** ()

Creates the descriptors needed by the proc_open.



public *boolean*  **isPtySupported** ()

Returns whether PTY is supported on the current operating system.



public  **start** ()

Starts the process and returns after writing the input to STDIN. This method blocks until all STDIN data is sent to the process then it returns while the process runs in the background. The termination of the process can be awaited with wait(). The callback receives the type of output (out or err) and some bytes from the output in real-time while writing the standard input to the process. It allows to have feedback from the independent process during execution.



public *boolean*  **stop** ([*unknown* $timeout], [*unknown* $signal])

Stops the process.



public  **close** ()

...


public  **reStart** ()

Restarts the process



public *boolean true if the process is currently running, false otherwise*  **isRunning** ()

Checks if the process is currently running.



public *boolean*  **update** ([*unknown* $blocking])

Updates the status of the process, reads pipes.



public  **getCommandForPid** (*unknown* $pid)

...


public  **getStarttimeForPid** (*unknown* $pid)

...


public  **getStatForPid** (*unknown* $pid)

...


public  **checkTimeout** ()

Performs a check between the timeout definition and the time the process started In case you run a background process (with the start method), you should trigger this method regularly to ensure the process timeout



public *int|null The process id if running, null otherwise*  **getPid** ()

Returns the Pid (process identifier), if applicable.



public *boolean*  **wait** ()

Waits for the process to terminate



public *boolean*  **read** (*int* $type, *boolean* $blocking)

Reads data in file handles and pipes



public *boolean*  **write** (*unknown* $data, [*unknown* $type])

Writes data to stdin



public  **handle** ([*callable* $onrecv], [*callable* $onsend], [*callable* $onerror], [*callable* $ontimeout], [*int* $timeout])

Handle the process



protected *bool*  **hasSystemCallBeenInterrupted** ()

Returns true if a system call has been interrupted



public *boolean*  **setBlocking** (*unknown* $flag)

Set streams to blocking / non blocking



