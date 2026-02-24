:original_name: obs_11_0065.html

.. _obs_11_0065:

Deleting All Multipart Upload Tasks in a Bucket
===============================================

All commands in this section use the Linux operating system as an example to describe how to delete all multipart upload tasks in a bucket.

Assume that bucket **bucket-test** contains the following multipart upload tasks:

.. code-block::

   obs://bucket-test/task1.txt uploadid1
   obs://bucket-test/task1.txt uploadid2
   obs://bucket-test/task2.txt uploadid3
   obs://bucket-test/task3.txt uploadid4
   obs://bucket-test/src1/
   obs://bucket-test/src1/task4.txt uploadid5
   obs://bucket-test/src2/
   obs://bucket-test/src2/task5.txt uploadid6

You can run the following command to delete all fragments of multipart upload tasks in the bucket at a time:

.. code-block::

   ./obsutil abort obs://bucket-test -r -f
