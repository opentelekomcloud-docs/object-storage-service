:original_name: obs_11_0028.html

.. _obs_11_0028:

Upload
======

All commands in this section use the Linux operating system as an example to describe how to upload files.

Assume that a local folder is in the following structure:

.. code-block::

   └── src1
       ├── src2
           ├── test1.txt
           └── test2.txt
       ├── src3
       └── test3.txt

Based on the preceding folder structure, different upload scenarios require different commands.

-  To upload the **test3.txt** file in the local **src1** folder to the root directory of bucket **bucket-test**, the command is as follows:

   .. code-block::

      ./obsutil cp /src1/test3.txt  obs://bucket-test

   After the upload completes, the following object is generated in the bucket:

   .. code-block::

      ./obs://bucket-test/test3.txt

-  To upload the **test3.txt** file in the local **src1** folder to the root directory of bucket **bucket-test** and rename it to **aaa.txt**, the command is as follows:

   .. code-block::

      ./obsutil cp /src1/test3.txt  obs://bucket-test/aaa.txt

   After the upload completes, the following object is generated in the bucket:

   .. code-block::

      ./obs://bucket-test/aaa.txt

-  To upload the **test3.txt** file in the local **src1** folder to the **src** folder in bucket **bucket-test**, the command is as follows:

   .. code-block::

      ./obsutil cp /src1/test3.txt  obs://bucket-test/src/

   After the upload completes, the following object is generated in the bucket:

   .. code-block::

      ./obs://bucket-test/src/test3.txt

-  To recursively upload the entire local **src2** folder to the root directory of bucket **bucket-test** in force mode, the command is as follows:

   .. code-block::

      ./obsutil cp /src1/src2  obs://bucket-test -r -f

   After the upload completes, the following objects are generated in the bucket:

   .. code-block::

      obs://bucket-test/src2/
      obs://bucket-test/src2/test1.txt
      obs://bucket-test/src2/test2.txt

-  To recursively upload the entire local **src1** folder to the **src** folder in bucket **bucket-test** in force mode, the command is as follows:

   .. code-block::

      ./obsutil cp /src1  obs://bucket-test/src -r -f

   After the upload completes, the following objects are generated in the bucket:

   .. code-block::

      obs://bucket-test/src/src1/
      obs://bucket-test/src/src1/src2/
      obs://bucket-test/src/src1/src2/test1.txt
      obs://bucket-test/src/src1/src2/test2.txt
      obs://bucket-test/src/src1/src3/
      obs://bucket-test/src/src1/test3.txt

-  To recursively upload the all files and subfolders in the local **src1** folder to the **src** folder in bucket **bucket-test** in force mode, the command is as follows:

   .. code-block::

      ./obsutil cp /src1  obs://bucket-test/src -r -f -flat

   After the upload completes, the following objects are generated in the bucket:

   .. code-block::

      obs://bucket-test/src/
      obs://bucket-test/src/src2/
      obs://bucket-test/src/src2/test1.txt
      obs://bucket-test/src/src2/test2.txt
      obs://bucket-test/src/src3/
      obs://bucket-test/src/test3.txt

-  To upload the **file1** file to the **bucket-test** bucket, and resume the upload if the upload fails, run the following commands:

   .. code-block::

      ./obsutil cp /file1  obs://bucket-test/file -f

   The upload fails. The command output is as follows:

   .. code-block::

      ./obsutil cp /file1 obs://bucket-test/file -f

      Parallel:      3                   Jobs:          3
      Threshold:     524288000           PartSize:      5242880
      VerifyLength:  false               VerifyMd5:     false
      CheckpointDir: xxxx

      [=================================__________________] 66.08% ?/s 3.35GB/4.88GB ?

   Run the preceding command again to resume the upload. The command output is as follows:

   .. code-block::

      obsutil cp /file1 obs://bucket-test/file -f

   .. code-block::

      Parallel:      3                   Jobs:          3
      Threshold:     524288000           PartSize:      5242880
      VerifyLength:  false               VerifyMd5:     false
      CheckpointDir: xxxx

      [====================================================] 100% 307.42MB/s 4.88GB/4.88GB 5.308s
      Upload successfully, 4.88GB, n/a, /file1 --> obs://bucket-test/file, cost [6325], status [200], request id [xxxxx]

-  To incrementally upload all files from the local **src1** folder to the **src** directory of bucket **bucket-test**, the command is as follows:

   .. code-block::

      ./obsutil cp /src1  obs://bucket-test/src -f -r -u

   Four objects are successfully uploaded, one of which is a new object. The command output contains **Skip count**.

   .. code-block::

      ./obsutil cp /src1 obs://bucket-test/src -f -r -u

   .. code-block::

      Start at 2024-10-08 02:00:18.8906532 +0000 UTC

      Parallel:      5                   Jobs:          5
      Threshold:     50.00MB             PartSize:      auto
      VerifyLength:  false               VerifyMd5:     false
      CheckpointDir: xxxx
      Task id: 6a97974a-7929-4188-9736-fcd637d16584
      OutputDir: xxxx
      [====================================================] 100% tps:0.00 ?/s 2.09KB/2.09KB 5ms
      Succeed count:   4         Failed count:    0         Skip count:      3
      Succeed bytes:   2.09KB
      Metrics [max cost:6 ms, min cost:6 ms, average cost:1.50 ms, average tps:52.63, transferred size :2.09KB]

-  Run the following command to exclude the **src2** folder (including all files and folders contained) when uploading the **src1** folder:

   .. code-block::

      ./obsutil cp /src1  obs://bucket-test/src -exclude "*src1/src2*" -f -r -mf

   Five objects are successfully uploaded, and the upload information contains **exclude** and the specific content.

   .. code-block::

      ./obsutil cp /src1  obs://bucket-test/src -exclude "*src1/src2*" -f -r -mf
      Start at 2024-10-08 02:04:27.7752009 +0000 UTC
      Parallel:      5                   Jobs:          5
      Threshold:     50.00MB             PartSize:      auto
      VerifyLength:  false               VerifyMd5:     false
      Exclude:       *src1/src2*
      Include:
      CheckpointDir: xxxx
      OutputDir: xxxx

      [====================================================] 100.00% tps:35.82 ?/s 5/5 2.39KB/2.39KB 340ms
      Succeed count:   3         Failed count:    0
      Succeed bytes:   2.39KB
      Metrics [max cost:338 ms, min cost:91 ms, average cost:240.40 ms, average tps:14.62, transferred size:2.39KB]

   After the upload completes, the following objects are generated in the bucket:

   .. code-block::

      obs://bucket-test/src/src1/
      obs://bucket-test/src/src1/src3/
      obs://bucket-test/src/src1/test3.txt

.. note::

   Resumable upload is available only for large files. Specifically, the file size is greater than 5 GB or the file size is greater than the threshold (50 MB by default).
