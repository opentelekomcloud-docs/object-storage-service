:original_name: obs_11_0031.html

.. _obs_11_0031:

Listing
=======

All commands in this section use the Linux operating system as an example to describe how to list files.

Assume that bucket **bucket-test** contains the following objects:

.. code-block::

   obs://bucket-test/test1.txt
   obs://bucket-test/test2.txt
   obs://bucket-test/test3.txt
   obs://bucket-test/test4.txt
   obs://bucket-test/test5.txt
   obs://bucket-test/test6.txt
   obs://bucket-test/src1/
   obs://bucket-test/src1/test7.txt
   obs://bucket-test/src2/
   obs://bucket-test/src2/test8.txt

Based on the structure of objects in the bucket, different object listing scenarios require different commands.

-  To list three objects in the **bucket-test** bucket, use the following command:

   .. code-block::

      ./obsutil ls obs://bucket-test -limit=3

   The returned result is listed in lexicographical order by object name and version ID as follows:

   .. code-block::

      obs://bucket-test/test1.txt
      obs://bucket-test/test2.txt
      obs://bucket-test/test3.txt

-  To list the three objects that come after **test3.txt** in the **bucket-test** bucket, use the following command:

   .. code-block::

      ./obsutil ls obs://bucket-test -limit=3 -marker=test3.txt

   The returned result is listed in lexicographical order by object name and version ID as follows:

   .. code-block::

      obs://bucket-test/test4.txt
      obs://bucket-test/test5.txt
      obs://bucket-test/test6.txt

-  To list the files and subdirectories in the root directory of the **bucket-test** bucket in non-recursive mode, meaning files inside subdirectories are not listed, use the following command:

   .. code-block::

      ./obsutil ls obs://bucket-test -d

   The returned result is listed in lexicographical order by object name and version ID as follows:

   .. code-block::

      obs://bucket-test/test1.txt
      obs://bucket-test/test2.txt
      obs://bucket-test/test3.txt
      obs://bucket-test/test4.txt
      obs://bucket-test/test5.txt
      obs://bucket-test/test6.txt
      obs://bucket-test/src1/
      obs://bucket-test/src2/
