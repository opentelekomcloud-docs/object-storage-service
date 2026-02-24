:original_name: obs_11_0008.html

.. _obs_11_0008:

Creating a Bucket
=================

Function
--------

You can use this command to create a bucket. A bucket name must be unique in OBS. One account can create a maximum of 100 buckets.

.. note::

   If you create a bucket and name it the same as an existing one in the same account and region, no error will be reported and status code 200 is returned. The bucket properties comply with those set in the first creation request. In other cases, creating a bucket with the same name as an existing one will receive the status code 409, indicating that the bucket already exists.

Command Line Structures
-----------------------

-  Windows

   .. code-block::

      obsutil mb obs://bucket [-fs] [-acl=xxx] [-sc=xxx] [-location=xxx] [-config=xxx]

-  macOS or Linux

   .. code-block::

      ./obsutil mb obs://bucket [-fs] [-acl=xxx] [-sc=xxx] [-location=xxx] [-config=xxx]

Examples
--------

-  In Windows, run **obsutil mb obs://bucket-test** to create a bucket. The creation succeeds.

   .. code-block::

      obsutil mb obs://bucket-test
      Start at 2024-09-29 07:52:11.3769487 +0000 UTC

      Create bucket [bucket-test] successfully, request id [000001923CC401864018BA75753D2D5F]

-  In Windows, run **obsutil mb obs://bucket001** to create a bucket with the same name as a bucket owned by another account. The creation fails.

   .. code-block::

      obsutil mb obs://bucket001
      Start at 2024-09-30 07:03:50.1378331 +0000 UTC

      Create bucket [bucket001] failed, status [409], error code [BucketAlreadyExists], error message [The requested bucket name is not available. The bucket namespace is shared by all users of the system. Please select a different name and try again.], request id [0000019241BE18DB4019EDD66E135C56]

Parameter Description
---------------------

+-----------------------+-------------------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| Parameter             | Optional or Mandatory                                                               | Description                                                                                                                                                                                                         |
+=======================+=====================================================================================+=====================================================================================================================================================================================================================+
| bucket                | Mandatory                                                                           | The bucket name                                                                                                                                                                                                     |
|                       |                                                                                     |                                                                                                                                                                                                                     |
|                       |                                                                                     | A bucket name:                                                                                                                                                                                                      |
|                       |                                                                                     |                                                                                                                                                                                                                     |
|                       |                                                                                     | -  Must be 3 to 63 characters long and start with a digit or letter. Only lowercase letters, digits, hyphens (-), and periods (.) are allowed.                                                                      |
|                       |                                                                                     | -  Cannot be formatted as an IP address.                                                                                                                                                                            |
|                       |                                                                                     | -  Cannot start or end with a hyphen (-) or period (.).                                                                                                                                                             |
|                       |                                                                                     | -  Cannot contain two consecutive periods (.), for example, **my..bucket**.                                                                                                                                         |
|                       |                                                                                     | -  Cannot contain a period (.) and a hyphen (-) adjacent to each other, for example, **my-.bucket** or **my.-bucket**.                                                                                              |
+-----------------------+-------------------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| fs                    | Optional (additional parameter)                                                     | Creates a parallel file system.                                                                                                                                                                                     |
+-----------------------+-------------------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| acl                   | Optional (additional parameter)                                                     | The access control policy that can be specified when creating a bucket                                                                                                                                              |
|                       |                                                                                     |                                                                                                                                                                                                                     |
|                       |                                                                                     | The value can be:                                                                                                                                                                                                   |
|                       |                                                                                     |                                                                                                                                                                                                                     |
|                       |                                                                                     | -  **private**: Only users granted permissions by the bucket ACL can access the bucket.                                                                                                                             |
|                       |                                                                                     | -  **public-read**: Anyone can read objects in the bucket.                                                                                                                                                          |
|                       |                                                                                     | -  **public-read-write**: Anyone can read, write, or delete objects in the bucket.                                                                                                                                  |
+-----------------------+-------------------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| sc                    | Optional (additional parameter)                                                     | The storage class of the bucket                                                                                                                                                                                     |
|                       |                                                                                     |                                                                                                                                                                                                                     |
|                       |                                                                                     | Different storage classes meet customers' needs for storage performance and costs.                                                                                                                                  |
|                       |                                                                                     |                                                                                                                                                                                                                     |
|                       |                                                                                     | The value can be:                                                                                                                                                                                                   |
|                       |                                                                                     |                                                                                                                                                                                                                     |
|                       |                                                                                     | -  **standard**: Standard storage class. It features low access latency and high throughput, and is applicable to storing frequently accessed data (multiple accesses per month) or data that is smaller than 1 MB. |
|                       |                                                                                     | -  **warm**: Warm storage class. It is ideal for storing infrequently accessed (less than 12 times a year) data, but when needed, the access has to be fast.                                                        |
|                       |                                                                                     | -  **cold**: Cold storage class. It provides secure, durable, and inexpensive storage for rarely-accessed (once a year) data.                                                                                       |
+-----------------------+-------------------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| location              | Mandatory unless the requested OBS region is the default one (additional parameter) | The region where the bucket resides                                                                                                                                                                                 |
|                       |                                                                                     |                                                                                                                                                                                                                     |
|                       |                                                                                     | -  **Once the bucket is created, its region cannot be changed.**                                                                                                                                                    |
|                       |                                                                                     | -  For lower latency and faster access, select the region nearest to where the data will be accessed.                                                                                                               |
+-----------------------+-------------------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| config                | Optional (additional parameter)                                                     | The user-defined configuration file for executing the current command. For details about parameters that can be configured, see :ref:`Configuration Parameters <obs_11_0035>`.                                      |
+-----------------------+-------------------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
