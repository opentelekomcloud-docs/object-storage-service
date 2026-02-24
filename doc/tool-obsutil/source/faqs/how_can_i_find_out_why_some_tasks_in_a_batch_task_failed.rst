:original_name: obs_11_0078.html

.. _obs_11_0078:

How Can I Find Out Why Some Tasks in a Batch Task Failed?
=========================================================

After a batch task is completed, there will be results telling you how many tasks succeeded or failed. To find out why those tasks failed, you can check their failure result file or obsutil log file.

After a batch task is executed, its task ID will be generated. You can query the failure result file in the **.obsutil_output** directory based on the task ID. The file is named in the **cp_{failed}_report\_**\ *Time*\ **\_**\ *TaskId*\ **.txt** format and contains detailed error information about each failed task.

In addition, you can view the obsutil log file to query the error records during obsutil running. You are advised to set the log level to **DEBUG** for fault locating. For details about the log configuration and log path, see :ref:`Log Files <obs_11_0056>`.
