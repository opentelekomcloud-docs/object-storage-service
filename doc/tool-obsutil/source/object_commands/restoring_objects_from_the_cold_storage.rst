:original_name: obs_11_0016.html

.. _obs_11_0016:

Restoring Objects from the Cold Storage
=======================================

Function
--------

You can use this command to restore a specified **cold** object or restore **cold** objects with a specific prefix in batches.

.. note::

   -  Object content cannot be read during restoration.
   -  After an object is restored, the time it requires before the object can be downloaded depends on the OBS server.

Command Line Structure
----------------------

-  In Windows

   -  Restoring an object

      .. code-block::

         obsutil restore obs://bucket/key [-d=1] [-t=xxx] [-versionId=xxx] [-fr] [-o=xxx] [-config=xxx]

   -  Restoring objects in batches

      .. code-block::

         obsutil restore obs://bucket[/key] -r [-f] [-v] [-d=1] [-t=xxx] [-o=xxx] [-j=1] [-config=xxx]

   -  Restoring all objects in a specific directory at a time

      .. code-block::

         obsutil restore obs://bucket/folder/ -r [-f] [-v] [-d=1] [-t=xxx] [-o=xxx] [-j=1] [-config=xxx]

-  In Linux or macOS

   -  Restoring an object

      .. code-block::

         ./obsutil restore obs://bucket/key [-d=1] [-t=xxx] [-versionId=xxx] [-fr] [-o=xxx] [-config=xxx]

   -  Restoring objects in batches

      .. code-block::

         ./obsutil restore obs://bucket[/key] -r [-f] [-v] [-d=1] [-t=xxx] [-o=xxx] [-j=1] [-config=xxx]

   -  Restoring all objects in a specific directory at a time

      .. code-block::

         ./obsutil restore obs://bucket/folder/ -r [-f] [-v] [-d=1] [-t=xxx] [-o=xxx] [-j=1] [-config=xxx]

Examples
--------

-  Take the Windows OS as an example. Run the **obsutil restore obs://bucket-test/key** command to restore a single object whose storage class is **cold**.

   .. code-block::

      obsutil restore obs://bucket-test/key
      Start at 2024-09-30 08:56:17.9537365 +0000 UTC

      Start to restore object [key] in the bucket [bucket-test] successfully, cost [252] ms, request id [0000019242250F754015F23EE0B7876E]

-  Take the Windows OS as an example. Run the **obsutil restore obs://bucket-test -r -f** command to restore objects whose storage class is **cold** in the bucket in batches.

   .. code-block::

      obsutil restore obs://bucket-test -r -f
      Start at 2024-09-30 08:57:11.3565648 +0000 UTC

      [================================================] 100.00% 3s
      Succeed count:   12        Failed count:    0
      Metrics [max cost:264 ms, min cost:54 ms, average cost:119.33 ms, average tps:19.70]
      Task id: 96f104ee-d0bf-40ff-95dd-31dec0d8f4f4

Parameter Description
---------------------

+-----------------------+-----------------------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| Parameter             | Optional or Mandatory                                                                         | Description                                                                                                                                                                                                                                                                                |
+=======================+===============================================================================================+============================================================================================================================================================================================================================================================================================+
| bucket                | Mandatory                                                                                     | The bucket name                                                                                                                                                                                                                                                                            |
+-----------------------+-----------------------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| key                   | Mandatory for restoring a single object whose storage class is **cold**                       | The name of the object to be restored or the name prefix of the objects to be restored in batches                                                                                                                                                                                          |
|                       |                                                                                               |                                                                                                                                                                                                                                                                                            |
|                       | Optional for batch restoring objects whose storage class is **cold**                          | .. note::                                                                                                                                                                                                                                                                                  |
|                       |                                                                                               |                                                                                                                                                                                                                                                                                            |
|                       |                                                                                               |    If this parameter is left blank when batch restoring objects, all objects whose storage class is **cold** in the bucket are restored.                                                                                                                                                   |
+-----------------------+-----------------------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| d                     | Optional (additional parameter)                                                               | The storage duration after objects whose storage class is **cold** are restored, in days. The value ranges from 1 to 30. The default value is **1**.                                                                                                                                       |
+-----------------------+-----------------------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| t                     | Optional (additional parameter)                                                               | The options for restoring objects. Possible values are:                                                                                                                                                                                                                                    |
|                       |                                                                                               |                                                                                                                                                                                                                                                                                            |
|                       |                                                                                               | -  standard                                                                                                                                                                                                                                                                                |
|                       |                                                                                               | -  expedited                                                                                                                                                                                                                                                                               |
|                       |                                                                                               |                                                                                                                                                                                                                                                                                            |
|                       |                                                                                               | .. note::                                                                                                                                                                                                                                                                                  |
|                       |                                                                                               |                                                                                                                                                                                                                                                                                            |
|                       |                                                                                               |    -  **expedited** indicates that objects can be quickly restored from Archive storage within 1 to 5 minutes.                                                                                                                                                                             |
|                       |                                                                                               |    -  **standard** indicates that objects can be restored from Archive storage within 3 to 5 hours.                                                                                                                                                                                        |
|                       |                                                                                               |    -  If this parameter is not configured, an expedited restore is used by default.                                                                                                                                                                                                        |
+-----------------------+-----------------------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| versionId             | Optional for restoring a single object whose storage class is **cold** (additional parameter) | The version ID of the to-be-restored object whose storage class is **cold**                                                                                                                                                                                                                |
+-----------------------+-----------------------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| fr                    | Optional for restoring a single object whose storage class is **cold** (additional parameter) | Generates an operation result file when restoring a single object whose storage class is **cold**.                                                                                                                                                                                         |
+-----------------------+-----------------------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| f                     | Optional for batch restoring objects whose storage class is **cold** (additional parameter)   | Runs in force mode.                                                                                                                                                                                                                                                                        |
+-----------------------+-----------------------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| r                     | Mandatory for batch restoring objects whose storage class is **cold** (additional parameter)  | Restores objects whose storage class is **cold** in batches by object name prefix.                                                                                                                                                                                                         |
+-----------------------+-----------------------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| v                     | Optional for batch restoring objects whose storage class is **cold** (additional parameter)   | Restores versions of objects whose storage class is **cold** in batches by object name prefix.                                                                                                                                                                                             |
+-----------------------+-----------------------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| o                     | Optional (additional parameter)                                                               | The folder that stores the result files. After the command is executed, result files (possibly success and failure files) will be created in the specified folder. The default value is **.obsutil_output**, a subfolder in the user's home directory where obsutil commands are executed. |
|                       |                                                                                               |                                                                                                                                                                                                                                                                                            |
|                       |                                                                                               | .. note::                                                                                                                                                                                                                                                                                  |
|                       |                                                                                               |                                                                                                                                                                                                                                                                                            |
|                       |                                                                                               |    -  A result file should be named as follows: **restore_{succeed \| failed}_report\_**\ *time*\ **\_**\ *TaskId*\ **.txt**.                                                                                                                                                              |
|                       |                                                                                               |                                                                                                                                                                                                                                                                                            |
|                       |                                                                                               |       By default, the maximum size of a single result file is 30 MB and the maximum number of result files that can be retained is 1,024. You can set the maximum size and number by configuring **recordMaxLogSize** and **recordBackups** in the configuration file.                     |
+-----------------------+-----------------------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| j                     | Optional for batch restoring objects whose storage class is **cold** (additional parameter)   | The maximum number of concurrent tasks for batch restoring objects whose storage class is **cold**. The default value is the value of **defaultJobs** in the configuration file.                                                                                                           |
|                       |                                                                                               |                                                                                                                                                                                                                                                                                            |
|                       |                                                                                               | .. note::                                                                                                                                                                                                                                                                                  |
|                       |                                                                                               |                                                                                                                                                                                                                                                                                            |
|                       |                                                                                               |    The value is ensured to be greater than or equal to 1.                                                                                                                                                                                                                                  |
+-----------------------+-----------------------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| config                | Optional (additional parameter)                                                               | The user-defined configuration file for executing the current command. For details about parameters that can be configured, see :ref:`Configuration Parameters <obs_11_0035>`.                                                                                                             |
+-----------------------+-----------------------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| payer                 | Optional (additional parameter)                                                               | Specifies that requester pays is enabled.                                                                                                                                                                                                                                                  |
+-----------------------+-----------------------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Response
--------

Refer to :ref:`Response <obs_11_0013__section6926520122416>` for uploading an object.
