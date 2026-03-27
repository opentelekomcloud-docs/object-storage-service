:original_name: obs_11_0030.html

.. _obs_11_0030:

Copy
====

All commands in this section use the Linux operating system as an example to describe how to copy files.

Assume that bucket **bucket-src** contains the following objects:

.. code-block::

   obs://bucket-src/test1.txt
   obs://bucket-src/test2.txt
   obs://bucket-src/test3.txt
   obs://bucket-src/test4.txt
   obs://bucket-src/test5.txt
   obs://bucket-src/test6.txt
   obs://bucket-src/src1/
   obs://bucket-src/src1/test7.txt
   obs://bucket-src/src2/
   obs://bucket-src/src2/test8.txt
   obs://bucket-src/src2/src3/
   obs://bucket-src/src2/src3/test9.txt

Based on the structure of objects in the bucket, different copy scenarios require different commands.

-  To copy the **test1.txt** file from the **bucket-src** bucket to the **bucket-dest** bucket, use the following command:

   .. code-block::

      ./obsutil cp obs://bucket-src/test1.txt  obs://bucket-dest

   After the copy is complete, the following object is generated in bucket **bucket-dest**:

   .. code-block::

      obs://bucket-dest/test1.txt

-  To copy the contents of the **test1.txt** file in the **bucket-src** bucket to the **test.txt** file in the **bucket-dest** bucket, use the following command:

   .. code-block::

      ./obsutil cp obs://bucket-src/test1.txt  obs://bucket-dest/test.txt

   After the copy is complete, the following object is generated in bucket **bucket-dest**:

   .. code-block::

      obs://bucket-dest/test.txt

-  To copy the **test1.txt** file in the **bucket-src** bucket to the **test** folder in the **bucket-dest** bucket, use the following command:

   .. code-block::

      ./obsutil cp obs://bucket-src/test1.txt  obs://bucket-dest/test/

   After the copy is complete, the following object is generated in bucket **bucket-dest**:

   .. code-block::

      obs://bucket-dest/test/test1.txt

-  To recursively copy the entire **src2** folder from the **bucket-src** bucket to the **bucket-dest** bucket in force mode, use the following command:

   .. code-block::

      ./obsutil cp obs://bucket-src/src2  obs://bucket-dest -r -f

   After the copy is complete, the following objects are generated in bucket **bucket-dest**:

   .. code-block::

      obs://bucket-dest/src2/
      obs://bucket-dest/src2/test8.txt
      obs://bucket-dest/src2/src3/
      obs://bucket-dest/src2/src3/test9.txt

-  To recursively copy all files and subfolders from the **src2** folder in the **bucket-src** bucket to the **bucket-dest** bucket in force mode, use the following command:

   .. code-block::

      ./obsutil cp obs://bucket-src/src2  obs://bucket-dest -r -f -flat

   After the copy is complete, the following objects are generated in bucket **bucket-dest**:

   .. code-block::

      obs://bucket-dest/test8.txt
      obs://bucket-dest/src3/
      obs://bucket-dest/src3/test9.txt
