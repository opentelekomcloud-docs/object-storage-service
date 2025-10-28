:original_name: obs_04_0173.html

.. _obs_04_0173:

SSE-OBS
=======

Functions
---------

With SSE-OBS, OBS uses the keys provided by itself for server-side encryption. Unlike SSE-KMS where KMS manages keys, in SSE-OBS, OBS manages keys.

Newly Added Headers
-------------------

Use the headers listed in :ref:`Table 1 <obs_04_0173__table9548129165313>` to implement SSE-OBS.

You can also configure the default encryption for a bucket to encrypt objects you upload to the bucket. After the default encryption is configured for a bucket, if upload requests for that bucket do not contain encryption headers, the default encryption applies to the uploaded objects. For more information about configuring bucket encryption, see :ref:`Configuring Bucket Encryption <obs_04_0062>`.

.. _obs_04_0173__table9548129165313:

.. table:: **Table 1** Header used in SSE-OBS

   +-----------------------------------+--------------------------------------------------------+
   | Header                            | Description                                            |
   +===================================+========================================================+
   | x-obs-server-side-encryption      | Indicates that SSE-OBS is used for encrypting objects. |
   |                                   |                                                        |
   |                                   | Type: string                                           |
   |                                   |                                                        |
   |                                   | Example: **x-obs-server-side-encryption:AES256**       |
   +-----------------------------------+--------------------------------------------------------+

APIs Where SSE-OBS Headers Apply
--------------------------------

You can configure headers about SSE-OBS in the APIs below:

-  :ref:`Uploading Objects - PUT <obs_04_0080>`
-  :ref:`Uploading Objects - POST <obs_04_0081>` (**x-obs-server-side-encryption** should be put in the form, instead of the header.)
-  :ref:`Copying Objects <obs_04_0082>` (The newly added headers apply to object copies.)
-  :ref:`Initiating a Multipart Upload <obs_04_0098>`

You can configure a bucket policy to restrict the request headers for a specified bucket. For example, if you require that object upload requests do not contain header **x-obs-server-side-encryption:"AES256"**, you can use the following bucket policy:

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
                       "x-obs-server-side-encryption": "AES256"
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
   x-obs-server-side-encryption:AES256
   Content-Length: 5242
   Expect: 100-continue

   [5242 Byte object contents]

Sample Response: Using the Default Key to Encrypt an Object
-----------------------------------------------------------

.. code-block::

   HTTP/1.1 200 OK
   Server: OBS
   x-obs-request-id: 8DF400000163D45AA81D038B6AE4C482
   ETag: "d8bffdfbab5345d91ac05141789d2477"
   x-obs-server-side-encryption: AES256
   x-obs-id-2: 32AAAUJAIAABAAAQAAEAABAAAQAAEAABCTv7cHmAnGfBAGXUHeibUsiETTNqlCqC
   Date: Wed, 06 Jun 2018 09:08:21 GMT
   Content-Length: 0

Sample Request: Copying an Object as an Encrypted Object
--------------------------------------------------------

.. code-block:: text

   PUT /destobject HTTP/1.1
   User-Agent: curl/7.29.0
   Host: examplebucket.obs.region.example.com
   x-obs-server-side-encryption:AES256
   Accept: */*
   Date: Wed, 06 Jun 2018 09:10:29 GMT
   Authorization: OBS H4IPJX0TQTHTHEBQQCEC:SH3uTrElaGWarVI1uTq325kTVCI=
   x-obs-copy-source: /bucket/srcobject1

Sample Response: Copying an Object as an Encrypted Object
---------------------------------------------------------

.. code-block::

   HTTP/1.1 200 OK
   Server: OBS
   x-obs-request-id: BB78000001648480AF3900CED7F15155
   ETag: "d8bffdfbab5345d91ac05141789d2477"
   x-obs-server-side-encryption: AES256
   x-obs-id-2: oRAXhgwdaLc9wKVHqTLSmQB7I35D+32AAAUJAIAABAAAQAAEAABAAAQAAEAABCS
   Date: Wed, 06 Jun 2018 09:10:29 GMT
   Content-Length: 0

Sample Request: Uploading an Encrypted Object Using a Signed URL
----------------------------------------------------------------

.. code-block:: text

   PUT /destobject?AccessKeyId=UI3SN1SRUQE14OYBKTZB&Expires=1534152518&x-obs-server-side-encryption=AES256&Signature=chvmG7%2FDA%2FDCQmTRJu3xngldJpg%3D HTTP/1.1
   User-Agent: curl/7.29.0
   Host: examplebucket.obs.region.example.com
   Accept: */*
   Date: Wed, 06 Jun 2018 09:10:29 GMT

Sample Response: Uploading an Encrypted Object Using a Signed URL
-----------------------------------------------------------------

.. code-block::

   HTTP/1.1 200 OK
   Server: OBS
   x-obs-request-id: BB78000001648480AF3900CED7F15155
   ETag: "d8bffdfbab5345d91ac05141789d2477"
   x-obs-server-side-encryption: AES256
   x-obs-id-2: oRAXhgwdaLc9wKVHqTLSmQB7I35D+32AAAUJAIAABAAAQAAEAABAAAQAAEAABCS
   Date: Wed, 06 Jun 2018 09:10:29 GMT
   Content-Length: 0
