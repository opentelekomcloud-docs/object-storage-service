:original_name: obs_11_0057.html

.. _obs_11_0057:

Result Lists
============

Configuring Result Lists
------------------------

Result files are generated when batch tasks complete. By default, they are saved to the subfolder **.obsutil_output** in the home directory of the user who executes obsutil commands. You can specify another folder to save them by setting the additional parameter **-o** when executing a command.

Viewing Result Lists
--------------------

Result files are classified into success, failure, and warning files. The naming rule is as follows: *Operation* **\_{succeed \| failed \| warning}_report\_** *Time* **\_**\ *TaskId*\ **.txt**. For example, the name of the result file for successfully uploading a folder is **cp_succeed_report_20190417021908_fbbc83e3-98ac-4d19-b23a-64023b1e0c34.txt**, among which, **fbbc83e3-98ac-4d19-b23a-64023b1e0c34** indicates the task ID.

.. note::

   -  If the number of successes, failures, or warnings is zero, the corresponding result file is not generated.
   -  The task ID of a result list is unique for each operation.
   -  If there are multiple folders and files and you need to confirm the details of a failed task, refer to the failure result file **cp_failed_report\_**\ *time*\ **\_**\ *TaskId*\ **.txt** in the result folder and the :ref:`log files <obs_11_0056>` in the log path.
   -  The maximum size of a single result file is 30 MB.
   -  obsutil can retain a maximum of 1,024 result files and does not automatically clear these files. Once the limit is reached, the task stops running. To prevent the batch operation efficiency from being reduced by too many result files, you need to periodically archive and back up the result files in **.obsutil_output** to another folder.
