:original_name: obs_04_0100.html

.. _obs_04_0100:

Uploading a Part of an Object - Copy
====================================

Functions
---------

After creating a multipart upload job, you can specify its upload ID and upload a part to the job in OBS. Alternatively, you can make an API call to add a part (part of an object or the whole object).

This operation supports server-side encryption.

.. important::

   You cannot determine whether a request is executed successfully only using **status_code** in the returned HTTP header. If 200 in **status_code** is returned, the server has received the request and starts to process the request. The body in the response shows whether the request is executed successfully. The request is executed successfully only when the body contains Etag; otherwise, the request fails to be executed.

Copy the source object and save it as **part1**. If a **part1** already exists before the copying, the original **part1** will be overwritten by the newly copied **part1**. After the copy is successful, only the latest **part1** is displayed. The old **part1** data will be deleted. Therefore, ensure that the target part does not exist or has no value when using the part copy operation. Otherwise, data may be deleted by mistake. The source object in the copy process does not change.

OBS Cold Objects
----------------

If source objects are Cold objects, check the restoration status of the objects. You can copy these objects only after they are restored. If the source object is not restored or is being restored, the copy fails and error **403 Forbidden** is returned. The fault is described as follows:

ErrorCode: InvalidObjectState

ErrorMessage: Operation is not valid for the source object's storage class

Request Syntax
--------------

.. code-block:: text

   PUT /ObjectName?partNumber=partNum&uploadId=UploadID HTTP/1.1
   Host: bucketname.obs.region.example.com
   Date: date
   x-obs-copy-source: sourceobject
   x-obs-copy-source-range:bytes=start-end
   Authorization: authorization
   Content-Length: length

Request Parameters
------------------

To copy a part, you need to specify the part number of the target part and the multipart upload task number. :ref:`Table 1 <obs_04_0100__table12334196>` describes the parameters.

.. _obs_04_0100__table12334196:

.. table:: **Table 1** Request parameters

   +-----------------------+--------------------------------------------+-----------------------+
   | Parameter             | Description                                | Mandatory             |
   +=======================+============================================+=======================+
   | partNumber            | Indicates the ID of a part to be uploaded. | Yes                   |
   |                       |                                            |                       |
   |                       | Type: integer                              |                       |
   +-----------------------+--------------------------------------------+-----------------------+
   | uploadId              | Indicates a multipart upload ID.           | Yes                   |
   |                       |                                            |                       |
   |                       | Type: string                               |                       |
   +-----------------------+--------------------------------------------+-----------------------+

Request Headers
---------------

In addition the common message headers, the request uses two extended headers. :ref:`Table 3 <obs_04_0007__table25197309>` describes the common message header.

.. table:: **Table 2** Request headers

   +-------------------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------+
   | Header                                                      | Description                                                                                                                                                                                                                 | Mandatory                                                                                                                                  |
   +=============================================================+=============================================================================================================================================================================================================================+============================================================================================================================================+
   | x-obs-copy-source                                           | Indicates the source object to be copied.                                                                                                                                                                                   | Yes                                                                                                                                        |
   |                                                             |                                                                                                                                                                                                                             |                                                                                                                                            |
   |                                                             | Type: string                                                                                                                                                                                                                |                                                                                                                                            |
   +-------------------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------+
   | x-obs-copy-source-range                                     | Indicates the range of bytes (start - end) to be copied from the source object. **start** indicates the start byte of the part to be copied and **end** indicates the end byte.                                             | No                                                                                                                                         |
   |                                                             |                                                                                                                                                                                                                             |                                                                                                                                            |
   |                                                             | Type: integer                                                                                                                                                                                                               |                                                                                                                                            |
   +-------------------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------+
   | x-obs-server-side-encryption-customer-algorithm             | Indicates an algorithm used to encrypt a destination part. The header is used in SSE-C mode.                                                                                                                                | No. This header is required when SSE-C is used. The encryption algorithm must be the same as that used to initiate multipart upload tasks. |
   |                                                             |                                                                                                                                                                                                                             |                                                                                                                                            |
   |                                                             | Type: string                                                                                                                                                                                                                |                                                                                                                                            |
   |                                                             |                                                                                                                                                                                                                             |                                                                                                                                            |
   |                                                             | Example: x-obs-server-side-encryption-customer-algorithm:AES256                                                                                                                                                             |                                                                                                                                            |
   |                                                             |                                                                                                                                                                                                                             |                                                                                                                                            |
   |                                                             | Constraint: This header must be used together with **x-obs-server-side-encryption-customer-key** and **x-obs-server-side-encryption-customer-key-MD5**.                                                                     |                                                                                                                                            |
   +-------------------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------+
   | x-obs-server-side-encryption-customer-key                   | Indicates a key used to encrypt a destination part. The header is used in SSE-C mode. This key is used to encrypt objects.                                                                                                  | No. This header is required when SSE-C is used. The key must be the same as that used to initiate multipart upload tasks.                  |
   |                                                             |                                                                                                                                                                                                                             |                                                                                                                                            |
   |                                                             | Type: string                                                                                                                                                                                                                |                                                                                                                                            |
   |                                                             |                                                                                                                                                                                                                             |                                                                                                                                            |
   |                                                             | Example: x-obs-server-side-encryption-customer-key:K7QkYpBkM5+hca27fsNkUnNVaobncnLht/rCB2o/9Cw=                                                                                                                             |                                                                                                                                            |
   |                                                             |                                                                                                                                                                                                                             |                                                                                                                                            |
   |                                                             | Constraint: This header is a Base64-encoded 256-bit key and must be used together with **x-obs-server-side-encryption-customer-algorithm** and **x-obs-server-side-encryption-customer-key-MD5**.                           |                                                                                                                                            |
   +-------------------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------+
   | x-obs-server-side-encryption-customer-key-MD5               | Indicates the MD5 value of a key used to encrypt a destination part. The header is used in SSE-C mode. The MD5 value is used to check whether any error occurs during the transmission of the key.                          | No. This header is required when SSE-C is used. The MD5 value must be the same as that used to initiate multipart upload tasks.            |
   |                                                             |                                                                                                                                                                                                                             |                                                                                                                                            |
   |                                                             | Type: string                                                                                                                                                                                                                |                                                                                                                                            |
   |                                                             |                                                                                                                                                                                                                             |                                                                                                                                            |
   |                                                             | Example: x-obs-server-side-encryption-customer-key-MD5:4XvB3tbNTN+tIEVa0/fGaQ==                                                                                                                                             |                                                                                                                                            |
   |                                                             |                                                                                                                                                                                                                             |                                                                                                                                            |
   |                                                             | Constraint: This header is a Base64-encoded 128-bit MD5 value and must be used together with **x-obs-server-side-encryption-customer-algorithm** and **x-obs-server-side-encryption-customer-key**.                         |                                                                                                                                            |
   +-------------------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------+
   | x-obs-copy-source-server-side-encryption-customer-algorithm | Indicates an algorithm used by a source object. The header is used in SSE-C mode.                                                                                                                                           | No. This header is required when SSE-C is used to copy a source object.                                                                    |
   |                                                             |                                                                                                                                                                                                                             |                                                                                                                                            |
   |                                                             | Type: string                                                                                                                                                                                                                |                                                                                                                                            |
   |                                                             |                                                                                                                                                                                                                             |                                                                                                                                            |
   |                                                             | Example: x-obs-copy-source-server-side-encryption-customer-algorithm:AES256                                                                                                                                                 |                                                                                                                                            |
   |                                                             |                                                                                                                                                                                                                             |                                                                                                                                            |
   |                                                             | Constraint: This header must be used together with **x-obs-copy-source-server-side-encryption-customer-key** and **x-obs-copy-source-server-side-encryption-customer-key-MD5**.                                             |                                                                                                                                            |
   +-------------------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------+
   | x-obs-copy-source-server-side-encryption-customer-key       | Indicates the algorithm used to decrypt a source object. The header is used in SSE-C mode.                                                                                                                                  | No. This header is required when SSE-C is used to copy a source object.                                                                    |
   |                                                             |                                                                                                                                                                                                                             |                                                                                                                                            |
   |                                                             | Type: string                                                                                                                                                                                                                |                                                                                                                                            |
   |                                                             |                                                                                                                                                                                                                             |                                                                                                                                            |
   |                                                             | Example: x-obs-copy-source-server-side-encryption-customer-key:K7QkYpBkM5+hca27fsNkUnNVaobncnLht/rCB2o/9Cw=                                                                                                                 |                                                                                                                                            |
   |                                                             |                                                                                                                                                                                                                             |                                                                                                                                            |
   |                                                             | Constraint: This header is a Base64-encoded 256-bit key and must be used together with **x-obs-copy-source-server-side-encryption-customer-algorithm** and **x-obs-copy-source-server-side-encryption-customer-key-MD5**.   |                                                                                                                                            |
   +-------------------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------+
   | x-obs-copy-source-server-side-encryption-customer-key-MD5   | Indicates the MD5 value of the key used for the source object. The header is used in SSE-C mode. The MD5 value is used to check whether any error occurs during the transmission of the key.                                | No. This header is required when SSE-C is used to copy a source object.                                                                    |
   |                                                             |                                                                                                                                                                                                                             |                                                                                                                                            |
   |                                                             | Type: string                                                                                                                                                                                                                |                                                                                                                                            |
   |                                                             |                                                                                                                                                                                                                             |                                                                                                                                            |
   |                                                             | Example: x-obs-copy-source-server-side-encryption-customer-key-MD5:4XvB3tbNTN+tIEVa0/fGaQ==                                                                                                                                 |                                                                                                                                            |
   |                                                             |                                                                                                                                                                                                                             |                                                                                                                                            |
   |                                                             | Constraint: This header is a Base64-encoded 128-bit MD5 value and must be used together with **x-obs-copy-source-server-side-encryption-customer-algorithm** and **x-obs-copy-source-server-side-encryption-customer-key**. |                                                                                                                                            |
   +-------------------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------+

Request Elements
----------------

This request involves no elements.

Response Syntax
---------------

.. code-block::

   HTTP/1.1 status_code
   Date: date

   <?xml version="1.0" encoding="UTF-8" standalone="yes"?>
   <CopyPartResult xmlns="http://obs.region.example.com/doc/2015-06-30/">
       <LastModified>modifiedDate</LastModified>
       <ETag>etag</ETag>
   </CopyPartResult>

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
   |                                                 | Example: x-obs-server-side-encryption:kms                                                                                                                                         |
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
   |                                                 | Example: x-obs-server-side-encryption-customer-algorithm:AES256                                                                                                                   |
   +-------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | x-obs-server-side-encryption-customer-key-MD5   | Indicates the MD5 value of a key used to encrypt objects. This header is included in a response if SSE-C is used.                                                                 |
   |                                                 |                                                                                                                                                                                   |
   |                                                 | Type: string                                                                                                                                                                      |
   |                                                 |                                                                                                                                                                                   |
   |                                                 | Example: x-obs-server-side-encryption-customer-key-MD5:4XvB3tbNTN+tIEVa0/fGaQ==                                                                                                   |
   +-------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Response Elements
-----------------

This response contains elements of a part copy result. :ref:`Table 4 <obs_04_0100__table44628158>` describes the elements.

.. _obs_04_0100__table44628158:

.. table:: **Table 4** Response elements

   +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------+
   | Element                           | Description                                                                                                                               |
   +===================================+===========================================================================================================================================+
   | LastModified                      | Indicates the latest time an object was modified.                                                                                         |
   |                                   |                                                                                                                                           |
   |                                   | Type: string                                                                                                                              |
   +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------+
   | ETag                              | ETag value of the target part. It is the unique identifier of the part content and is used to verify data consistency when merging parts. |
   |                                   |                                                                                                                                           |
   |                                   | Type: string                                                                                                                              |
   +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------+

Error Responses
---------------

#. If the AK or signature is invalid, OBS returns **403 Forbidden** and the error code is **AccessDenied**.
#. Check whether the source bucket or destination bucket exists. If the source bucket or destination bucket does not exist, OBS returns **404 Not Found** and the error code is **NoSuchBucket**.
#. If the source object does not exist, OBS returns **404 Not Found** and the error code is **NoSuchKey**.
#. If the user does not have the read permission for the specified object, OBS returns **403 Forbidden** and the error code is **AccessDenied**.
#. If the user does not have the write permission for the destination bucket, OBS returns **403 Forbidden** and the error code is **AccessDenied**.
#. If the specified task does not exist, OBS returns **404 Not Found** and the error code is **NoSuchUpload**.
#. If the user is not the initiator of the multipart upload task, OBS returns **403 Forbidden** and the error code is **AccessDenied**.
#. When the size of a copied part has exceeded 5 GB, OBS returns **400 Bad Request**.
#. If a part number is not within the range from 1 to 10000, OBS returns error code **400 Bad Request**.

Other errors are included in :ref:`Table 2 <obs_04_0115__d0e843>`.

Sample Request
--------------

.. code-block:: text

   PUT /tobject02?partNumber=2&uploadId=00000163D40171ED8DF4050919BD02B8 HTTP/1.1
   User-Agent: curl/7.29.0
   Host: examplebucket.obs.region.example.com
   Accept: */*
   Date: WED, 01 Jul 2015 05:16:32 GMT
   Authorization: OBS H4IPJX0TQTHTHEBQQCEC:dSnpnNpawDSsLg/xXxaqFzrAmMw=
   x-obs-copy-source: /destbucket/object01

Sample Response
---------------

::

   HTTP/1.1 200 OK
   Server: OBS
   x-obs-request-id: 8DF400000163D40ABBD20405D30B0542
   x-obs-id-2: 32AAAQAAEAABAAAQAAEAABAAAQAAEAABCTIJpD2efLy5o8sTTComwBb2He0j11Ne
   Content-Type: application/xml
   Date: WED, 01 Jul 2015 05:16:32 GMT
   Transfer-Encoding: chunked

   <?xml version="1.0" encoding="UTF-8" standalone="yes"?>
   <CopyPartResult xmlns="http://obs.example.com/doc/2015-06-30/">
     <LastModified>2015-07-01T05:16:32.344Z</LastModified>
     <ETag>"3b46eaf02d3b6b1206078bb86a7b7013"</ETag>
   </CopyPartResult>
