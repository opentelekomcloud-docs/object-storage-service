:original_name: obs_11_0059.html

.. _obs_11_0059:

Using obsutil for Resumable Data Transfer
=========================================

obsutil supports resumable data transfer (upload, download, and copy) for large files by using the multipart algorithms for upload, download, and copy. You can set the threshold size for starting a multipart upload, download, or copy task based on your actual requirements to resume the upload, download, or copy task if the task fails or is interrupted. You can specify the threshold size for starting a multipart task in either of the following ways:

Method 1
--------

Set **defaultBigfileThreshold** in the configuration file. For details, see :ref:`Configuration Parameters <obs_11_0035>`.

Method 2
--------

Set **threshold**, a command-level parameter, when you run commands for :ref:`object uploads <obs_11_0013>`, :ref:`object downloads <obs_11_0018>`, :ref:`object copy <obs_11_0017>`, :ref:`synchronous uploads of incremental objects <obs_11_0042>`, :ref:`synchronous downloads of incremental objects <obs_11_0043>`, and :ref:`synchronous copy of incremental objects <obs_11_0044>`.

Example: **obsutil cp d:\\temp\\test.txt obs://bucket-test/key** **-threshold=52428800**

In this command:

-  **obsutil cp d:\\temp\\test.txt obs://bucket-test/key** uploads file **test.txt** in the **temp** directory under D drive to bucket **bucket-test** and renames the file **key**.
-  **-threshold=52428800** starts a multipart upload when the threshold 50 MB is reached.

The following example is based on a Windows OS:

.. code-block::

   obsutil cp d:\temp\test.txt obs://bucket-test/key -threshold=52428800

   Parallel:      3                   Jobs:          3
   Threshold:     50.00MB             PartSize:      auto
   VerifyLength:  false               VerifyMd5:     false
   CheckpointDir: xxxx

   [====================================================] 100.00% 1.68 MB/s 5s
   Upload successfully, 8.46MB, d:\temp\test.txt --> obs://bucket-test/key

.. note::

   -  Priority: Command level parameter **threshold** has higher priority than the **defaultBigfileThreshold** in the configuration file.
   -  The threshold size of a multipart task applies to single files or objects. When the size of a file or object is greater than the threshold value, the multipart algorithm is applied to the file or object.
   -  The multipart algorithm and resumable data transfer are forcibly bound together. That is, once the multipart algorithm is used, the resumable data transfer is enabled for the task.
