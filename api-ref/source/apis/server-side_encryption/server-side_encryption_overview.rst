:original_name: obs_04_0105.html

.. _obs_04_0105:

Server-Side Encryption Overview
===============================

You can configure server-side encryption for objects, so that they will be encrypted or decrypted when you upload them to or download them from a bucket.

The encryption and decryption happen on the server side.

The encryption methods provided include SSE-KMS and SSE-C. All of them use the AES-256 algorithm.

With SSE-KMS, OBS uses the keys provided by KMS for server-side encryption. You can create custom keys on KMS to encrypt your objects.

With SSE-C, OBS uses the keys and MD5 values provided by customers for server-side encryption.

When server-side encryption is used, the returned ETag value is not the object's MD5 value.
