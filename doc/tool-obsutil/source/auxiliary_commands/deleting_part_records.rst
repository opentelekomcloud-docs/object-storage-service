:original_name: obs_11_0024.html

.. _obs_11_0024:

Deleting Part Records
=====================

Function
--------

You can use this command to delete part records from a specified directory.

Command Line Structure
----------------------

-  In Windows

   .. code-block::

      obsutil clear [checkpoint_dir] [-u] [-d] [-c] [-config=xxx]

-  In Linux or macOS

   .. code-block::

      ./obsutil clear [checkpoint_dir] [-u] [-d] [-c] [-config=xxx]

Examples
--------

-  Take the Windows OS as an example. Run the **obsutil clear -u** command to delete the part records of multipart upload tasks in the default directory.

   .. code-block::

      obsutil clear -u

      Clear checkpoint files for uploading in folder [xxxxx]
      Start at 2024-10-08 01:49:37.6541204 +0000 UTC
      [==================================================================] 100.00% 0s
      Succeed files is:   1         Failed files is:    0

Parameter Description
---------------------

+-----------------------+---------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| Parameter             | Optional or Mandatory           | Description                                                                                                                                                          |
+=======================+=================================+======================================================================================================================================================================+
| checkpoint_dir        | Optional                        | The folder where the part records reside. The default value is **.obsutil_checkpoint**, the same subfolder where obsutil commands reside.                            |
+-----------------------+---------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| u                     | Optional (additional parameter) | Deletes the part records of all multipart upload tasks.                                                                                                              |
|                       |                                 |                                                                                                                                                                      |
|                       |                                 | .. note::                                                                                                                                                            |
|                       |                                 |                                                                                                                                                                      |
|                       |                                 |    At the same time, the system attempts to delete the multipart upload tasks in the part records.                                                                   |
+-----------------------+---------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| d                     | Optional (additional parameter) | Deletes the part records of all multipart download tasks.                                                                                                            |
|                       |                                 |                                                                                                                                                                      |
|                       |                                 | .. note::                                                                                                                                                            |
|                       |                                 |                                                                                                                                                                      |
|                       |                                 |    At the same time, the system attempts to delete the fragments in the part records.                                                                                |
+-----------------------+---------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| c                     | Optional (additional parameter) | Deletes the part records of all multipart copy tasks.                                                                                                                |
|                       |                                 |                                                                                                                                                                      |
|                       |                                 | .. note::                                                                                                                                                            |
|                       |                                 |                                                                                                                                                                      |
|                       |                                 |    At the same time, the system attempts to delete the multipart copy tasks in the part records.                                                                     |
+-----------------------+---------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| config                | Optional (additional parameter) | The user-defined configuration file for executing a command. For details about parameters that can be configured, see :ref:`Configuration Parameters <obs_11_0035>`. |
+-----------------------+---------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------+

.. note::

   You must configure at least one among the **u**, **d** and **c** parameters.
