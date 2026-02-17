:original_name: obs_11_0010.html

.. _obs_11_0010:

Querying Bucket Properties
==========================

Function
--------

You can use this command to query the basic properties of a bucket, including its default storage class, region, version ID, storage usage, bucket quota, whether it supports POSIX, and the number of objects in the bucket.

Command Line Structure
----------------------

-  In Windows

   .. code-block::

      obsutil stat obs://bucket [-acl] [-bf=xxx] [-config=xxx]  [-payer=xxx]

-  In Linux or macOS

   .. code-block::

      ./obsutil stat obs://bucket [-acl] [-bf=xxx] [-config=xxx]
       [-payer=xxx]

Examples
--------

-  Take the Windows OS as an example. Run the **obsutil stat obs://bucket-test** command to query the basic properties of bucket **bucket-test**.

   .. code-block::

      obsutil stat obs://bucket-test

      Start at 2024-09-29 07:58:46.0506904 +0000 UTC

      Bucket:
        obs://bucket-test
      StorageClass:
        standard

      ObsVersion:
        3.0
      BucketType:
        OBJECTObjectNumber:
        8005
      Size:
        320076506
      Quota:
        0

Parameter Description
---------------------

+-----------------------+---------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| Parameter             | Optional or Mandatory           | Description                                                                                                                                                                         |
+=======================+=================================+=====================================================================================================================================================================================+
| bucket                | Mandatory                       | The bucket name                                                                                                                                                                     |
+-----------------------+---------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| acl                   | Optional                        | Queries the access control policies of the bucket while querying bucket properties.                                                                                                 |
+-----------------------+---------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| bf                    | Optional (additional parameter) | The display format of the used bucket capacity (in bytes). Possible values are:                                                                                                     |
|                       |                                 |                                                                                                                                                                                     |
|                       |                                 | -  human-readable                                                                                                                                                                   |
|                       |                                 | -  raw                                                                                                                                                                              |
|                       |                                 |                                                                                                                                                                                     |
|                       |                                 | .. note::                                                                                                                                                                           |
|                       |                                 |                                                                                                                                                                                     |
|                       |                                 |    If this parameter is not configured, the display format of the used bucket capacity (in bytes) is determined by the **humanReadableFormat** parameter in the configuration file. |
+-----------------------+---------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| bucket-cname          | Optional (additional parameter) | The user-defined domain name bound to the bucket                                                                                                                                    |
|                       |                                 |                                                                                                                                                                                     |
|                       |                                 | .. note::                                                                                                                                                                           |
|                       |                                 |                                                                                                                                                                                     |
|                       |                                 |    This parameter is only supported by obsutil 5.7.9 and later.                                                                                                                     |
+-----------------------+---------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| config                | Optional (additional parameter) | The user-defined configuration file for executing the current command. For details about parameters that can be configured, see :ref:`Configuration Parameters <obs_11_0035>`.      |
+-----------------------+---------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| payer                 | Optional (additional parameter) | Specifies that requester pays is enabled.                                                                                                                                           |
+-----------------------+---------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Response
--------

+--------------+----------------------------------------------------------------------------------------------------------------------------------------+
| Field        | Description                                                                                                                            |
+==============+========================================================================================================================================+
| Bucket       | The bucket name                                                                                                                        |
+--------------+----------------------------------------------------------------------------------------------------------------------------------------+
| StorageClass | The default storage class of the bucket                                                                                                |
+--------------+----------------------------------------------------------------------------------------------------------------------------------------+
| Location     | The region where the bucket resides                                                                                                    |
+--------------+----------------------------------------------------------------------------------------------------------------------------------------+
| ObsVersion   | The version of the bucket                                                                                                              |
+--------------+----------------------------------------------------------------------------------------------------------------------------------------+
| BucketType   | The type of the bucket. **OBJECT** indicates a bucket for object storage. **POSIX** indicates a bucket used as a parallel file system. |
+--------------+----------------------------------------------------------------------------------------------------------------------------------------+
| ObjectNumber | The number of objects in the bucket                                                                                                    |
+--------------+----------------------------------------------------------------------------------------------------------------------------------------+
| Size         | The storage usage of the bucket, in bytes                                                                                              |
+--------------+----------------------------------------------------------------------------------------------------------------------------------------+
| Quota        | The bucket quota. Value **0** indicates that no upper limit is set for the bucket quota.                                               |
+--------------+----------------------------------------------------------------------------------------------------------------------------------------+
| Acl          | The access control policy of the bucket                                                                                                |
+--------------+----------------------------------------------------------------------------------------------------------------------------------------+
