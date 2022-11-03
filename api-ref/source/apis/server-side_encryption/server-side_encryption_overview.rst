:original_name: obs_04_0105.html

.. _obs_04_0105:

Server-Side Encryption Overview
===============================

Users can upload and download objects in common mode or using server-side encryption.

OBS supports server-side encryption.

Users can implement this function based on the key type to meet site requirements. Two server-side encryption modes are supported: KMS server-side encryption (SSE-KMS) and server-side encryption (SSE-C) provided by the customer. Both the two modes use the industry-standard AES256 encryption algorithm.

In the SSE-KMS mode, OBS uses the keys provided by KMS for server-side encryption.

In the SSE-C mode, OBS uses the keys and MD5 values provided by customers for server-side encryption.

When server-side encryption is used, the returned ETag value is not the MD5 value of the object. OBS will verify the MD5 value of an uploaded object when the upload request carries the **Content-MD5** header field, no matter whether server-side encryption is used or not.
