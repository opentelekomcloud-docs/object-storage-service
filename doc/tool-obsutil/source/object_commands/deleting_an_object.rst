:original_name: obs_11_0021.html

.. _obs_11_0021:

Deleting an Object
==================

Function
--------

-  You can use this command to delete a specified object.
-  You can also use this command to delete objects in batches based on a specified object name prefix.

   .. warning::

      The delete operation cannot be undone.

Important Notes
---------------

In big data scenarios, parallel file systems usually have deep directory levels and each directory has a large number of files. In such case, deleting directories from parallel file systems may fail due to timeout. To address this problem, you are advised to delete directories in either of the following ways:

#. On the Hadoop client that has OBSA, an OBS client plugin, embedded, run the **hadoop fs - rmr obs://{**\ *Name of a parallel file system*\ **}/{**\ *Directory name*\ **}** command.
#. Configure a lifecycle rule for directories so that they can be deleted in background based on the preset lifecycle rule.

Command Line Structure
----------------------

-  In Windows

   -  Deleting a single object

      .. code-block::

         obsutil rm obs://bucket/key [-f] [-versionId=xxx] [-fr] [-o=xxx] [-config=xxx]

   -  Deleting objects in batches

      .. code-block::

         obsutil rm obs://bucket/[key] -r [-j=1] [-f] [-v] [-o=xxx] [-config=xxx]

-  In Linux or macOS

   -  Deleting a single object

      .. code-block::

         ./obsutil rm obs://bucket/key [-f] [-versionId=xxx] [-fr] [-o=xxx] [-config=xxx]

   -  Deleting objects in batches

      .. code-block::

         ./obsutil rm obs://bucket/[key] -r [-j=1] [-f] [-v] [-o=xxx] [-config=xxx]

Examples
--------

-  Take the Windows OS as an example. Run the **obsutil rm obs://bucket-test/key -f** command to delete a single object named **key** in bucket **bucket-test**.

   .. code-block::

      obsutil rm obs://bucket-test/key -f

      Start at 2024-09-25 04:48:10.1147483 +0000 UTC

      Delete object [key] in the bucket [bucket-test] successfully, cost [152], request id [0000016979E1D2B2860BB5181229C72C]

-  Take the Windows OS as an example. Run the **obsutil rm obs://bucket-test -r -f** command to delete all objects in bucket **bucket-test**.

   .. code-block::

      obsutil rm obs://bucket-test -r -f
      Start at 2024-09-30 08:46:55.5335644 +0000 UTC

      [===============================================] 100.00% 21s
      Succeed count:   1313      Failed count:    0
      Task id: 95936984-f81a-441a-bba0-1fd8254d9241

-  Take the Windows OS as an example. Run the **obsutil rm obs://bucket-test/key -r -f** command to delete all objects and folders prefixed with **key** in bucket **bucket-test**.

   .. code-block::

      obsutil rm obs://bucket-test/key -r -f
      Start at 2024-09-30 08:49:09.5602115 +0000 UTC

      [===============================================] 100.00% 21s
      Succeed count:   10      Failed count:    0
      Task id: 79ab59ec-7e00-4f22-8c88-465faa834125

Parameter Description
---------------------

+-----------------------+------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| Parameter             | Optional or Mandatory                                            | Description                                                                                                                                                                                                                                                                                |
+=======================+==================================================================+============================================================================================================================================================================================================================================================================================+
| bucket                | Mandatory                                                        | The bucket name                                                                                                                                                                                                                                                                            |
+-----------------------+------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| key                   | Mandatory for deleting a single object.                          | The name of the object to be deleted, or the name prefix of the objects to be deleted in batches                                                                                                                                                                                           |
|                       |                                                                  |                                                                                                                                                                                                                                                                                            |
|                       | Optional for deleting objects in batches.                        | .. note::                                                                                                                                                                                                                                                                                  |
|                       |                                                                  |                                                                                                                                                                                                                                                                                            |
|                       |                                                                  |    If this parameter is left blank when deleting objects in batches, all objects in the bucket are deleted.                                                                                                                                                                                |
+-----------------------+------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| fr                    | Optional for deleting a single object (additional parameter)     | Generates an operation result file when deleting an object.                                                                                                                                                                                                                                |
+-----------------------+------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| f                     | Optional (additional parameter)                                  | Runs in force mode.                                                                                                                                                                                                                                                                        |
+-----------------------+------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| versionId             | Optional for deleting a single object (additional parameter)     | The version ID of the object to be deleted.                                                                                                                                                                                                                                                |
+-----------------------+------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| r                     | Mandatory for deleting objects in batches (additional parameter) | Deletes objects in batches based on a specified object name prefix.                                                                                                                                                                                                                        |
|                       |                                                                  |                                                                                                                                                                                                                                                                                            |
|                       |                                                                  | .. caution::                                                                                                                                                                                                                                                                               |
|                       |                                                                  |                                                                                                                                                                                                                                                                                            |
|                       |                                                                  |    CAUTION:                                                                                                                                                                                                                                                                                |
|                       |                                                                  |    When you batch delete objects, all objects with the specified prefix will be deleted.                                                                                                                                                                                                   |
+-----------------------+------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| j                     | Optional for deleting objects in batches (additional parameter)  | The maximum number of concurrent tasks for deleting objects in batches. The default value is the value of **defaultJobs** in the configuration file.                                                                                                                                       |
|                       |                                                                  |                                                                                                                                                                                                                                                                                            |
|                       |                                                                  | .. note::                                                                                                                                                                                                                                                                                  |
|                       |                                                                  |                                                                                                                                                                                                                                                                                            |
|                       |                                                                  |    The value is ensured to be greater than or equal to 1.                                                                                                                                                                                                                                  |
+-----------------------+------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| v                     | Optional for deleting objects in batches (additional parameter)  | Deletes versions of an object and the delete markers in batches based on a specified object name prefix.                                                                                                                                                                                   |
+-----------------------+------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| o                     | Optional (additional parameter)                                  | The folder that stores the result files. After the command is executed, result files (possibly success and failure files) will be created in the specified folder. The default value is **.obsutil_output**, a subfolder in the user's home directory where obsutil commands are executed. |
|                       |                                                                  |                                                                                                                                                                                                                                                                                            |
|                       |                                                                  | .. note::                                                                                                                                                                                                                                                                                  |
|                       |                                                                  |                                                                                                                                                                                                                                                                                            |
|                       |                                                                  |    -  A result file should be named as follows: **rm_{succeed \| failed}_report\_**\ *time*\ **\_TaskId.txt**.                                                                                                                                                                             |
|                       |                                                                  |    -  By default, the maximum size of a single result file is 30 MB and the maximum number of result files that can be retained is 1,024. You can set the maximum size and number by configuring **recordMaxLogSize** and **recordBackups** in the configuration file.                     |
|                       |                                                                  |    -  If there are multiple folders and files and you need to confirm the details of a failed task, refer to the failure result file **cp_failed_report\_**\ *time*\ **\_**\ *TaskId*\ **.txt** in the result folder and the :ref:`log files <obs_11_0056>` in the log path.               |
+-----------------------+------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| bucket-cname          | Optional (additional parameter)                                  | The user-defined domain name bound to the bucket                                                                                                                                                                                                                                           |
|                       |                                                                  |                                                                                                                                                                                                                                                                                            |
|                       |                                                                  | .. note::                                                                                                                                                                                                                                                                                  |
|                       |                                                                  |                                                                                                                                                                                                                                                                                            |
|                       |                                                                  |    This parameter is only supported by obsutil 5.7.9 and later.                                                                                                                                                                                                                            |
+-----------------------+------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| config                | Optional (additional parameter)                                  | The user-defined configuration file for executing the current command. For details about parameters that can be configured, see :ref:`Configuration Parameters <obs_11_0035>`.                                                                                                             |
+-----------------------+------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| payer                 | Optional (additional parameter)                                  | Specifies that requester pays is enabled.                                                                                                                                                                                                                                                  |
+-----------------------+------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Response
--------

Refer to :ref:`Response <obs_11_0013__section6926520122416>` for uploading an object.
