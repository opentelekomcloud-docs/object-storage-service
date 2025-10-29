:original_name: obs_04_0107.html

.. _obs_04_0107:

SSE-C
=====

Functions
---------

With SSE-C used, OBS uses the keys and MD5 values provided by customers for server-side encryption.

Newly Added Headers
-------------------

OBS does not store your encryption keys. If you lost them, you lost the objects. Six headers are added to support SSE-C.

The following table lists headers that are required when you use SSE-C to encrypt objects.

.. table:: **Table 1** Header fields used for encrypting objects in SSE-C mode

   +-------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Element                                         | Description                                                                                                                                                                                   |
   +=================================================+===============================================================================================================================================================================================+
   | x-obs-server-side-encryption-customer-algorithm | Indicates the encryption algorithm for the object when SSE-C is used.                                                                                                                         |
   |                                                 |                                                                                                                                                                                               |
   |                                                 | Example: **x-obs-server-side-encryption-customer-algorithm: AES256**                                                                                                                          |
   +-------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | x-obs-server-side-encryption-customer-key       | Indicates the key for encrypting objects when SSE-C is used. Its value is a Base64-encoded 256-bit key.                                                                                       |
   |                                                 |                                                                                                                                                                                               |
   |                                                 | Example: **x-obs-server-side-encryption-customer-key:K7QkYpBkM5+hca27fsNkUnNVaobncnLht/rCB2o/9Cw=**                                                                                           |
   +-------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | x-obs-server-side-encryption-customer-key-MD5   | Indicates the MD5 value of the key for encrypting objects when SSE-C is used. Its value is a Base64-encoded MD5 hash. The MD5 value is used to ensure data integrity during key transmission. |
   |                                                 |                                                                                                                                                                                               |
   |                                                 | Example: **x-obs-server-side-encryption-customer-key-MD5:4XvB3tbNTN+tIEVa0/fGaQ==**                                                                                                           |
   +-------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

APIs where the newly added headers apply:

-  :ref:`Uploading an Object - PUT <obs_04_0080>`
-  :ref:`Uploading an Object - POST <obs_04_0081>`
-  :ref:`Copying an Object <obs_04_0082>`: The newly added headers apply to the object copy.
-  :ref:`Querying Object Metadata <obs_04_0084>`
-  :ref:`Downloading an Object <obs_04_0083>`
-  :ref:`Initiating a Multipart Upload <obs_04_0098>`
-  :ref:`Uploading Parts <obs_04_0099>`
-  :ref:`Copying Parts <obs_04_0100>`: The newly added headers apply to target parts.

The following table lists three headers that are added for CopyObject and UploadPart-Copy operations to support source objects encrypted using SSE-C.

.. table:: **Table 2** Header fields for source objects encrypted by the SSE-C

   +-------------------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Element                                                     | Description                                                                                                                                                     |
   +=============================================================+=================================================================================================================================================================+
   | x-obs-copy-source-server-side-encryption-customer-algorithm | Indicates the algorithm for decrypting the source object when SSE-C is used.                                                                                    |
   |                                                             |                                                                                                                                                                 |
   |                                                             | Example: **x-obs-server-side-encryption-customer-algorithm: AES256**                                                                                            |
   +-------------------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | x-obs-copy-source-server-side-encryption-customer-key       | Indicates the key for decrypting the source object when SSE-C is used.                                                                                          |
   |                                                             |                                                                                                                                                                 |
   |                                                             | Example: **x-obs-copy-source-server-side-encryption-customer-algorithm: K7QkYpBkM5+hca27fsNkUnNVaobncnLht/rCB2o/9Cw=**                                          |
   +-------------------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | x-obs-copy-source-server-side-encryption-customer-key-MD5   | Indicates the MD5 value of the key for decrypting the source object when SSE-C is used. The MD5 value is used to ensure data integrity during key transmission. |
   |                                                             |                                                                                                                                                                 |
   |                                                             | Example: **x-obs-copy-source-server-side-encryption-customer-key:4XvB3tbNTN+tIEVa0/fGaQ==**                                                                     |
   +-------------------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------+

Sample Request: Uploading an Object Encrypted with SSE-C
--------------------------------------------------------

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

Sample Response: Uploading an Object Encrypted with SSE-C
---------------------------------------------------------

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

Sample Request: Copying an SSE-C Encrypted Object and Saving It as a KMS Encrypted Object
-----------------------------------------------------------------------------------------

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

Sample Response: Copying an SSE-C Encrypted Object and Saving It as a KMS Encrypted Object
------------------------------------------------------------------------------------------

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

Sample Request: Uploading an SSE-C Encrypted Object Using a Signed URL
----------------------------------------------------------------------

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

Sample Response: Uploading an SSE-C Encrypted Object Using a Signed URL
-----------------------------------------------------------------------

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
