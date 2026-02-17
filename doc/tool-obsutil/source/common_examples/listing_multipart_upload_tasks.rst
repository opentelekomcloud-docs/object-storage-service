:original_name: obs_11_0032.html

.. _obs_11_0032:

Listing Multipart Upload Tasks
==============================

All commands in this section use the Linux operating system as an example to describe how to list multipart upload tasks.

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

-  Run the following command to list three multipart upload tasks in bucket **bucket-test**:

   .. code-block::

      ./obsutil ls obs://bucket-test -m -limit=3

   The returned result is listed in lexicographical order by object name as follows:

   .. code-block::

      obs://bucket-test/task1.txt uploadid1
      obs://bucket-test/task1.txt uploadid2
      obs://bucket-test/task2.txt uploadid3

-  To list the rest multipart upload tasks following **uploadid1**, the command is as follows:

   .. code-block::

      ./obsutil ls obs://bucket-test -m -limit=3 -marker=task1.txt -uploadIdMarker=uploadid1

   The returned result is listed in lexicographical order by object name and upload ID as follows:

   .. code-block::

      obs://bucket-test/task1.txt uploadid2
      obs://bucket-test/task2.txt uploadid3
      obs://bucket-test/task3.txt uploadid4
