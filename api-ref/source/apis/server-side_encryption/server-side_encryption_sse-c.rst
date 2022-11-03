:original_name: obs_04_0107.html

.. _obs_04_0107:

Server-Side Encryption (SSE-C)
==============================

In the SSE-C mode, OBS uses the keys and MD5 values provided by customers for server-side encryption.

OBS does not store your encryption keys. If you lost your encryption keys, you lost the objects. Six headers are added to support SSE-C.

The following table lists headers that are required when you use SSE-C to encrypt objects.

.. table:: **Table 1** Header fields used for encrypting objects in SSE-C mode

   +-------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Element                                         | Description                                                                                                                                                                                                                                         |
   +=================================================+=====================================================================================================================================================================================================================================================+
   | x-obs-server-side-encryption-customer-algorithm | Indicates an encryption algorithm. The header is used in SSE-C mode.                                                                                                                                                                                |
   |                                                 |                                                                                                                                                                                                                                                     |
   |                                                 | Example: x-obs-server-side-encryption-customer-algorithm: AES256                                                                                                                                                                                    |
   +-------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | x-obs-server-side-encryption-customer-key       | Indicates the key used to encrypt objects in SSE-C mode. The header value is a Base64-encoded 256-bit key.                                                                                                                                          |
   |                                                 |                                                                                                                                                                                                                                                     |
   |                                                 | Example: x-obs-server-side-encryption-customer-key:K7QkYpBkM5+hca27fsNkUnNVaobncnLht/rCB2o/9Cw=                                                                                                                                                     |
   +-------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | x-obs-server-side-encryption-customer-key-MD5   | Indicates the MD5 value of the key used to encrypt an object. The header is used in SSE-C mode. The value of the element is an MD5 Base64-encoded hash. The MD5 value is used to check whether any error occurs during the transmission of the key. |
   |                                                 |                                                                                                                                                                                                                                                     |
   |                                                 | Example: x-obs-server-side-encryption-customer-key-MD5:4XvB3tbNTN+tIEVa0/fGaQ==                                                                                                                                                                     |
   +-------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

API operations to which the newly added headers apply:

-  PutObject
-  PostObject
-  CopyObject (the newly added headers apply to target objects)
-  HeadObject
-  GetObject
-  InitiateMultipartUpload
-  UploadPart
-  UploadPart-Copy (the newly added headers apply to target parts)

The following table lists three headers that are added for CopyObject and UploadPart-Copy operations to support source objects encrypted using SSE-C.

.. table:: **Table 2** Header fields for source objects encrypted by the SSE-C

   +-------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Element                                                     | Description                                                                                                                                                                                       |
   +=============================================================+===================================================================================================================================================================================================+
   | x-obs-copy-source-server-side-encryption-customer-algorithm | Indicates the algorithm used to decrypt a source object. The header is used in SSE-C mode.                                                                                                        |
   |                                                             |                                                                                                                                                                                                   |
   |                                                             | Example: x-obs-server-side-encryption-customer-algorithm: AES256                                                                                                                                  |
   +-------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | x-obs-copy-source-server-side-encryption-customer-key       | Indicates the key used to decrypt a source object. The header is used in SSE-C mode.                                                                                                              |
   |                                                             |                                                                                                                                                                                                   |
   |                                                             | Example: x-obs-copy-source-server-side-encryption-customer-algorithm: K7QkYpBkM5+hca27fsNkUnNVaobncnLht/rCB2o/9Cw=                                                                                |
   +-------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | x-obs-copy-source-server-side-encryption-customer-key-MD5   | Indicates the MD5 value of the key used to decrypt a source object. The header is used in SSE-C mode. The MD5 value is used to check whether any error occurs during the transmission of the key. |
   |                                                             |                                                                                                                                                                                                   |
   |                                                             | Example: x-obs-copy-source-server-side-encryption-customer-key:4XvB3tbNTN+tIEVa0/fGaQ==                                                                                                           |
   +-------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Sample Request 1
----------------

**Upload an object with the SSE-C encryption mode.**

.. code-block:: text

   PUT /encryp2 HTTP/1.1
   User-Agent: curl/7.29.0
   Host: examplebucket.obs.region.example.com
   Accept: */*
   Date: Wed, 06 Jun 2018 09:12:00 GMT
   Authorization: OBS H4IPJX0TQTHTHEBQQCEC:mZSfafoM+llApk0HGOThlqeccu0=
   x-obs-server-side-encryption-customer-algorithm:AES256
   x-obs-server-side-encryption-customer-key:K7QkYpBkM5+hca27fsNkUnNVaobncnLht/rCB2o/9Cw=
   x-obs-server-side-encryption-customer-key-MD5:4XvB3tbNTN+tIEVa0/fGaQ==
   Content-Length: 5242

   [5242 Byte object contents]

Sample Response 1
-----------------

::

   HTTP/1.1 200 OK
   Server: OBS
   x-obs-request-id: 8DF400000163D45E0017055619BD02B8
   ETag: "0f91242c7f3d86f98ae572a686d0696e"
   x-obs-server-side-encryption-customer-algorithm: AES256
   x-obs-server-side-encryption-customer-key-MD5: 4XvB3tbNTN+tIEVa0/fGaQ==
   x-obs-id-2: 32AAAUgAIAABAAAQAAEAABAAAQAAEAABCSSAJ8bTNJV0X+Ote1PtuWecqyMh6zBJ
   Date: Wed, 06 Jun 2018 09:12:00 GMT
   Content-Length: 0

Sample Request 2
----------------

**Copy the SSE-C encrypted object and save it as the KMS encrypted object.**

.. code-block:: text

   PUT /kmsobject HTTP/1.1
   User-Agent: curl/7.29.0
   Host: examplebucket.obs.region.example.com
   Accept: */*
   Date: Wed, 06 Jun 2018 09:20:10 GMT
   Authorization: OBS H4IPJX0TQTHTHEBQQCEC:mZSfafoM+llApk0HGOThlqeccu0=
   x-obs-copy-source-server-side-encryption-customer-algorithm:AES256
   x-obs-copy-source-server-side-encryption-customer-key:K7QkYpBkM5+hca27fsNkUnNVaobncnLht/rCB2o/9Cw=
   x-obs-copy-source-server-side-encryption-customer-key-MD5:4XvB3tbNTN+tIEVa0/fGaQ==
   x-obs-server-side-encryption: kms
   x-obs-copy-source: /examplebucket/encryp2
   Content-Length: 5242

   [5242 Byte object contents]

Sample Response 2
-----------------

::

   HTTP/1.1 200 OK
   Server: OBS
   x-obs-request-id: BB7800000164848E0FC70528B9D92C41
   ETag: "1072e1b96b47d7ec859710068aa70d57"
   x-obs-server-side-encryption: kms
   x-obs-server-side-encryption-kms-key-id: region:783fc6652cf246c096ea836694f71855:key/522d6070-5ad3-4765-9737-9312ddc72cdb
   x-obs-id-2: 32AAAUJAIAABAAAQAAEAABAAAQAAEAABCTkkRzQXs9ECzZcavVRncBqqYNkoAEsr
   Date: Wed, 06 Jun 2018 09:20:10 GMT
   Content-Length: 0

Sample Request 3
----------------

**The URL contains the signature and the SSE-C encrypted object is uploaded.**

.. code-block:: text

   PUT /encrypobject?AccessKeyId=H4IPJX0TQTHTHEBQQCEC&Expires=1532688887&Signature=EQmDuOhaLUrzrzRNZxwS72CXeXM%3D HTTP/1.1
   User-Agent: curl/7.29.0
   Host: examplebucket.obs.region.example.com
   Accept: */*
   x-obs-server-side-encryption-customer-algorithm: AES256
   x-obs-server-side-encryption-customer-key:K7QkYpBkM5+hca27fsNkUnNVaobncnLht/rCB2o/9Cw=
   x-obs-server-side-encryption-customer-key-MD5:4XvB3tbNTN+tIEVa0/fGaQ==
   Content-Length: 5242
   Expect: 100-continue

   [5242 Byte object contents]

Sample Response 3
-----------------

::

   HTTP/1.1 100 Continue
   HTTP/1.1 200 OK
   Server: OBS
   x-obs-request-id: 804F00000164DB5E5B7FB908D3BA8E00
   ETag: "1072e1b96b47d7ec859710068aa70d57"
   x-obs-server-side-encryption-customer-algorithm: AES256
   x-obs-server-side-encryption-customer-key-MD5: 4XvB3tbNTN+tIEVa0/fGaQ==
   x-obs-id-2: 32AAAUJAIAABAAAQAAEAABAAAQAAEAABCTlpxILjhVK/heKOWIP8Wn2IWmQoerfw
   Content-Length: 0
