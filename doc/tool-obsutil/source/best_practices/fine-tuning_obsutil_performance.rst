:original_name: obs_11_0052.html

.. _obs_11_0052:

Fine-Tuning obsutil Performance
===============================

By default, obsutil uploads, downloads, and copies files or objects whose size is greater than 50 MB in multiple parts. :ref:`Table 1 <obs_11_0052__table8301721164611>` details related parameters in the **.obsutilconfig** file.

.. _obs_11_0052__table8301721164611:

.. table:: **Table 1** Multipart-related parameters

   +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter                         | Description                                                                                                                                                                                                                                                |
   +===================================+============================================================================================================================================================================================================================================================+
   | defaultBigfileThreshold           | Indicates the threshold for triggering multipart tasks, in bytes. If the size of a file to be uploaded, downloaded, or copied is greater than the threshold, the file is uploaded, downloaded, or copied in multiple parts. The default value is **50MB**. |
   +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | defaultPartSize                   | Size of each part, in bytes. The default value is **auto**.                                                                                                                                                                                                |
   |                                   |                                                                                                                                                                                                                                                            |
   |                                   | .. note::                                                                                                                                                                                                                                                  |
   |                                   |                                                                                                                                                                                                                                                            |
   |                                   |    -  For a multipart upload and copy, the value ranges from **100KB** to **5GB**.                                                                                                                                                                         |
   |                                   |    -  For multipart download, the value is unrestricted.                                                                                                                                                                                                   |
   +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | defaultParallels                  | Maximum number of concurrent tasks in the multipart mode. The default value is 5.                                                                                                                                                                          |
   +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Generally, multipart tasks not only speed up transmission but also allow you to resume failed tasks. By default, the part size of a multipart task can be automatically adjusted by the obsutil in the **auto** mode. In practice, however, to further improve the upload and download performance, you can adjust the part size according to the file size and the network conditions, to obtain the maximum transmission efficiency and ensure the successful completion of a transmission task.

Adjust the number of concurrent tasks in the multipart mode according to the following formula:

**defaultParallels = Min(Number of CPUs x 2, Object size/defaultPartSize x 1.5)**

In the upload, download, and copy commands, parameters **-p** and **-ps** are used to modify the number of concurrent tasks in the multipart mode and part size respectively, and then deliver the multipart task based on the parameter values configured in the command. The default values in the configuration file are used if you do not set them in a command.

Adjust the number of concurrent tasks in the multipart mode according to the following formula:

**p = Min(Number of CPUs x 2, Object size/ps x 1.5)**

For batch upload and download tasks, adjust the maximum number of concurrent tasks in a multipart upload, indicated by the parameter **defaultJobs (-j)**, for better performance.

If you have a large number of **small files** (each is usually several MB) to be uploaded or downloaded, set **defaultJobs (-j)** to a larger value for better performance. In this case, adjusting **defaultParallels (-p)** and **defaultPartSize (-ps)** may be ineffective.

If you want to upload or download **large files**, set **defaultParallels (-p)** and **defaultPartSize (-ps)** to a larger value for better performance. However, if there are too many concurrent tasks (calculated from **defaultJobs** x **defaultParallels**), the upload and download performance may deteriorate because of resource switchover and preemption between threads, and some tasks may fail due to network fluctuations.

.. note::

   -  Resources of a running host are limited. Therefore, if the number of concurrent tasks in the multipart mode is set too large, the performance of obsutil upload, download, or copy may deteriorate due to resource switchover and preemption between threads. In this case, you need to adjust the values of **defaultParallels** (**-p**) and **defaultPartSize** (**-ps**) based on the actual file size and network status. To perform a pressure test, lower the two values at first, and then gradually increase them to determine the optimal values.
   -  If the values of **defaultParallels** (**-p**) and **defaultPartSize** (**-ps**) are too large, an EOF error may occur due to network instability. In this case, set the two parameters to smaller values.
   -  If a batch operation is performed, the destination object size can be set to the average size of the objects to be operated.
   -  If a batch task fails due to timeout, EOF, and other common network issues, retry the task through an incremental operation (specifically, configuring parameter **-u** in the **cp** command). You can also restore the failed task (by configuring parameter **-recover** in the **cp** command) based on the generated task ID.
