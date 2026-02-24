:original_name: obs_11_0020.html

.. _obs_11_0020:

Deleting a Multipart Upload Task
================================

Function
--------

-  You can use this command to delete a multipart upload task in a specified bucket by using the multipart upload ID.
-  You can also use this command to delete multipart upload tasks in batches based on a specified object name prefix.

Command Line Structure
----------------------

-  In Windows

   -  Deleting a single multipart upload task

      .. code-block::

         obsutil abort obs://bucket/key -u=xxx [-f] [-fr] [-o=xxx] [-config=xxx]

   -  Deleting multipart upload tasks in batches

      .. code-block::

         obsutil abort obs://bucket[/key] -r [-f] [-o=xxx] [-j=1] [-config=xxx]

-  In Linux or macOS

   -  Deleting a single multipart upload task

      .. code-block::

         ./obsutil abort obs://bucket/key -u=xxx [-f] [-fr] [-o=xxx] [-config=xxx]

   -  Deleting multipart upload tasks in batches

      .. code-block::

         ./obsutil abort obs://bucket[/key] -r [-f] [-o=xxx] [-j=1] [-config=xxx]

Examples
--------

-  Take the Windows OS as an example. Run the **obsutil abort obs://bucket-test/key -u=xxx -f** command to delete a single multipart upload task.

   .. code-block::

      obsutil abort obs://bucket-test/key -u=xxx -f

      Start at 2024-10-08 01:25:55.6771288 +0000 UTC

      [--------------------------------------------------] 100.00% tps:0.00 1/1 106ms
      Succeed count:      1         Failed count:       0
      Metrics [max cost:54 ms, min cost:54 ms, average cost:54.00 ms, average tps:8.77]

      Task id: 4972589c-c775-41be-a288-bbee3edaaee9

-  Take the Windows OS as an example. Run the **obsutil abort obs://bucket-test -r -f** command to delete all multipart upload tasks in the bucket in batches.

   .. code-block::

      obsutil abort obs://bucket-test -r -f
      Start at 2024-10-08 01:28:29.1980739 +0000 UTC

      [-----------------------------------------------] 100.00% tps:2924.55 3/3 202ms
      Succeed count:      3         Failed count:       0
      Metrics [max cost:148 ms, min cost:61 ms, average cost:113.33 ms, average tps:14.63]

      Task id: cd2fd08e-fc31-47d9-b4b0-9f9a3376435f

Parameter Description
---------------------

+-----------------------+------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| Parameter             | Optional or Mandatory                                                        | Description                                                                                                                                                                                                                                                                                |
+=======================+==============================================================================+============================================================================================================================================================================================================================================================================================+
| bucket                | Mandatory                                                                    | The bucket name                                                                                                                                                                                                                                                                            |
+-----------------------+------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| key                   | Mandatory for deleting a multipart upload task.                              | The object name involved in a multipart upload task to be deleted, or the name prefix of the objects involved in multipart upload tasks to be deleted in batches                                                                                                                           |
|                       |                                                                              |                                                                                                                                                                                                                                                                                            |
|                       | Optional for deleting multipart upload tasks in batches.                     | .. note::                                                                                                                                                                                                                                                                                  |
|                       |                                                                              |                                                                                                                                                                                                                                                                                            |
|                       |                                                                              |    If this parameter is left blank when deleting multipart upload tasks in batches, all multipart upload tasks in the bucket are deleted.                                                                                                                                                  |
+-----------------------+------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| u                     | Mandatory for deleting a single multipart upload task (additional parameter) | The ID of the multipart upload task to be deleted                                                                                                                                                                                                                                          |
|                       |                                                                              |                                                                                                                                                                                                                                                                                            |
|                       |                                                                              | .. note::                                                                                                                                                                                                                                                                                  |
|                       |                                                                              |                                                                                                                                                                                                                                                                                            |
|                       |                                                                              |    You can obtain the value of this parameter from :ref:`Listing Multipart Upload Tasks <obs_11_0019>`.                                                                                                                                                                                    |
+-----------------------+------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| fr                    | Optional for deleting a single multipart upload task (additional parameter)  | Generates an operation result file when deleting a multipart upload task.                                                                                                                                                                                                                  |
+-----------------------+------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| f                     | Optional (additional parameter)                                              | Runs in force mode.                                                                                                                                                                                                                                                                        |
+-----------------------+------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| r                     | Mandatory for deleting multipart upload tasks (additional parameter)         | Deletes multipart upload tasks in batches based on a specified object name prefix.                                                                                                                                                                                                         |
+-----------------------+------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| j                     | Optional for deleting multipart upload tasks (additional parameter)          | The maximum number of concurrent tasks for deleting multipart uploads in batches. The default value is the value of **defaultJobs** in the configuration file.                                                                                                                             |
|                       |                                                                              |                                                                                                                                                                                                                                                                                            |
|                       |                                                                              | .. note::                                                                                                                                                                                                                                                                                  |
|                       |                                                                              |                                                                                                                                                                                                                                                                                            |
|                       |                                                                              |    The value is ensured to be greater than or equal to 1.                                                                                                                                                                                                                                  |
+-----------------------+------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| o                     | Optional (additional parameter)                                              | The folder that stores the result files. After the command is executed, result files (possibly success and failure files) will be created in the specified folder. The default value is **.obsutil_output**, a subfolder in the user's home directory where obsutil commands are executed. |
|                       |                                                                              |                                                                                                                                                                                                                                                                                            |
|                       |                                                                              | .. note::                                                                                                                                                                                                                                                                                  |
|                       |                                                                              |                                                                                                                                                                                                                                                                                            |
|                       |                                                                              |    -  A result file should be named as follows: **abort_{succeed \| failed}_report\_**\ *time*\ **\_TaskId.txt**.                                                                                                                                                                          |
|                       |                                                                              |    -  By default, the maximum size of a single result file is 30 MB and the maximum number of result files that can be retained is 1,024. You can set the maximum size and number by configuring **recordMaxLogSize** and **recordBackups** in the configuration file.                     |
+-----------------------+------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| config                | Optional (additional parameter)                                              | The user-defined configuration file for executing the current command. For details about parameters that can be configured, see :ref:`Configuration Parameters <obs_11_0035>`.                                                                                                             |
+-----------------------+------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| payer                 | Optional (additional parameter)                                              | Specifies that requester pays is enabled.                                                                                                                                                                                                                                                  |
+-----------------------+------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Response
--------

Refer to :ref:`Response <obs_11_0013__section6926520122416>` for uploading an object.
