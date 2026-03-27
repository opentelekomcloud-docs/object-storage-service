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

-  To download the **test1.txt** file from the **bucket-test** bucket to the local **src1** folder, use the following command:

   .. code-block::

      ./obsutil cp obs://bucket-test/test1.txt  /src1

   After the download is complete, the following file is generated on the local PC:

   .. code-block::

      └── src1
          └── test1.txt

-  To download the **test1.txt** file from the **bucket-test** bucket to your local PC, use the following command. If **test.txt** does not exist locally, the **test1.txt** file will be downloaded and saved as **test.txt**. If **test.txt** already exists, the download will overwrite it with the contents of **test1.txt**.

   .. code-block::

      ./obsutil cp obs://bucket-test/test1.txt  /test.txt

   After the download is complete, the following file is generated on the local PC:

   .. code-block::

      └── test.txt

-  To recursively download the entire **src2** folder from the **bucket-test** bucket to the local **src1** folder in force mode, use the following command:

   .. code-block::

      ./obsutil cp obs://bucket-test/src2  /src1 -r -f

   After the download is complete, the following files are generated on the local PC:

   .. code-block::

      └── src1
          └── src2
              ├── src3
                  └── test9.txt
              └── test8.txt

-  To recursively download all files and subfolders from the **src2** folder of the **bucket-test** bucket to the local **src1** folder in force mode, use the following command:

   .. code-block::

      ./obsutil cp obs://bucket-test/src2  /src1 -r -f -flat

   After the download is complete, the following files are generated on the local PC:

   .. code-block::

      └── src1
          ├── src3
              └── test9.txt
          └── test8.txt

-  To recursively download all objects from the **bucket-test** bucket to the local **src0** folder in force mode, use the following command:

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

-  To exclude the **src2** folder (including all of its contents) when downloading the **src1** folder from the **bucket-test** bucket, use the following command:

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
