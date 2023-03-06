:original_name: obs_04_0099.html

.. _obs_04_0099:

Multipart Upload
================

Functions
---------

After initiating a multipart upload, you can use this operation to upload parts for the multipart upload using its task ID. When parts are uploaded in a multipart upload of an object, the upload sequence does not affect part merging, namely, multiple parts can be uploaded concurrently.

Part sizes range from 100 KB to 5 GB. However, when parts are being merged, the size of the last uploaded part ranges from 0 to 5 GB. The upload part ID ranges from 1 to 10,000.

This operation supports server-side encryption.

.. important::

   The value of **partNumber** in a multipart task is unique. If you upload a part of the same **partNumber** repeatedly, the last part uploaded will overwrite the previous one. When multiple concurrent uploading of the same **partNumber** part of the same object is performed, the Last Write Win policy is applied. The time of **Last Write** is defined as the time when the metadata of the part is created. To ensure data accuracy, the client must be locked to ensure concurrent upload of the same part of the same object. Concurrent upload of different parts of the same object does not need to be locked.

Request Syntax
--------------

.. code-block:: text

   PUT /ObjectName?partNumber=partNum&uploadId=uploadID  HTTP/1.1
   Host: bucketname.obs.region.example.com
   Date: date
   Content-Length: length
   Authorization: authorization
   Content-MD5:md5
   <object Content>

Request Parameters
------------------

This request uses parameters to specify the upload task ID and part number. :ref:`Table 1 <obs_04_0099__table6481817>` describes the parameters.

.. _obs_04_0099__table6481817:

.. table:: **Table 1** Request parameters

   +-----------------------+-------------------------------------------------------------------------------------+-----------------------+
   | Parameter             | Description                                                                         | Mandatory             |
   +=======================+=====================================================================================+=======================+
   | partNumber            | Indicates the ID of a part to be uploaded. The value is an integer from 1 to 10000. | Yes                   |
   |                       |                                                                                     |                       |
   |                       | Type: integer                                                                       |                       |
   +-----------------------+-------------------------------------------------------------------------------------+-----------------------+
   | uploadId              | Indicates a multipart upload ID.                                                    | Yes                   |
   |                       |                                                                                     |                       |
   |                       | Type: string                                                                        |                       |
   +-----------------------+-------------------------------------------------------------------------------------+-----------------------+

Request Headers
---------------

This request uses common headers. For details, see :ref:`Table 3 <obs_04_0007__table25197309>`.

.. table:: **Table 2** Server encryption request headers

   +-------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------+
   | Header                                          | Description                                                                                                                                                                                         | Mandatory                                                                                                                                  |
   +=================================================+=====================================================================================================================================================================================================+============================================================================================================================================+
   | x-obs-server-side-encryption-customer-algorithm | Indicates an encryption algorithm. The header is used in SSE-C mode.                                                                                                                                | No. This header is required when SSE-C is used. The encryption algorithm must be the same as that used to initiate multipart upload tasks. |
   |                                                 |                                                                                                                                                                                                     |                                                                                                                                            |
   |                                                 | Type: string                                                                                                                                                                                        |                                                                                                                                            |
   |                                                 |                                                                                                                                                                                                     |                                                                                                                                            |
   |                                                 | Example: **x-obs-server-side-encryption-customer-algorithm:AES256**                                                                                                                                 |                                                                                                                                            |
   |                                                 |                                                                                                                                                                                                     |                                                                                                                                            |
   |                                                 | Constraint: This header must be used together with **x-obs-server-side-encryption-customer-key** and **x-obs-server-side-encryption-customer-key-MD5**.                                             |                                                                                                                                            |
   +-------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------+
   | x-obs-server-side-encryption-customer-key       | Indicates a key used to encrypt objects. The header is used in SSE-C mode. This key is used to encrypt objects.                                                                                     | No. This header is required when SSE-C is used. The key must be the same as that used to initiate multipart upload tasks.                  |
   |                                                 |                                                                                                                                                                                                     |                                                                                                                                            |
   |                                                 | Type: string                                                                                                                                                                                        |                                                                                                                                            |
   |                                                 |                                                                                                                                                                                                     |                                                                                                                                            |
   |                                                 | Example: **x-obs-server-side-encryption-customer-key:K7QkYpBkM5+hca27fsNkUnNVaobncnLht/rCB2o/9Cw=**                                                                                                 |                                                                                                                                            |
   |                                                 |                                                                                                                                                                                                     |                                                                                                                                            |
   |                                                 | Constraint: This header is a Base64-encoded 256-bit key and must be used together with **x-obs-server-side-encryption-customer-algorithm** and **x-obs-server-side-encryption-customer-key-MD5**.   |                                                                                                                                            |
   +-------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------+
   | x-obs-server-side-encryption-customer-key-MD5   | Indicates the MD5 value of a key used to encrypt objects. The header is used in SSE-C mode. The MD5 value is used to check whether any error occurs during the transmission of the key.             | No. This header is required when SSE-C is used. The MD5 value must be the same as that used to initiate multipart upload tasks.            |
   |                                                 |                                                                                                                                                                                                     |                                                                                                                                            |
   |                                                 | Type: string                                                                                                                                                                                        |                                                                                                                                            |
   |                                                 |                                                                                                                                                                                                     |                                                                                                                                            |
   |                                                 | Example: **x-obs-server-side-encryption-customer-key-MD5:4XvB3tbNTN+tIEVa0/fGaQ==**                                                                                                                 |                                                                                                                                            |
   |                                                 |                                                                                                                                                                                                     |                                                                                                                                            |
   |                                                 | Constraint: This header is a Base64-encoded 128-bit MD5 value and must be used together with **x-obs-server-side-encryption-customer-algorithm** and **x-obs-server-side-encryption-customer-key**. |                                                                                                                                            |
   +-------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------+

Request Elements
----------------

This request involves no elements.

Response Syntax
---------------

::

   HTTP/1.1 status_code
   Date: date
   ETag: etag
   Content-Length: length

Response Headers
----------------

The response to the request uses common headers. For details, see :ref:`Table 1 <obs_04_0013__d0e686>`.

.. table:: **Table 3** Additional response headers

   +-------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Header                                          | Description                                                                                                                                                                       |
   +=================================================+===================================================================================================================================================================================+
   | x-obs-server-side-encryption                    | This header is included in a response if SSE-KMS is used.                                                                                                                         |
   |                                                 |                                                                                                                                                                                   |
   |                                                 | Type: string                                                                                                                                                                      |
   |                                                 |                                                                                                                                                                                   |
   |                                                 | Example: **x-obs-server-side-encryption:kms**                                                                                                                                     |
   +-------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | x-obs-server-side-encryption-kms-key-id         | Indicates the master key ID. This header is included in a response if SSE-KMS is used.                                                                                            |
   |                                                 |                                                                                                                                                                                   |
   |                                                 | Type: string                                                                                                                                                                      |
   |                                                 |                                                                                                                                                                                   |
   |                                                 | Format: *regionID*\ **:**\ *domainID*\ **:key/**\ *key_id*                                                                                                                        |
   |                                                 |                                                                                                                                                                                   |
   |                                                 | *regionID* is the ID of the region to which the key belongs. *domainID* is the account ID of the tenant to which the key belongs. *key_id* is the key ID used in this encryption. |
   |                                                 |                                                                                                                                                                                   |
   |                                                 | Example: **x-obs-server-side-encryption-kms-key-id:region:domainiddomainiddomainiddoma0001:key/4f1cd4de-ab64-4807-920a-47fc42e7f0d0**                                             |
   +-------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | x-obs-server-side-encryption-customer-algorithm | Indicates an encryption algorithm. This header is included in a response if SSE-C is used.                                                                                        |
   |                                                 |                                                                                                                                                                                   |
   |                                                 | Type: string                                                                                                                                                                      |
   |                                                 |                                                                                                                                                                                   |
   |                                                 | Example: **x-obs-server-side-encryption-customer-algorithm:AES256**                                                                                                               |
   +-------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | x-obs-server-side-encryption-customer-key-MD5   | Indicates the MD5 value of a key used to encrypt objects. This header is included in a response if SSE-C is used.                                                                 |
   |                                                 |                                                                                                                                                                                   |
   |                                                 | Type: string                                                                                                                                                                      |
   |                                                 |                                                                                                                                                                                   |
   |                                                 | Example: **x-obs-server-side-encryption-customer-key-MD5:4XvB3tbNTN+tIEVa0/fGaQ==**                                                                                               |
   +-------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Response Elements
-----------------

This response involves no elements.

Error Responses
---------------

#. If a part number is not within the range from 1 to 10000, OBS returns **400 Bad Request**.
#. If a part size has exceeded 5 GB, the error code **400 Bad Request** is returned.
#. If the AK or signature is invalid, OBS returns **403 Forbidden** and the error code is **AccessDenied**.
#. Check whether the bucket exists. If the bucket is not found, OBS returns **404 Not Found** and the error code is **NoSuchBucket**.
#. View the bucket ACL to check whether the user has the read permission for the requested bucket. If the user does not have the read permission, OBS returns **403 AccessDenied**.
#. Check whether the multipart upload task exists. If the task does not exist, OBS returns **404 Not Found** and the error code is **NoSuchUpload**.
#. Check whether the request user is the initiator of the multipart upload task. If not, OBS returns **403 Forbidden** and the error code is **AccessDenied**.

Other errors are included in :ref:`Table 2 <obs_04_0115__d0e843>`.

Sample Request
--------------

.. code-block:: text

   PUT /object02?partNumber=1&uploadId=00000163D40171ED8DF4050919BD02B8 HTTP/1.1
   User-Agent: curl/7.29.0
   Host: examplebucket.obs.region.example.com
   Accept: */*
   Date: WED, 01 Jul 2015 05:15:55 GMT
   Authorization: OBS H4IPJX0TQTHTHEBQQCEC:ZB0hFwaHubi1aKHv7dSZjJts40g=
   Content-Length: 102015348

   [102015348 Byte part content]

Sample Response
---------------

::

   HTTP/1.1 200 OK
   Server: OBS
   x-obs-request-id: 8DF400000163D40956A703289CA066F1
   ETag: "b026324c6904b2a9cb4b88d6d61c81d1"
   x-obs-id-2: 32AAAQAAEAABAAAQAAEAABAAAQAAEAABCUQu/EOEVSMa04GXVwy0z9WI+BsDKvfh
   Date: WED, 01 Jul 2015 05:15:55 GMT
   Content-Length: 0
