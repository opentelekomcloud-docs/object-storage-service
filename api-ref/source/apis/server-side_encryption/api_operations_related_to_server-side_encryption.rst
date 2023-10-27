:original_name: obs_04_0108.html

.. _obs_04_0108:

API Operations Related to Server-Side Encryption
================================================

This section lists the operations related to server-side encryption and describes HTTP protocols applicable to the operations.

The following table describes the requirements on the transmission protocols used by the API operation related to server-side encryption.

.. table:: **Table 1** Requirements for the transmission protocol used by the operations related to the SSE-C

   ======================= =================
   Operation               Transfer Protocol
   ======================= =================
   PutObject               HTTPS
   PostObject              HTTPS
   InitiateMultipartUpload HTTPS
   HeadObject              HTTPS
   GetObject               HTTPS
   UploadPart              HTTPS
   CompleteMultipartUpload HTTP or HTTPS
   ======================= =================

.. table:: **Table 2** Requirements for the transfer protocol used by the operations related to the SSE-KMS

   ======================= =================
   Operation               Transfer Protocol
   ======================= =================
   PutObject               HTTPS
   PostObject              HTTPS
   InitiateMultipartUpload HTTPS
   HeadObject              HTTP or HTTPS
   GetObject               HTTPS
   UploadPart              HTTPS
   CompleteMultipartUpload HTTP or HTTPS
   ======================= =================

.. table:: **Table 3** Requirements for transfer protocol used by the CopyObject operation

   +--------------------------------+--------------------------------+-------------------+
   | Source Object                  | Target Object                  | Transfer Protocol |
   +================================+================================+===================+
   | Non-encrypted object           | Object encrypted using SSE-KMS | HTTPS             |
   +--------------------------------+--------------------------------+-------------------+
   | Object encrypted using SSE-KMS | Object encrypted using SSE-KMS | HTTPS             |
   +--------------------------------+--------------------------------+-------------------+
   | Object encrypted using SSE-C   | Object encrypted using SSE-KMS | HTTPS             |
   +--------------------------------+--------------------------------+-------------------+
   | Non-encrypted object           | Object encrypted using SSE-C   | HTTPS             |
   +--------------------------------+--------------------------------+-------------------+
   | Object encrypted using SSE-KMS | Object encrypted using SSE-C   | HTTPS             |
   +--------------------------------+--------------------------------+-------------------+
   | Object encrypted using SSE-C   | Object encrypted using SSE-C   | HTTPS             |
   +--------------------------------+--------------------------------+-------------------+
   | Non-encrypted object           | Non-encrypted object           | HTTP or HTTPS     |
   +--------------------------------+--------------------------------+-------------------+
   | Object encrypted using SSE-KMS | Non-encrypted object           | HTTP or HTTPS     |
   +--------------------------------+--------------------------------+-------------------+
   | Object encrypted using SSE-C   | Non-encrypted object           | HTTP or HTTPS     |
   +--------------------------------+--------------------------------+-------------------+

.. table:: **Table 4** Requirements for the transfer protocol used by the UploadPart-Copy operation

   +--------------------------------+------------------------------+-------------------+
   | Source Object                  | Target Part                  | Transfer Protocol |
   +================================+==============================+===================+
   | Non-encrypted object           | Part encrypted using SSE-KMS | HTTP or HTTPS     |
   +--------------------------------+------------------------------+-------------------+
   | Object encrypted using SSE-KMS | Part encrypted using SSE-KMS | HTTP or HTTPS     |
   +--------------------------------+------------------------------+-------------------+
   | Object encrypted using SSE-C   | Part encrypted using SSE-KMS | HTTP or HTTPS     |
   +--------------------------------+------------------------------+-------------------+
   | Non-encrypted object           | Part encrypted using SSE-C   | HTTPS             |
   +--------------------------------+------------------------------+-------------------+
   | Object encrypted using SSE-KMS | Part encrypted using SSE-C   | HTTPS             |
   +--------------------------------+------------------------------+-------------------+
   | Object encrypted using SSE-C   | Part encrypted using SSE-C   | HTTPS             |
   +--------------------------------+------------------------------+-------------------+
   | Non-encrypted object           | Non-encrypted part           | HTTP or HTTPS     |
   +--------------------------------+------------------------------+-------------------+
   | Object encrypted using SSE-KMS | Non-encrypted part           | HTTP or HTTPS     |
   +--------------------------------+------------------------------+-------------------+
   | Object encrypted using SSE-C   | Non-encrypted part           | HTTP or HTTPS     |
   +--------------------------------+------------------------------+-------------------+
