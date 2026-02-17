:original_name: obs_11_0015.html

.. _obs_11_0015:

Querying Object Properties
==========================

Function
--------

You can use this command to query the basic properties of an object.

Command Line Structure
----------------------

-  In Windows

   .. code-block::

      obsutil stat obs://bucket/key [-acl][-bf=xxx] [-config=xxx]

-  In Linux or macOS

   .. code-block::

      ./obsutil stat obs://bucket/key [-acl][-bf=xxx] [-config=xxx]

Examples
--------

-  Take the Windows OS as an example. Run the **obsutil stat obs://bucket-test/key** command to query the basic properties of an object.

   .. code-block::

      obsutil stat obs://bucket-test/key

      Start at 2024-09-25 04:48:10.1147483 +0000 UTC

      Key:
        obs://bucket-test/key
      LastModified:
        2018-11-16T02:15:49Z
      Size:
        7
      StorageClass:
        standard
      ETag:
        43d93b553855b0e1fc67e31c28c07b65
      ContentType:
        text/plain
      Type:
        file
      Metadata:
        key=value

Parameter Description
---------------------

+-----------------------+---------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| Parameter             | Optional or Mandatory           | Description                                                                                                                                                                                                                                                  |
+=======================+=================================+==============================================================================================================================================================================================================================================================+
| bucket                | Mandatory                       | The name of the bucket to which an object belongs                                                                                                                                                                                                            |
+-----------------------+---------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| key                   | Mandatory                       | The name of the object whose attributes are to be queried                                                                                                                                                                                                    |
+-----------------------+---------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| acl                   | Optional                        | Queries the access control policies of the object at the same time.                                                                                                                                                                                          |
+-----------------------+---------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| bf                    | Optional (additional parameter) | The display format of the object size (in bytes). Possible values are:                                                                                                                                                                                       |
|                       |                                 |                                                                                                                                                                                                                                                              |
|                       |                                 | -  **human-readable**: The object size is displayed in a human-readable format. For example, the object size is displayed in KB, MB, GB, or TB (for instance, 1 GB), rather than in bytes (for instance, 1,073,741,824 bytes, which is a very large number). |
|                       |                                 | -  **raw**: The number of bytes is displayed without any conversion or formatting. For example, if the space occupied by an object is 1 GB, the object size is displayed as 1,073,741,824 bytes.                                                             |
|                       |                                 |                                                                                                                                                                                                                                                              |
|                       |                                 | For common users, the **human-readable** format is easier to understand. For scenarios where accurate calculation or automatic processing is required, the **raw** format is more suitable.                                                                  |
|                       |                                 |                                                                                                                                                                                                                                                              |
|                       |                                 | If this parameter is not configured, the display format of the object size (in bytes) is determined by the **humanReadableFormat** parameter in the configuration file.                                                                                      |
+-----------------------+---------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| bucket-cname          | Optional (additional parameter) | The user-defined domain name bound to the bucket                                                                                                                                                                                                             |
|                       |                                 |                                                                                                                                                                                                                                                              |
|                       |                                 | .. note::                                                                                                                                                                                                                                                    |
|                       |                                 |                                                                                                                                                                                                                                                              |
|                       |                                 |    This parameter is only supported by obsutil 5.7.9 and later.                                                                                                                                                                                              |
+-----------------------+---------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| config                | Optional (additional parameter) | The user-defined configuration file for executing the current command. For details about parameters that can be configured, see :ref:`Configuration Parameters <obs_11_0035>`.                                                                               |
+-----------------------+---------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| payer                 | Optional (additional parameter) | Specifies that requester pays is enabled.                                                                                                                                                                                                                    |
+-----------------------+---------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Response
--------

+-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| Field                             | Description                                                                                                                                                                                                                               |
+===================================+===========================================================================================================================================================================================================================================+
| Key                               | The object name                                                                                                                                                                                                                           |
+-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| LastModified                      | The latest modification time of the object                                                                                                                                                                                                |
+-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| Size                              | The object size                                                                                                                                                                                                                           |
|                                   |                                                                                                                                                                                                                                           |
|                                   | Unit: byte                                                                                                                                                                                                                                |
+-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| StorageClass                      | The storage class of the object                                                                                                                                                                                                           |
|                                   |                                                                                                                                                                                                                                           |
|                                   | Possible values are:                                                                                                                                                                                                                      |
|                                   |                                                                                                                                                                                                                                           |
|                                   | -  **standard**: Standard storage class. It features low access latency and high throughput, and is applicable to storing frequently accessed data (multiple accesses per month) or data that is smaller than 1 MB.                       |
|                                   | -  **warm**: Warm storage class. It is ideal for storing infrequently accessed (less than 12 times a year) data, but when needed, the access has to be fast.                                                                              |
|                                   | -  **cold**: Cold storage class. It provides secure, durable, and inexpensive storage for rarely-accessed (once a year) data. **For an object whose storage class is cold, restore the object first and then specify its storage class.** |
+-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| MD5                               | Real MD5 of the object. This parameter is used to ensure and verify data integrity.                                                                                                                                                       |
|                                   |                                                                                                                                                                                                                                           |
|                                   | You can query this value only after running the **cp** command and configuring the **-vmd5** parameter.                                                                                                                                   |
+-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| ETag                              | The ETag value of an object calculated on the server                                                                                                                                                                                      |
+-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| ContentType                       | The file type of an object. It determines the format and encoding method a browser will use to read the file.                                                                                                                             |
+-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| Type                              | The file type                                                                                                                                                                                                                             |
+-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| Metadata                          | The user-defined metadata of the object. This field can be queried only when the object has user-defined metadata.                                                                                                                        |
+-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
