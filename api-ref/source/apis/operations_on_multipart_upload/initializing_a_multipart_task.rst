:original_name: obs_04_0098.html

.. _obs_04_0098:

Initializing a Multipart Task
=============================

Functions
---------

Before using this operation, make an API operation call to create a multipart upload task. The system will return a globally unique upload ID as the multipart upload identifier. This identifier can be used in subsequent requests including UploadPart, CompleteMultipartUpload, and ListParts. Create a multipart upload task does not affect the object that has the same name as object to be uploaded in multiple parts. You can create more than one multipart upload tasks for an object. This operation request can contain headers **x-obs-acl**, **x-obs-meta-\***, **Content-Type**, and **Content-Encoding**. The headers are recorded in the multipart upload metadata.

This operation supports server-side encryption.

Request Syntax
--------------

.. code-block:: text

   POST /ObjectName?uploads  HTTP/1.1
   Host: bucketname.obs.region.example.com
   Date: date
   Authorization: authorization

Request Parameters
------------------

This request uses parameters to specify a multipart upload. :ref:`Table 1 <obs_04_0098__table13291134>` describes the parameters.

.. _obs_04_0098__table13291134:

.. table:: **Table 1** Request parameters

   +-----------------------+-------------------------------+-----------------------+
   | Parameter             | Description                   | Mandatory             |
   +=======================+===============================+=======================+
   | uploads               | Indicates a multipart upload. | Yes                   |
   |                       |                               |                       |
   |                       | Type: string                  |                       |
   +-----------------------+-------------------------------+-----------------------+

Request Headers
---------------

The request can use additional headers, as shown in :ref:`Table 2 <obs_04_0098__table11912770163049>`.

.. _obs_04_0098__table11912770163049:

.. table:: **Table 2** Request headers

   +-------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+---------------------------------------------------+
   | Header                                          | Description                                                                                                                                                                                                                                      | Mandatory                                         |
   +=================================================+==================================================================================================================================================================================================================================================+===================================================+
   | x-obs-acl                                       | When initializing a multipart upload task, you can add this message header to set the permission control policy for the object. The predefined common policies are as follows: **private**, **public-read**, and **public-read-write**.          | No                                                |
   |                                                 |                                                                                                                                                                                                                                                  |                                                   |
   |                                                 | Type: string                                                                                                                                                                                                                                     |                                                   |
   |                                                 |                                                                                                                                                                                                                                                  |                                                   |
   |                                                 | Note: This header is a predefined policy expressed in a character string.                                                                                                                                                                        |                                                   |
   |                                                 |                                                                                                                                                                                                                                                  |                                                   |
   |                                                 | Example: **x-obs-acl: public-read-write**                                                                                                                                                                                                        |                                                   |
   +-------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+---------------------------------------------------+
   | x-obs-grant-read                                | When initializing a multipart upload task, you can use this header to authorize all users in an account to read the object and obtain the object metadata.                                                                                       | No                                                |
   |                                                 |                                                                                                                                                                                                                                                  |                                                   |
   |                                                 | Type: string                                                                                                                                                                                                                                     |                                                   |
   |                                                 |                                                                                                                                                                                                                                                  |                                                   |
   |                                                 | Example: **x-obs-grant-read: ID=domainID** If multiple accounts are authorized, separate them with commas (,).                                                                                                                                   |                                                   |
   +-------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+---------------------------------------------------+
   | x-obs-grant-read-acp                            | When initializing a multipart upload task, you can use this header to authorize all users in an account the permission to obtain the object ACL.                                                                                                 | No                                                |
   |                                                 |                                                                                                                                                                                                                                                  |                                                   |
   |                                                 | Type: string                                                                                                                                                                                                                                     |                                                   |
   |                                                 |                                                                                                                                                                                                                                                  |                                                   |
   |                                                 | Example: **x-obs-grant-read-acp: ID=domainID** If multiple accounts are authorized, separate them with commas (,).                                                                                                                               |                                                   |
   +-------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+---------------------------------------------------+
   | x-obs-grant-write-acp                           | When initializing a multipart upload task, you can use this header to authorize all users in an account the permission to write the object ACL.                                                                                                  | No                                                |
   |                                                 |                                                                                                                                                                                                                                                  |                                                   |
   |                                                 | Type: string                                                                                                                                                                                                                                     |                                                   |
   |                                                 |                                                                                                                                                                                                                                                  |                                                   |
   |                                                 | Example: **x-obs-grant-write-acp: ID=domainID** If multiple accounts are authorized, separate them with commas (,).                                                                                                                              |                                                   |
   +-------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+---------------------------------------------------+
   | x-obs-grant-full-control                        | When initializing a multipart upload task, you can use this header to authorize all users in an account the permission to read the object, obtain the object metadata, obtain the object ACL, and write the object ACL.                          | No                                                |
   |                                                 |                                                                                                                                                                                                                                                  |                                                   |
   |                                                 | Type: string                                                                                                                                                                                                                                     |                                                   |
   |                                                 |                                                                                                                                                                                                                                                  |                                                   |
   |                                                 | Example: **x-obs-grant-full-control: ID=domainID** If multiple accounts are authorized, separate them with commas (,).                                                                                                                           |                                                   |
   +-------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+---------------------------------------------------+
   | x-obs-storage-class                             | When initiating a multi-part upload task, you can add this header to specify the storage class for the object. If you do not use this header, the object storage class is the default storage class of the bucket.                               | No                                                |
   |                                                 |                                                                                                                                                                                                                                                  |                                                   |
   |                                                 | Type: string                                                                                                                                                                                                                                     |                                                   |
   |                                                 |                                                                                                                                                                                                                                                  |                                                   |
   |                                                 | Note: There are three storage classes: STANDARD (Standard storage class), WARM (Warm storage class), and COLD (Cold storage class). Therefore, this parameter value can be **STANDARD**, **WARM**, or **COLD**. These values are case sensitive. |                                                   |
   |                                                 |                                                                                                                                                                                                                                                  |                                                   |
   |                                                 | Example: x-obs-storage-class: STANDARD                                                                                                                                                                                                           |                                                   |
   +-------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+---------------------------------------------------+
   | x-obs-website-redirect-location                 | If a bucket is configured with the static website hosting function, it will redirect requests for this object to another object in the same bucket or to an external URL. OBS stores the value of this header in the object metadata.            | No                                                |
   |                                                 |                                                                                                                                                                                                                                                  |                                                   |
   |                                                 | Type: string                                                                                                                                                                                                                                     |                                                   |
   |                                                 |                                                                                                                                                                                                                                                  |                                                   |
   |                                                 | Default value: none                                                                                                                                                                                                                              |                                                   |
   |                                                 |                                                                                                                                                                                                                                                  |                                                   |
   |                                                 | Constraint: The value must be prefixed by a slash (/), **http://**, or **https://**. The length of the value cannot exceed 2 KB.                                                                                                                 |                                                   |
   +-------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+---------------------------------------------------+
   | x-obs-server-side-encryption                    | Indicates that SSE-KMS is used.                                                                                                                                                                                                                  | No. This header is required when SSE-KMS is used. |
   |                                                 |                                                                                                                                                                                                                                                  |                                                   |
   |                                                 | Type: string                                                                                                                                                                                                                                     |                                                   |
   |                                                 |                                                                                                                                                                                                                                                  |                                                   |
   |                                                 | Example: x-obs-server-side-encryption:kms                                                                                                                                                                                                        |                                                   |
   +-------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+---------------------------------------------------+
   | x-obs-server-side-encryption-kms-key-id         | Master key ID. This header is used in SSE-KMS mode. If the customer does not provide the master key ID, the default master key ID will be used.                                                                                                  | No                                                |
   |                                                 |                                                                                                                                                                                                                                                  |                                                   |
   |                                                 | Type: string                                                                                                                                                                                                                                     |                                                   |
   |                                                 |                                                                                                                                                                                                                                                  |                                                   |
   |                                                 | The following two formats are supported:                                                                                                                                                                                                         |                                                   |
   |                                                 |                                                                                                                                                                                                                                                  |                                                   |
   |                                                 | 1. *regionID*\ **:**\ *domainID*\ **:key/**\ *key_id*                                                                                                                                                                                            |                                                   |
   |                                                 |                                                                                                                                                                                                                                                  |                                                   |
   |                                                 | 2. *key_id*                                                                                                                                                                                                                                      |                                                   |
   |                                                 |                                                                                                                                                                                                                                                  |                                                   |
   |                                                 | *regionID* is the ID of the region to which the key belongs. *domainID* is the account ID of the tenant to which the key belongs. *key_id* is the key ID created in KMS.                                                                         |                                                   |
   |                                                 |                                                                                                                                                                                                                                                  |                                                   |
   |                                                 | Example:                                                                                                                                                                                                                                         |                                                   |
   |                                                 |                                                                                                                                                                                                                                                  |                                                   |
   |                                                 | 1. x-obs-server-side-encryption-kms-key-id:*region*:domainiddomainiddomainiddoma0001:key/4f1cd4de-ab64-4807-920a-47fc42e7f0d0                                                                                                                    |                                                   |
   |                                                 |                                                                                                                                                                                                                                                  |                                                   |
   |                                                 | 2. x-obs-server-side-encryption-kms-key-id:4f1cd4de-ab64-4807-920a-47fc42e7f0d0                                                                                                                                                                  |                                                   |
   +-------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+---------------------------------------------------+
   | x-obs-server-side-encryption-customer-algorithm | Indicates an encryption algorithm. The header is used in SSE-C mode.                                                                                                                                                                             | No. This header is required when SSE-C is used.   |
   |                                                 |                                                                                                                                                                                                                                                  |                                                   |
   |                                                 | Type: string                                                                                                                                                                                                                                     |                                                   |
   |                                                 |                                                                                                                                                                                                                                                  |                                                   |
   |                                                 | Example: x-obs-server-side-encryption-customer-algorithm:AES256                                                                                                                                                                                  |                                                   |
   |                                                 |                                                                                                                                                                                                                                                  |                                                   |
   |                                                 | Constraint: This header must be used together with **x-obs-server-side-encryption-customer-key** and **x-obs-server-side-encryption-customer-key-MD5**.                                                                                          |                                                   |
   +-------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+---------------------------------------------------+
   | x-obs-server-side-encryption-customer-key       | The key used to encrypt objects. The header is used in SSE-C mode. This key is used to encrypt objects.                                                                                                                                          | No. This header is required when SSE-C is used.   |
   |                                                 |                                                                                                                                                                                                                                                  |                                                   |
   |                                                 | Type: string                                                                                                                                                                                                                                     |                                                   |
   |                                                 |                                                                                                                                                                                                                                                  |                                                   |
   |                                                 | Example: x-obs-server-side-encryption-customer-key:K7QkYpBkM5+hca27fsNkUnNVaobncnLht/rCB2o/9Cw=                                                                                                                                                  |                                                   |
   |                                                 |                                                                                                                                                                                                                                                  |                                                   |
   |                                                 | Constraint: This header is a Base64-encoded 256-bit key and must be used together with **x-obs-server-side-encryption-customer-algorithm** and **x-obs-server-side-encryption-customer-key-MD5**.                                                |                                                   |
   +-------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+---------------------------------------------------+
   | x-obs-server-side-encryption-customer-key-MD5   | Indicates the MD5 value of a key used to encrypt objects. The header is used in SSE-C mode. The MD5 value is used to check whether any error occurs during the transmission of the key.                                                          | No. This header is required when SSE-C is used.   |
   |                                                 |                                                                                                                                                                                                                                                  |                                                   |
   |                                                 | Type: string                                                                                                                                                                                                                                     |                                                   |
   |                                                 |                                                                                                                                                                                                                                                  |                                                   |
   |                                                 | Example: x-obs-server-side-encryption-customer-key-MD5:4XvB3tbNTN+tIEVa0/fGaQ==                                                                                                                                                                  |                                                   |
   |                                                 |                                                                                                                                                                                                                                                  |                                                   |
   |                                                 | Constraint: This header is a Base64-encoded 128-bit MD5 value and must be used together with **x-obs-server-side-encryption-customer-algorithm** and **x-obs-server-side-encryption-customer-key**.                                              |                                                   |
   +-------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+---------------------------------------------------+
   | x-obs-expires                                   | Indicates the expiration time of an object, in days. An object will be automatically deleted once it expires (calculated from the last modification time of the object).                                                                         | No                                                |
   |                                                 |                                                                                                                                                                                                                                                  |                                                   |
   |                                                 | Type: integer                                                                                                                                                                                                                                    |                                                   |
   |                                                 |                                                                                                                                                                                                                                                  |                                                   |
   |                                                 | Example: x-obs-expires:3                                                                                                                                                                                                                         |                                                   |
   +-------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+---------------------------------------------------+

For details about other common message headers, see :ref:`Table 3 <obs_04_0007__table25197309>`.

Request Elements
----------------

This request involves no elements.

Response Syntax
---------------

::

   HTTP/1.1 status_code
   Date: date
   Content-Length: length
   Connection: status

   <?xml version="1.0" encoding="UTF-8" standalone="yes"?>
   <InitiateMultipartUploadResult xmlns="http://obs.region.example.com/doc/2015-06-30/">
       <Bucket>BucketName</Bucket>
       <Key>ObjectName</Key>
       <UploadId>uploadID</UploadId>
   </InitiateMultipartUploadResult>

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
   |                                                 | Example: x-obs-server-side-encryption-kms-key-id:*region*:domainiddomainiddomainiddoma0001:key/4f1cd4de-ab64-4807-920a-47fc42e7f0d0                                               |
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

This response contains elements to indicate the upload ID and the key (name) of the object (bucket) for which the multipart upload was initiated. The returned information is used in the subsequent operations. :ref:`Table 4 <obs_04_0098__table6651816>` describes the elements.

.. _obs_04_0098__table6651816:

.. table:: **Table 4** Response elements

   +-----------------------------------+----------------------------------------------------------------------------------------------------+
   | Element                           | Description                                                                                        |
   +===================================+====================================================================================================+
   | InitiateMultipartUploadResult     | Container of a multipart upload task.                                                              |
   |                                   |                                                                                                    |
   |                                   | Type: XML                                                                                          |
   +-----------------------------------+----------------------------------------------------------------------------------------------------+
   | Bucket                            | Indicates the name of the bucket to which the multipart upload was initiated.                      |
   |                                   |                                                                                                    |
   |                                   | Type: string                                                                                       |
   +-----------------------------------+----------------------------------------------------------------------------------------------------+
   | Key                               | Indicates the object key in a multipart upload.                                                    |
   |                                   |                                                                                                    |
   |                                   | Type: string                                                                                       |
   +-----------------------------------+----------------------------------------------------------------------------------------------------+
   | UploadId                          | Indicates the ID for the initiated multipart upload. This ID is used for the subsequent operation. |
   |                                   |                                                                                                    |
   |                                   | Type: string                                                                                       |
   +-----------------------------------+----------------------------------------------------------------------------------------------------+

Error Responses
---------------

1. If the AK or signature is invalid, OBS returns **403 Forbidden** and the error code is **AccessDenied**.

2. If the bucket does not exist, OBS returns **404 Not Found** and the error code is **NoSuchBucket**.

3. Check whether the user has the write permission for the specified bucket. If no, OBS returns **403 Forbidden** and the error code is **AccessDenied**.

Other errors are included in :ref:`Table 2 <obs_04_0115__d0e843>`.

Sample Request 1
----------------

**Initialize a multipart task.**

.. code-block:: text

   POST /objectkey?uploads  HTTP/1.1
   Host: examplebucket.obs.region.example.com
   Date: WED, 01 Jul 2015 05:14:52 GMT
   Authorization: OBS AKIAIOSFODNN7EXAMPLE:VGhpcyBtZXNzYWdlIHNpZ25lZGGieSRlbHZpbmc=

Sample Response 1
-----------------

::

   HTTP/1.1 200 OK
   Server: OBS
   x-obs-id-2: Weag1LuByRx9e6j5Onimru9pO4ZVKnJ2Qz7/C1NPcfTWAtRPfTaOFg==
   x-obs-request-id: 996c76696e6727732072657175657374
   Date: WED, 01 Jul 2015 05:14:52 GMT
   Content-Length: 303

   <?xml version="1.0" encoding="UTF-8" standalone="yes"?>
   <InitiateMultipartUploadResult xmlns="http://obs.region.example.com/doc/2015-06-30/">
     <Bucket>bucketname</Bucket>
     <Key>objectkey</Key>
     <UploadId>DCD2FC98B4F70000013DF578ACA318E7</UploadId>
   </InitiateMultipartUploadResult>

Sample Request 2
----------------

**The ACL is carried when the multipart task is initialized.**

.. code-block:: text

   POST /objectkey?uploads  HTTP/1.1
   Host: examplebucket.obs.region.example.com
   Date: WED, 01 Jul 2015 05:15:43 GMT
   x-obs-grant-write-acp:ID=52f24s3593as5730ea4f722483579ai7,ID=a93fcas852f24s3596ea8366794f7224
   Authorization: OBS AKIAIOSFODNN7EXAMPLE:VGhpcyBtZXNzYWdlIHNpZ25lZGGieSRlbHZpbmc=

Sample Response 2
-----------------

::

   HTTP/1.1 200 OK
   Server: OBS
   x-obs-id-2: 32AAAQAAEAABAAAQAAEAABAAAQAAEAABCTnv+daB51p+IVhAvWN7s5rSKhcWqDFs
   x-obs-request-id: BB78000001648457112DF37FDFADD7AD
   Date: WED, 01 Jul 2015 05:15:43 GMT
   Content-Length: 303

   <?xml version="1.0" encoding="UTF-8" standalone="yes"?>
   <InitiateMultipartUploadResult xmlns="http://obs.region.example.com/doc/2015-06-30/">
     <Bucket>bucketname</Bucket>
     <Key>objectkey</Key>
     <UploadId>000001648453845DBB78F2340DD460D8</UploadId>
   </InitiateMultipartUploadResult>
