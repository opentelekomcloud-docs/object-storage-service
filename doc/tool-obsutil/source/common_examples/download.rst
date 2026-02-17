:original_name: obs_11_0029.html

.. _obs_11_0029:

Download
========

All commands in this section use the Linux operating system as an example to describe how to download files.

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
   obs://bucket-test/src2/src3/
   obs://bucket-test/src2/src3/test9.txt

Based on the structure of objects in the bucket, different download scenarios require different commands.

-  To download the **test1.txt** file from bucket **bucket-test** to the local **src1** folder, the command is as follows:

   .. code-block::

      ./obsutil cp obs://bucket-test/test1.txt  /src1

   After the download is complete, the following file is generated on the local PC:

   .. code-block::

      └── src1
          └── test1.txt

-  Run the following command to download the **test1.txt** file to your local PC. If there is no **test.txt** on the local PC, the **test1.txt** file is directly downloaded and you can rename it to **test.txt**. If **test.txt** already exists, **test1.txt** is downloaded and overwrites the original local **test.txt** file after renaming.

   .. code-block::

      ./obsutil cp obs://bucket-test/test1.txt  /test.txt

   After the download is complete, the following file is generated on the local PC:

   .. code-block::

      └── test.txt

-  To recursively download the entire **src2** folder from bucket **bucket-test** to the local **src1** folder in force mode, the command is as follows:

   .. code-block::

      ./obsutil cp obs://bucket-test/src2  /src1 -r -f

   After the download is complete, the following files are generated on the local PC:

   .. code-block::

      └── src1
          └── src2
              ├── src3
                  └── test9.txt
              └── test8.txt

-  To recursively download all files and subfolders in the **src2** folder from bucket **bucket-test** to the local **src1** folder in force mode, the command is as follows:

   .. code-block::

      ./obsutil cp obs://bucket-test/src2  /src1 -r -f -flat

   After the download is complete, the following files are generated on the local PC:

   .. code-block::

      └── src1
          ├── src3
              └── test9.txt
          └── test8.txt

-  To recursively download the all objects in bucket **bucket-test** to the local **src0** folder in force mode, the command is as follows:

   .. code-block::

      ./obsutil cp obs://bucket-test  /src0 -r -f

   After the download is complete, the following files are generated on the local PC:

   .. code-block::

      └── src0
          ├── test1.txt
          ├── test2.txt
          ├── test3.txt
          ├── test4.txt
          ├── test5.txt
          ├── test6.txt
          ├── src1
              └── test7.txt
          └── src2
              ├── src3
                  └── test9.txt
              └── test8.txt

-  Run the following command to exclude the **src2** folder (including all files and folders contained) when downloading the **src1** folder from the **bucket-test** bucket:

   .. code-block::

      ./obsutil cp obs://bucket-test/src1/ src1 -exclude "*src1/src2*" -r -f -mf

   Four objects are successfully downloaded, and the download information contains **exclude** and the specific content.

   .. code-block::

      ./obsutil cp obs://bucket-test/src1/ src1 -exclude "*src1/src2*" -r -f -mf

      Parallel:      5                   Jobs:          5
      Threshold:     50.00MB             PartSize:      auto
      VerifyLength:  false               VerifyMd5:     false
      Exclude:       *src1/src2*
      Include:
      CheckpointDir: xxxx
      OutputDir: xxxx
      TempFileDir: xxxx

      [====================================================] 100.00% tps:87.78 ?/s 4/4 2.39KB/2.39KB 223ms
      Succeed count:   4         Failed count:    0
      Succeed bytes:   2.39KB
      Metrics [max cost:147 ms, min cost:77 ms, average cost:56.00 ms, average tps:8.85, transferred size:2.39KB]

   After the download is complete, the following files are generated on the local PC:

   .. code-block::

      └── src1
          ├── src3
              └── test9.txt
          └── test7.txt
