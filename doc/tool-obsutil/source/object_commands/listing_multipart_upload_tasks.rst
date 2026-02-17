:original_name: obs_11_0019.html

.. _obs_11_0019:

Listing Multipart Upload Tasks
==============================

Function
--------

You can use this command to query multipart upload tasks in a bucket.

Command Line Structure
----------------------

-  In Windows

   .. code-block::

      obsutil ls obs://bucket[/prefix] [-s] [-d] -m [-a] [-uploadIdMarker=xxx] [-marker=xxx] [-limit=1]  [-config=xxx]

-  In Linux or macOS

   .. code-block::

      ./obsutil ls obs://bucket[/prefix] [-s] [-d] -m [-a] [-uploadIdMarker=xxx] [-marker=xxx] [-limit=1]  [-config=xxx]

Examples
--------

-  Take the Windows OS as an example. Run the **obsutil ls obs://bucket-test -m -limit=10** command to query the multipart upload tasks in the bucket.

   .. code-block::

      obsutil ls obs://bucket-test -m -limit=10

      Listing multipart uploads.

      Upload list:
      Key                                               Initiated
      StorageClass        UploadId
      obs://bucket-test/aaa                                  2018-11-27T03:49:07Z
      standard            000001675348ED21860C3F61EF955BD3

      obs://bucket-test/dir1/10GB.txt                        2018-11-07T06:58:09Z
      standard            00000166ECF6CF7C860D1DBAF3F76013

      obs://bucket-test/dir1/1GB.txt                         2018-11-07T06:58:09Z
      standard            00000166ECF6CF6F860B7FBE95D01B03

      obs://bucket-test/dir1/50GB.txt                        2018-11-07T06:58:09Z
      standard            00000166ECF6CF86860D1DC2C8E8F66B

      obs://bucket-test/dir1/5GB.txt                         2018-11-07T06:58:09Z
      standard            00000166ECF6CF75860CDA7780CB52C3

      obs://bucket-test/test11/20GB.txt                      2018-11-27T08:21:26Z
      standard            0000016754423D24860CA8A4D06C2054

      Folder number: 0
      Upload number: 6

-  For more examples, see :ref:`Common Examples <obs_11_0027>`.

Parameter Description
---------------------

+-----------------------+----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| Parameter             | Optional or Mandatory            | Description                                                                                                                                                                                                                                                                                                                            |
+=======================+==================================+========================================================================================================================================================================================================================================================================================================================================+
| bucket                | Mandatory                        | The bucket name                                                                                                                                                                                                                                                                                                                        |
+-----------------------+----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| prefix                | Optional                         | The object name prefix for listing multipart uploads                                                                                                                                                                                                                                                                                   |
|                       |                                  |                                                                                                                                                                                                                                                                                                                                        |
|                       |                                  | .. note::                                                                                                                                                                                                                                                                                                                              |
|                       |                                  |                                                                                                                                                                                                                                                                                                                                        |
|                       |                                  |    If this parameter is left blank, all multipart upload tasks in the bucket are listed.                                                                                                                                                                                                                                               |
+-----------------------+----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| s                     | Optional (additional parameter)  | Displays simplified query result.                                                                                                                                                                                                                                                                                                      |
|                       |                                  |                                                                                                                                                                                                                                                                                                                                        |
|                       |                                  | .. note::                                                                                                                                                                                                                                                                                                                              |
|                       |                                  |                                                                                                                                                                                                                                                                                                                                        |
|                       |                                  |    In the simplified format, the returned result contains only the object name and upload ID of the multipart upload.                                                                                                                                                                                                                  |
+-----------------------+----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| d                     | Optional (additional parameter)  | Lists only the multipart upload tasks and sub-directories in the current directory are listed, instead of recursively listing all the multipart upload tasks and sub-directories.                                                                                                                                                      |
+-----------------------+----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| m                     | Mandatory (additional parameter) | Lists multipart upload tasks in the bucket.                                                                                                                                                                                                                                                                                            |
+-----------------------+----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| a                     | Optional (additional parameter)  | Lists the objects and the multipart upload tasks in the bucket.                                                                                                                                                                                                                                                                        |
+-----------------------+----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| marker                | Optional (additional parameter)  | The start position for listing multipart upload tasks in a bucket. The multipart upload tasks following this start position are sorted in lexicographical order by object name.                                                                                                                                                        |
|                       |                                  |                                                                                                                                                                                                                                                                                                                                        |
|                       |                                  | .. note::                                                                                                                                                                                                                                                                                                                              |
|                       |                                  |                                                                                                                                                                                                                                                                                                                                        |
|                       |                                  |    For details about how to use this parameter, see :ref:`Listing Multipart Upload Tasks <obs_11_0032>`.                                                                                                                                                                                                                               |
+-----------------------+----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| uploadIdMarker        | Optional (additional parameter)  | The start position for listing multipart upload tasks in a bucket. This parameter must be used together with **marker**. The multipart upload tasks following this start position are sorted in lexicographical order by object name and upload ID.                                                                                    |
+-----------------------+----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| limit                 | Optional (additional parameter)  | The maximum number of objects that can be listed. If the value is less than or equal to **0**, all objects are listed.                                                                                                                                                                                                                 |
|                       |                                  |                                                                                                                                                                                                                                                                                                                                        |
|                       |                                  | .. note::                                                                                                                                                                                                                                                                                                                              |
|                       |                                  |                                                                                                                                                                                                                                                                                                                                        |
|                       |                                  |    If there are a large number of multipart upload tasks in a bucket, you are advised to set this parameter to limit the number of multipart upload tasks each time. If not all tasks are listed, **marker** and **uploadIdMarker** of the next request will be returned in the result, which you can use to list the remaining tasks. |
+-----------------------+----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| config                | Optional (additional parameter)  | The user-defined configuration file for executing the current command. For details about parameters that can be configured, see :ref:`Configuration Parameters <obs_11_0035>`.                                                                                                                                                         |
+-----------------------+----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| payer                 | Optional (additional parameter)  | Specifies that requester pays is enabled.                                                                                                                                                                                                                                                                                              |
+-----------------------+----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
