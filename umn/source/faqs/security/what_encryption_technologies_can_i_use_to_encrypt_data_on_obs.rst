:original_name: obs_faq_0044.html

.. _obs_faq_0044:

What Encryption Technologies Can I Use to Encrypt Data on OBS?
==============================================================

Before uploading your data to OBS, you can encrypt the data to ensure security during transmission and storage. OBS support various encryption technologies used on clients.

OBS allows users to encrypt objects using server-side encryption so that the objects can be securely stored on OBS.

The objects to be uploaded can be encrypted using SSE-KMS. You need to create a key using KMS or use the default key provided by KMS. Then you can use the KMS key to perform server-side encryption when uploading objects on OBS.

After server-side encryption is enabled, objects to be uploaded will be encrypted and stored on the server. When downloading the encrypted objects, the encrypted data will be decrypted on the server and displayed in plaintext to users.

OBS provides SSE-KMS and SSE-C that can be configured by calling APIs. With SSE-C, OBS uses the customer-provided keys and their MD5 values for server-side encryption.
