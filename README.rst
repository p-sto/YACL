YACL - Yet Another C Logger
===========================

Repo contains very, very, very(!) simple C logger. Idea was to have some fun and write logger using preprocessor macros.
Tested on GCC (v5.4) and CLang (v3.8).


Usage
-----

There's nothing fancy and complicated about this implementation - just copy logger.h to your source files.

.. code:: C

    #include "logger.h"     // in file where you wish to add logging

    ...
    
    /*In your main function:*/

    logger_clean();     // before launching make sure you have clean logging file

    logger(LEVEL_INFO, "%s", "Hello World");

Logs will be printed both to stdout (stderr for LEVEL_ERROR) and to file ``execution.log``

Logger supports debug flag - if such was declared e.g. using -DDEBUG in compilation then LEVEL_DEBUG will be printed/written to log file.
Otherwise DEBUG information will not be printed/written so you can prepare debug and release builds.

Feel free to use it, modify and adjust to your own projects.
All logs are writen immediately to file (thus it makes heavy use of file descriptors).
This might be treated both as advantage and disadvantage but:

    1. It works
    2. It's simple


Example output
--------------

::

    15:39:37 [INFO] Conjugate Gradient solver using MKL.
    15:39:37 [INFO] Num of threads: 1
    15:39:53 [DEBUG] Matrix parameters:
    15:39:53 [DEBUG] Size = 589446, non-zero elements = 21758924
    15:39:53 [WARNING] Could not read properly number of devices, err=CUDA driver version is insufficient for CUDA runtime version
    15:39:53 [INFO] Launching CPU CG.
    15:40:00 [INFO] Conjugate gradient method finished within 7.061 [secs] in total 51 iterations.
