:original_name: obs_04_0064.html

.. _obs_04_0064:

Deleting the Encryption Configuration of a Bucket
=================================================

Functions
---------

OBS uses the DELETE method to delete the encryption configuration of a specified bucket.

To perform this operation, you must have the **PutEncryptionConfiguration** permission. By default, only the bucket owner can delete the tags of a bucket. The bucket owner can allow other users to perform this operation by setting a bucket policy or granting them the permission.

Request Syntax
--------------

.. code-block:: text

   DELETE /?encryption HTTP/1.1
   User-Agent: curl/7.29.0
   Host: bucketname.obs.region.example.com
   Accept: */*
   Date: date
   Authorization: authorization string

Request parameters
------------------

This request contains no parameter.

Request Headers
---------------

This request uses common headers. For details, see :ref:`Table 3 <obs_04_0007__table25197309>`.

Request Elements
----------------

This request involves no elements.

Response Syntax
---------------

::

   HTTP/1.1 status_code
   Server: OBS
   x-obs-request-id: request id
   x-obs-id-2: id
   Date: date

Response Headers
----------------

The response to the request uses common headers. For details, see :ref:`Table 1 <obs_04_0013__d0e686>`.

Response Elements
-----------------

This response involves no elements.

Error Responses
---------------

No special error responses are returned. For details about error responses, see :ref:`Table 2 <obs_04_0115__d0e843>`.

Sample Request
--------------

.. code-block:: text

   DELETE /examplebucket?encryption HTTP/1.1
   User-Agent: curl/7.29.0
   Host: examplebucket.obs.region.example.com
   Accept: */*
   Date: Tue, 08 Jan 2019 13:18:35 +0000
   Authorization: OBS UDSIAMSTUBTEST000001:UT9F2YUgaFu9uFGMmxFj2CBgQHs=

Sample Response
---------------

::

   HTTP/1.1 204 No Content
   Server: OBS
   x-obs-request-id: 000001682D993B666808E265A3F6361D
   x-obs-id-2: 32AAAQAAEAABAAAQAAEAABAAAQAAEAABCSyB46jGSQsu06m1nyIeKxTuJ+H27ooC
   Date: Tue, 08 Jan 2019 13:14:03 GMT
