:original_name: obs_11_0006.html

.. _obs_11_0006:

Quick Start
===========

This section uses the Linux OS as an example to describe how to use obsutil to perform basic operations in OBS. For details, see .

Prerequisites
-------------

-  You have obtained obsutil and completed :ref:`initial configuration <obs_11_0005>`.
-  The directory saving obsutil is accessed.

Procedure
---------

#. Run the **./obsutil mb obs://bucket-test** command to create a bucket named **bucket-test** in the region.

   .. code-block::

      ./obsutil mb obs://bucket-test

      Create bucket [bucket-test] successfully!

#. Run the **./obsutil cp /temp/test.txt obs://bucket-test/test.txt** command to upload the **test.txt** file to bucket **bucket-test**.

   .. code-block::

      ./obsutil cp /temp/test.txt obs://bucket-test/test.txt

      Parallel:      5                   Jobs:          5
      Threshold:     52428800            PartSize:      5242880
      VerifyLength:  false               VerifyMd5:     false
      CheckpointDir: /temp/.obsutil_checkpoint

      test.txt:[==============================================] 100.00% 48.47 KB/s 0s
      Upload successfully, 4.44KB, /temp/test.txt --> obs://bucket-test1/test.txt

   .. note::

      To upload local folder **test** to the OBS bucket, run the following command:

      .. code-block::

         ./obsutil cp /test/ obs://bucket-test -r -f

      -  For details about the **cp** command, see :ref:`Uploading an Object <obs_11_0013>`.
      -  For more upload scenarios, see :ref:`Upload <obs_11_0028>`.

#. Run the **./obsutil cp obs://bucket-test/test.txt** **/temp/test1.txt** command to download **test.txt** from bucket **bucket-test** to a local PC.

   .. code-block::

      ./obsutil cp obs://bucket-test/test.txt /temp/test1.txt

      Parallel:      5                   Jobs:          5
      Threshold:     52428800            PartSize:      5242880
      VerifyLength:  false               VerifyMd5:     false
      CheckpointDir: /temp/.obsutil_checkpoint

      test.txt:[=============================================] 100.00% 775.52 KB/s 0s
      Download successfully, 4.44KB, obs://bucket-test1/test.txt --> /temp/test1.txt

   .. note::

      To download directory **test** from the OBS bucket to the local folder **temp**, run the following command:

      .. code-block::

         ./obsutil cp obs://bucket-test/test /temp -r -f

      -  For details about the **cp** command, see :ref:`Downloading an Object <obs_11_0018>`.
      -  For more download scenarios, see :ref:`Download <obs_11_0029>`.

#. Run the **./obsutil rm obs://bucket-test/test.txt -f** command to delete object **test.txt** from bucket **bucket-test**.

   .. code-block::

      ./obsutil rm obs://bucket-test/test.txt -f

      Delete object [test.txt] in the bucket [bucket-test] successfully!

#. Run the **./obsutil rm obs://bucket-test -f** command to delete bucket **bucket-test**.

   .. code-block::

      ./obsutil rm obs://bucket-test -f

      Delete bucket [bucket-test] successfully!
