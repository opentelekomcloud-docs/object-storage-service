:original_name: obs_11_0009.html

.. _obs_11_0009:

Listing Buckets
===============

Function
--------

You can use this command to obtain the bucket list. In the list, bucket names are displayed in lexicographical order.

Command Line Structure
----------------------

-  In Windows

   .. code-block::

      obsutil ls [-s]  [-sc] [-du] [-fs] [-j=1] [-limit=1]  [-config=xxx]

-  In Linux or macOS

   .. code-block::

      ./obsutil ls [-s]  [-sc] [-du] [-fs] [-j=1] [-limit=1]  [-config=xxx]

Examples
--------

-  Take the Windows OS as an example. Run the **obsutil ls -limit=5** command to obtain the bucket list.

   .. code-block::

      obsutil ls -limit=5
      Start at 2024-09-29 07:58:46.0506904 +0000 UTC

      Bucket                        CreationDate                  Location         BucketType
      obs://bucket001               2018-09-03T01:53:02Z          example          OBJECT

      obs://bucket002               2018-11-01T01:40:01Z          example          OBJECT

      obs://bucket003               2018-10-25T11:45:45Z          example          OBJECT

      obs://bucket004               2018-10-26T02:33:09Z          example          OBJECT

      obs://bucket005               2018-10-26T02:34:50Z          example          OBJECT

      Bucket number : 5

Parameter Description
---------------------

+-----------------------+------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| Parameter             | Optional or Mandatory                                                  | Description                                                                                                                                                                      |
+=======================+========================================================================+==================================================================================================================================================================================+
| s                     | Optional (additional parameter)                                        | Displays simplified query result.                                                                                                                                                |
|                       |                                                                        |                                                                                                                                                                                  |
|                       |                                                                        | .. note::                                                                                                                                                                        |
|                       |                                                                        |                                                                                                                                                                                  |
|                       |                                                                        |    In the simplified format, the returned result contains only the bucket name.                                                                                                  |
+-----------------------+------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| sc                    | Optional (additional parameter)                                        | Queries the storage classes of the buckets when listing buckets.                                                                                                                 |
+-----------------------+------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| j                     | Optional (additional parameter). It must be used together with **sc**. | The maximum number of concurrent tasks for querying the bucket storage class. The default value is the value of **defaultJobs** in the configuration file.                       |
|                       |                                                                        |                                                                                                                                                                                  |
|                       |                                                                        | .. note::                                                                                                                                                                        |
|                       |                                                                        |                                                                                                                                                                                  |
|                       |                                                                        |    The value is ensured to be greater than or equal to 1.                                                                                                                        |
+-----------------------+------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| du                    | Optional (additional parameter)                                        | Quickly returns the total size of listed objects, without displaying detailed object information. This parameter can be used together with other parameters.                     |
|                       |                                                                        |                                                                                                                                                                                  |
|                       |                                                                        | .. note::                                                                                                                                                                        |
|                       |                                                                        |                                                                                                                                                                                  |
|                       |                                                                        |    This parameter takes effect only on listing objects, but not on listing buckets.                                                                                              |
+-----------------------+------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| limit                 | Optional (additional parameter)                                        | The maximum number of buckets that can be queried. If the value is less than 0, all buckets are listed. If it is left blank, a maximum of 1000 buckets can be listed by default. |
+-----------------------+------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| config                | Optional (additional parameter)                                        | The user-defined configuration file for executing the current command. For details about parameters that can be configured, see :ref:`Configuration Parameters <obs_11_0035>`.   |
+-----------------------+------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

.. note::

   In a bucket listing result, **BucketType** indicates the bucket type. **OBJECT** indicates an object storage bucket, while **POSIX** indicates a parallel file system.
