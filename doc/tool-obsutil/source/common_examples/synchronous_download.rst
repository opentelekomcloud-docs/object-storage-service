:original_name: obs_11_0047.html

.. _obs_11_0047:

Synchronous Download
====================

All commands in this section use the Linux operating system as an example to describe how to perform synchronous download operations.

Assume that bucket **bucket-test** contains the following objects:

.. code-block::

   obs://bucket-test/src1/
   obs://bucket-test/src1/test3.txt
   obs://bucket-test/src1/src2/
   obs://bucket-test/src1/src2/test1.txt
   obs://bucket-test/src1/src2/test2.txt
   obs://bucket-test/src1/src3/

Assume that a local folder is in the following structure:

.. code-block::

   └── src1
       └── test3.txt

Based on the structure of the preceding local folder and objects in the bucket, different synchronous download scenarios require different commands.

-  To synchronize all files and subfolders in the **src1** folder in bucket **bucket-test** to the local **src1** folder, the command is as follows:

   .. code-block::

      ./obsutil sync obs://bucket-test/src1  /src1

   After the synchronization is successful, the following files are generated in the local **src1** folder:

   .. code-block::

      └── src1
          ├── src2
              ├── test1.txt
              └── test2.txt
          ├── src3
          └── test3.txt
