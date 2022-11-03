:original_name: obs_04_0106.html

.. _obs_04_0106:

Server-Side Encryption (SSE-KMS)
================================

In the SSE-KMS mode, OBS uses the keys provided by KMS for server-side encryption. When an object encrypted using SSE-KMS is added to a bucket in a region for the first time, OBS creates a default customer master key (CMK), which is used to encrypt and decrypt the keys provided by KMS. The SSE-KMS mode does not support the keys created by customers. The bucket ACL and policy do not allow cross-tenant authorized access to objects encrypted using SSE-KMS.

Two headers are added to support SSE-KMS in SSE-KMS mode.

You can also configure the default encryption method for a bucket to encrypt objects in the bucket. When default encryption is enabled for a bucket, any request for uploading objects without specified encryption header will trigger the default bucket encryption for the objects uploaded. For more information about bucket encryption configuration, see :ref:`Configuring Bucket Encryption <obs_04_0062>`.

.. table:: **Table 1** Header fields used in SSE-KMS mode

   +-----------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Element                                 | Description                                                                                                                                                                          |
   +=========================================+======================================================================================================================================================================================+
   | x-obs-server-side-encryption            | Indicates that SSE-KMS is used. Objects are encrypted using SSE-KMS.                                                                                                                 |
   |                                         |                                                                                                                                                                                      |
   |                                         | Type: string                                                                                                                                                                         |
   |                                         |                                                                                                                                                                                      |
   |                                         | Example: x-obs-server-side-encryption:kms                                                                                                                                            |
   +-----------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | x-obs-server-side-encryption-kms-key-id | Indicates the master key ID of an encrypted object. This header is used in SSE-KMS mode. If the customer does not provide the master key ID, the default master key ID will be used. |
   |                                         |                                                                                                                                                                                      |
   |                                         | Type: string                                                                                                                                                                         |
   |                                         |                                                                                                                                                                                      |
   |                                         | The following two formats are supported:                                                                                                                                             |
   |                                         |                                                                                                                                                                                      |
   |                                         | 1. *regionID*\ **:**\ *domainID*\ **:key/**\ *key_id*                                                                                                                                |
   |                                         |                                                                                                                                                                                      |
   |                                         | 2. *key_id*                                                                                                                                                                          |
   |                                         |                                                                                                                                                                                      |
   |                                         | **regionID** is the ID of the region to which the key belongs. **domainID** is the account ID of the tenant to which the key belongs. **key_id** is the key ID created inKMS.        |
   |                                         |                                                                                                                                                                                      |
   |                                         | Example:                                                                                                                                                                             |
   |                                         |                                                                                                                                                                                      |
   |                                         | 1. x-obs-server-side-encryption-kms-key-id:*region*:domainiddomainiddomainiddoma0001:key/4f1cd4de-ab64-4807-920a-47fc42e7f0d0                                                        |
   |                                         |                                                                                                                                                                                      |
   |                                         | 2. x-obs-server-side-encryption-kms-key-id:4f1cd4de-ab64-4807-920a-47fc42e7f0d0                                                                                                      |
   +-----------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

API operations to which the newly added headers apply:

-  PUT operation for uploading objects
-  POST operation for uploading objects (**x-obs-server-side-encryption** and **x-obs-server-side-encryption-kms-key-id** need to be placed in the table instead of the header field)
-  PutObject-Copy (the newly added headers apply to target objects)
-  API operations for initiating a multipart upload task

OBS supports bucket policies. You can use a bucket policy to implement server-side encryption on all the objects stored in a bucket. For example, a tenant's object upload request does not contain the header **x-obs-server-side-encryption:"kms"** for server-side encryption (SSE-KMS), the following bucket policy will reject the upload request.

.. code-block::

   {
   "Statement":[{
   "Sid":"DenyUnEncryptedObjectUploads",
   "Effect":"Deny",
   "Principal":"*",
   "Action":"PutObject",
   "Resource":"YourBucket/*",
   "Condition":{
   "StringNotEquals":{
   "x-obs-server-side-encryption":"kms"
   }
   }
   }
   }

Sample Request 1
----------------

**Use the default key to encrypt the uploaded object**.

.. code-block:: text

   PUT /encryp1 HTTP/1.1
   User-Agent: curl/7.29.0
   Host: examplebucket.obs.region.example.com
   Accept: */*
   Date: Wed, 06 Jun 2018 09:08:21 GMT
   Authorization: OBS H4IPJX0TQTHTHEBQQCEC:f3/7eS6MFbW3JO4+7I5AtyAQENU=
   x-obs-server-side-encryption:kms
   Content-Length: 5242
   Expect: 100-continue

   [5242 Byte object contents]

Sample Response 1
-----------------

::

   HTTP/1.1 200 OK
   Server: OBS
   x-obs-request-id: 8DF400000163D45AA81D038B6AE4C482
   ETag: "d8bffdfbab5345d91ac05141789d2477"
   x-obs-server-side-encryption: kms
   x-obs-server-side-encryption-kms-key-id: region:783fc6652cf246c096ea836694f71855:key/522d6070-5ad3-4765-9737-9312ddc72cdb
   x-obs-id-2: 32AAAUJAIAABAAAQAAEAABAAAQAAEAABCTv7cHmAnGfBAGXUHeibUsiETTNqlCqC
   Date: Wed, 06 Jun 2018 09:08:21 GMT
   Content-Length: 0

Sample Request 2
----------------

**Use a specified key to encrypt the uploaded object**.

.. code-block:: text

   PUT /encryp1 HTTP/1.1
   User-Agent: curl/7.29.0
   Host: examplebucket.obs.region.example.com
   Accept: */*
   Date: Wed, 06 Jun 2018 09:08:50 GMT
   Authorization: OBS H4IPJX0TQTHTHEBQQCEC:f3/PWjkXYTYGs5lPOctTNEI2QENU=
   x-obs-server-side-encryption:kms
   x-obs-server-side-encryption-kms-key-id: 522d6070-5ad3-4765-43a7-a7d1-ab21f498482d
   Content-Length: 5242
   Expect: 100-continue

   [5242 Byte object contents]

Sample Response 2
-----------------

::

   HTTP/1.1 200 OK
   Server: OBS
   x-obs-request-id: 8DF400000163D45AA81D038B6AE4C482
   ETag: "d8bffdfbab5345d91ac05141789d2477"
   x-obs-server-side-encryption: kms
   x-obs-server-side-encryption-kms-key-id: region:783fc6652cf246c096ea836694f71855:key/522d6070-5ad3-4765-43a7-a7d1-ab21f498482d
   x-obs-id-2: 32AAAUJAIAABAdiAEAABA09AEAABCTv7cHmAn12BAG83ibUsiET5eqlCqg
   Date: Wed, 06 Jun 2018 09:08:50 GMT
   Content-Length: 0

Sample Request 3
----------------

**Copy a common object and save it as an encrypted object by encrypting it using a specified key.**

.. code-block:: text

   PUT /destobject HTTP/1.1
   User-Agent: curl/7.29.0
   Host: examplebucket.obs.region.example.com
   x-obs-server-side-encryption:kms
   x-obs-server-side-encryption-kms-key-id: region:783fc6652cf246c096ea836694f71855:key/522d6070-5ad3-4765-9737-9312ddc72cdb
   Accept: */*
   Date: Wed, 06 Jun 2018 09:10:29 GMT
   Authorization: OBS H4IPJX0TQTHTHEBQQCEC:SH3uTrElaGWarVI1uTq325kTVCI=
   x-obs-copy-source: /bucket/srcobject1

Sample Response 3
-----------------

::

   HTTP/1.1 200 OK
   Server: OBS
   x-obs-request-id: BB78000001648480AF3900CED7F15155
   ETag: "d8bffdfbab5345d91ac05141789d2477"
   x-obs-server-side-encryption: kms
   x-obs-server-side-encryption-kms-key-id: region:783fc6652cf246c096ea836694f71855:key/522d6070-5ad3-4765-9737-9312ddc72cdb
   x-obs-id-2: oRAXhgwdaLc9wKVHqTLSmQB7I35D+32AAAUJAIAABAAAQAAEAABAAAQAAEAABCS
   Date: Wed, 06 Jun 2018 09:10:29 GMT
   Content-Length: 0

Sample Request 4
----------------

**Carry the signature in the URL and upload the encrypted object.**

.. code-block:: text

   PUT /destobject?AccessKeyId=UI3SN1SRUQE14OYBKTZB&Expires=1534152518&x-obs-server-side-encryption=kms&Signature=chvmG7%2FDA%2FDCQmTRJu3xngldJpg%3D HTTP/1.1
   User-Agent: curl/7.29.0
   Host: examplebucket.obs.region.example.com
   Accept: */*
   Date: Wed, 06 Jun 2018 09:10:29 GMT

Sample Response 4
-----------------

::

   HTTP/1.1 200 OK
   Server: OBS
   x-obs-request-id: BB78000001648480AF3900CED7F15155
   ETag: "d8bffdfbab5345d91ac05141789d2477"
   x-obs-server-side-encryption: kms
   x-obs-server-side-encryption-kms-key-id: region:783fc6652cf246c096ea836694f71855:key/522d6070-5ad3-4765-9737-9312ddc72cdb
   x-obs-id-2: oRAXhgwdaLc9wKVHqTLSmQB7I35D+32AAAUJAIAABAAAQAAEAABAAAQAAEAABCS
   Date: Wed, 06 Jun 2018 09:10:29 GMT
   Content-Length: 0
