:original_name: obs_11_0045.html

.. _obs_11_0045:

Archiving Log Files
===================

Function
--------

You can use this command to archive log files to a local PC or to a specified bucket.

Command Line Structure
----------------------

-  In Windows

   -  Archiving to a local PC

      .. code-block::

         obsutil archive [file_or_folder_url] [-config=xxx]

   -  Archiving to a specified bucket

      .. code-block::

         obsutil archive obs://bucket[/key] [-config=xxx]

-  In Linux or macOS

   -  Archiving to a local PC

      .. code-block::

         obsutil archive [file_or_folder_url] [-config=xxx]

   -  Archiving to a specified bucket

      .. code-block::

         obsutil archive obs://bucket[/key] [-config=xxx]

Examples
--------

-  Take the Windows OS as an example. Run the **obsutil archive** command to archive log files to the same directory where the tool is executed.

   .. code-block::

      obsutil archive

      [----------------------------------------------------------] 100.00% 15/15 35ms
      Succeed to archive log files to [D:\obsutil\obsutil_log.zip]

Parameter Description
---------------------

+-----------------------+---------------------------------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| Parameter             | Optional or Mandatory                                   | Description                                                                                                                                                                                                                                                                                                      |
+=======================+=========================================================+==================================================================================================================================================================================================================================================================================================================+
| file_or_folder_url    | Optional                                                | The path to which log files are archived. The rules are as follows:                                                                                                                                                                                                                                              |
|                       |                                                         |                                                                                                                                                                                                                                                                                                                  |
|                       |                                                         | -  If this parameter is left blank, log files are archived to the same directory where obsutil commands reside with **obsutil_log.zip** as the archive file name.                                                                                                                                                |
|                       |                                                         | -  If this parameter specifies a file or folder path that does not exist, the tool checks whether the value ends with a slash (/) or backslash (\\). If yes, a folder is created based on the path, and log files are archived to the newly created directory with **obsutil_log.zip** as the archive file name. |
|                       |                                                         | -  If this parameter specifies a file or folder path that does not exist and the value does not end with a slash (/) or backslash (\\), log files are archived to a local PC with the value as the archive file name.                                                                                            |
|                       |                                                         | -  If this parameter specifies an existing .zip file, then log files are archived to a local PC overwriting the existing file, with the value as the archive file name.                                                                                                                                          |
|                       |                                                         | -  If this parameter specifies an existing folder, then log files are archived to the specified directory with **obsutil_log.zip** as the archive file name.                                                                                                                                                     |
|                       |                                                         |                                                                                                                                                                                                                                                                                                                  |
|                       |                                                         | .. note::                                                                                                                                                                                                                                                                                                        |
|                       |                                                         |                                                                                                                                                                                                                                                                                                                  |
|                       |                                                         |    All archive files are .zip files.                                                                                                                                                                                                                                                                             |
+-----------------------+---------------------------------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| bucket                | Mandatory for archiving log files to a specified bucket | The bucket name                                                                                                                                                                                                                                                                                                  |
+-----------------------+---------------------------------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| key                   | Optional for archiving log files to a specified bucket  | The object name or object name prefix when archiving log files to a specified bucket                                                                                                                                                                                                                             |
|                       |                                                         |                                                                                                                                                                                                                                                                                                                  |
|                       |                                                         | The rules are as follows:                                                                                                                                                                                                                                                                                        |
|                       |                                                         |                                                                                                                                                                                                                                                                                                                  |
|                       |                                                         | -  If this parameter is left blank, log files are archived to the root directory of the bucket with **obsutil_log.zip** as the object name.                                                                                                                                                                      |
|                       |                                                         | -  If the value ends with a slash (/), the value is used as the object name prefix when archiving log files, and the object name is the value plus **obsutil_log.zip**. Otherwise, log files are archived with the value as the object name.                                                                     |
+-----------------------+---------------------------------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| config                | Optional (additional parameter)                         | The user-defined configuration file for executing a command. For details about parameters that can be configured, see :ref:`Configuration Parameters <obs_11_0035>`.                                                                                                                                             |
+-----------------------+---------------------------------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
