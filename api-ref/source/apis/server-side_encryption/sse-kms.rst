:original_name: obs_04_0106.html

.. _obs_04_0106:

SSE-KMS
=======

Functions
---------

With SSE-KMS, OBS uses the keys provided by Key Management Service (KMS) for server-side encryption. You can create custom keys on KMS to encrypt your objects. If you do not specify a key, OBS creates a default key the first time you upload an object to the bucket. Custom keys or default keys are used to encrypt and decrypt data encryption keys (DEKs).

.. note::

   When a custom KMS key in a non-default IAM project is used to encrypt objects, only the key owner can upload or download the encrypted objects.

   When the default KMS key in a region is used to encrypt an object, this default key belongs to the object owner. Only the key owner (also the object owner) can upload or download this object.

Newly Added Headers
-------------------

Two headers are added for SSE-KMS. You can configure the headers listed in :ref:`Table 1 <obs_04_0106__table173131815497>` to use SSE-KMS.

You can also configure the default encryption for a bucket to encrypt objects you upload to the bucket. After default encryption is enabled for a bucket, any object upload request without encryption header included will inherit the bucket's encryption settings. For details, see :ref:`Configuring Bucket Encryption <obs_04_0062>`.

.. _obs_04_0106__table173131815497:

.. table:: **Table 1** Headers used in SSE-KMS

   +-----------------------------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Header                                  | Type                  | Description                                                                                                                                                                   |
   +=========================================+=======================+===============================================================================================================================================================================+
   | x-obs-server-side-encryption            | String                | **Definition**:                                                                                                                                                               |
   |                                         |                       |                                                                                                                                                                               |
   |                                         |                       | Encryption mode.                                                                                                                                                              |
   |                                         |                       |                                                                                                                                                                               |
   |                                         |                       | Example: **x-obs-server-side-encryption:AES256**                                                                                                                              |
   |                                         |                       |                                                                                                                                                                               |
   |                                         |                       | **Constraints**:                                                                                                                                                              |
   |                                         |                       |                                                                                                                                                                               |
   |                                         |                       | None                                                                                                                                                                          |
   |                                         |                       |                                                                                                                                                                               |
   |                                         |                       | **Range**:                                                                                                                                                                    |
   |                                         |                       |                                                                                                                                                                               |
   |                                         |                       | -  kms: SSE-KMS is used.                                                                                                                                                      |
   |                                         |                       | -  AES256: SSE-OBS is used and the AES256 algorithm is used.                                                                                                                  |
   |                                         |                       |                                                                                                                                                                               |
   |                                         |                       | **Default value**:                                                                                                                                                            |
   |                                         |                       |                                                                                                                                                                               |
   |                                         |                       | None                                                                                                                                                                          |
   +-----------------------------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | x-obs-server-side-encryption-kms-key-id | String                | **Definition**:                                                                                                                                                               |
   |                                         |                       |                                                                                                                                                                               |
   |                                         |                       | ID of a specified key used for SSE-KMS encryption.                                                                                                                            |
   |                                         |                       |                                                                                                                                                                               |
   |                                         |                       | **Constraints**:                                                                                                                                                              |
   |                                         |                       |                                                                                                                                                                               |
   |                                         |                       | This header can only be used when you specify **kms** for the **x-obs-server-side-encryption** header.                                                                        |
   |                                         |                       |                                                                                                                                                                               |
   |                                         |                       | **Default value**:                                                                                                                                                            |
   |                                         |                       |                                                                                                                                                                               |
   |                                         |                       | If you specify **kms** for encryption but do not specify a key ID, the default master key will be used. If there is not a default master key, OBS will create one and use it. |
   +-----------------------------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

APIs Where SSE-KMS Headers Apply
--------------------------------

You can configure headers about SSE-KMS in the APIs below:

-  :ref:`Uploading Objects - PUT <obs_04_0080>`
-  :ref:`Uploading Objects - POST <obs_04_0081>`: **x-obs-server-side-encryption** and **x-obs-server-side-encryption-kms-key-id** need to be placed in the form instead of headers.
-  :ref:`Copying Objects <obs_04_0082>` (The newly added headers apply to object copies.)
-  :ref:`Initiating a Multipart Upload <obs_04_0098>`

You can configure a bucket policy to restrict the request headers for a specified bucket. For example, if you require that object upload requests do not contain header **x-obs-server-side-encryption:"kms"**, you can use the following bucket policy:

.. code-block::

   {
       "Statement": [
           {
               "Sid": "DenyUnEncryptedObjectUploads",
               "Effect": "Deny",
               "Principal": "*",
               "Action": "PutObject",
               "Resource": "YourBucket/*",
               "Condition": {
                   "StringNotEquals": {
                       "x-obs-server-side-encryption": "kms"
                   }
               }
           }
       ]
   }

Sample Request: Using the Default Key to Encrypt an Object
----------------------------------------------------------

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

Sample Response: Using the Default Key to Encrypt an Object
-----------------------------------------------------------

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

Sample Request: Using a Custom Key to Encrypt an Object
-------------------------------------------------------

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

Sample Response: Using a Custom Key to Encrypt an Object
--------------------------------------------------------

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

Sample Request: Using a Key to Encrypt an Object Copy
-----------------------------------------------------

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

Sample Response: Using a Key to Encrypt an Object Copy
------------------------------------------------------

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

Sample Request: Uploading an Encrypted Object Using a Signed URL
----------------------------------------------------------------

.. code-block:: text

   PUT /destobject?AccessKeyId=UI3SN1SRUQE14OYBKTZB&Expires=1534152518&x-obs-server-side-encryption=kms&Signature=chvmG7%2FDA%2FDCQmTRJu3xngldJpg%3D HTTP/1.1
   User-Agent: curl/7.29.0
   Host: examplebucket.obs.region.example.com
   Accept: */*
   Date: Wed, 06 Jun 2018 09:10:29 GMT

Sample Response: Uploading an Encrypted Object Using a Signed URL
-----------------------------------------------------------------

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
