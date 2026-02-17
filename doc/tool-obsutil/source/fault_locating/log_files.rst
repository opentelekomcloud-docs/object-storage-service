:original_name: obs_11_0056.html

.. _obs_11_0056:

Log Files
=========

Configuring Log Files
---------------------

obsutil log files include tool logs and SDK logs. You can add the following parameters to the **.obsutilconfig** file to enable the two logging functions.

-  Tool logging (records the log information generated during obsutil running): configure **utilLogPath**, **utilLogBackups**, **utilLogLevel**, and **utilMaxLogSize**.
-  SDK logging (records the log information generated when using obsutil to call OBS server-side APIs): configure **sdkLogPath**, **sdkLogBackups**, **sdkLogLevel**, and **sdkMaxLogSize**.

.. note::

   -  For details about the parameter description, see :ref:`Configuration Parameters <obs_11_0035>`.
   -  **utilLogPath** and **sdkLogPath** indicate the absolute paths of the log files, not the folders that store the log files.
   -  If **utilLogPath** and **sdkLogPath** are not specified, tool logging and SDK logging are not enabled, and therefore no log file is generated during obsutil running.
   -  Log files that are rolled over are named as follows: *filename*\ **.log.**\ *number*

.. important::

   If multiple obsutil processes are running at the same time, log files may fail to be written concurrently or may be lost. In this case, add parameter **-config** when running commands to configure an independent configuration file for each process. Make sure that **utilLogPath** and **sdkLogPath** are set to different paths for each process.

Collecting Log Files
--------------------

You can collect logs in either of the following methods:

Method 1: Use auxiliary commands by referring to :ref:`Archiving Log Files <obs_11_0045>`.

Method 2: Locate the paths specified by **utilLogPath** and **sdkLogPath** in the configuration file, and then search for the log files in the corresponding paths in the local file system.
