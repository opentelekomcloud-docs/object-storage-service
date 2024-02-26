:original_name: en-us_topic_0125560339.html

.. _en-us_topic_0125560339:

Initiate Multipart Upload
=========================

You can use this operation to obtain a globally unique upload ID.

This upload ID is used to associate all parts in the specific multipart upload. You can specify this upload ID in each of your subsequent requests such as **Upload Part**, **Complete Multipart Upload**, and **List Parts**.

The key of the object for which a multipart upload is intended can be the same as an existing object. You can initiate one or more multipart uploads for one object.

An **Initiate Multipart Upload** request can contain multiple headers such as **x-amz-acl**, **x-amz-meta-\***, **Content-Type**, and **Content-Encoding**. The headers are recorded in the metadata of parts uploaded for the specific multipart upload.

This operation makes server-side encryption available.

WORM
----

If a bucket has WORM enabled, you can configure object-level retention policies when initiating multipart uploads. You can specify the **x-amz-object-lock-mode** and **x-amz-object-lock-retain-until-date** headers when you initiate a multipart upload to protect the object assembled. If you do not specify these two headers but have configured a default bucket-level WORM policy, this default policy automatically applies to the object newly assembled. You can also configure or update a WORM retention policy after the object is assembled, see section :ref:`Configuring WORM Retention for an Object <en-us_topic_0000001806154009>`.

Different from uploads with PUT and POST, a multipart upload only requires that the date specified in the **x-amz-object-lock-retain-until-date** header be no later than the initiation time, but does not have to be later than the completion time of the multipart upload. When the default bucket-level WORM policy is applied, the protection starts when the object parts are assembled and ends once the default bucket-level protection period expires. Before assembling the object parts uploaded, the multipart upload can be canceled and will not be affected by the WORM configuration.

Request Syntax
--------------

.. code-block:: text

   POST /ObjectName?uploads  HTTP/1.1
    User-Agent: agent
    Host: bucketname.obs.example.com
    Accept: */*
    Date: date
    Authorization: signatureValue

Request Parameters
------------------

This request uses a parameter to specify a multipart upload. :ref:`Table 1 <en-us_topic_0125560339__table13291134>` describes the parameters.

.. _en-us_topic_0125560339__table13291134:

.. table:: **Table 1** Request parameter

   +-----------------------+-----------------------------------------------------------+-----------------------+
   | Parameter             | Description                                               | Remarks               |
   +=======================+===========================================================+=======================+
   | uploads               | Indicates the ID of the multipart upload to be initiated. | Mandatory             |
   |                       |                                                           |                       |
   |                       | Type: String                                              |                       |
   +-----------------------+-----------------------------------------------------------+-----------------------+

Request Headers
---------------

This request uses common headers. For details about common request headers, see section :ref:`Common Request Headers <en-us_topic_0125560462>`.

This request also uses one optional header, as described in :ref:`Table 2 <en-us_topic_0125560339__table46028401>`.

.. _en-us_topic_0125560339__table46028401:

.. table:: **Table 2** Request headers

   +-------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+----------------------------------------------------------------------------------+
   | Header                                          | Description                                                                                                                                                                                                                     | Remarks                                                                          |
   +=================================================+=================================================================================================================================================================================================================================+==================================================================================+
   | x-amz-storage-class                             | When creating an object, you can add this header in the request to set the storage class of the object. If you do not add this header, the object will use the default storage class of the bucket.                             | Optional                                                                         |
   |                                                 |                                                                                                                                                                                                                                 |                                                                                  |
   |                                                 | Type: String                                                                                                                                                                                                                    |                                                                                  |
   |                                                 |                                                                                                                                                                                                                                 |                                                                                  |
   |                                                 | Note: The storage class can be **STANDARD** (OBS Standard), **STANDARD_IA** (OBS Warm), or **GLACIER** (OBS Cold). Note that the three storage class values are case-sensitive.                                                 |                                                                                  |
   |                                                 |                                                                                                                                                                                                                                 |                                                                                  |
   |                                                 | Example: x-amz-storage-class: STANDARD                                                                                                                                                                                          |                                                                                  |
   +-------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+----------------------------------------------------------------------------------+
   | x-amz-website-redirect-location                 | If a bucket is configured as a website, redirects requests for this object to another object in the same bucket or to an external URL. OBS stores the value of this header in the object metadata.                              | Optional                                                                         |
   |                                                 |                                                                                                                                                                                                                                 |                                                                                  |
   |                                                 | Type: String                                                                                                                                                                                                                    |                                                                                  |
   |                                                 |                                                                                                                                                                                                                                 |                                                                                  |
   |                                                 | Default: None                                                                                                                                                                                                                   |                                                                                  |
   |                                                 |                                                                                                                                                                                                                                 |                                                                                  |
   |                                                 | Constraint: The value must be prefixed by a slash (/), **http://**, or **https://**. The length of the value cannot exceed 2 K.                                                                                                 |                                                                                  |
   +-------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+----------------------------------------------------------------------------------+
   | x-amz-server-side-encryption                    | Indicates that SSE-KMS is used.                                                                                                                                                                                                 | No. This header is mandatory when SSE-KMS is used.                               |
   |                                                 |                                                                                                                                                                                                                                 |                                                                                  |
   |                                                 | Type: string                                                                                                                                                                                                                    |                                                                                  |
   |                                                 |                                                                                                                                                                                                                                 |                                                                                  |
   |                                                 | Example: x-amz-server-side-encryption:aws:kms                                                                                                                                                                                   |                                                                                  |
   +-------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+----------------------------------------------------------------------------------+
   | x-amz-server-side-encryption-aws-kms-key-id     | Indicates the master key ID. This header is used in SSE-KMS mode. If the customer does not provide the master key, the default master key will be used.                                                                         | No                                                                               |
   |                                                 |                                                                                                                                                                                                                                 |                                                                                  |
   |                                                 | Type: string                                                                                                                                                                                                                    |                                                                                  |
   |                                                 |                                                                                                                                                                                                                                 |                                                                                  |
   |                                                 | Example: x-amz-server-side-encryption-aws-kms-key-id:arn:aws:kms:sichuan:domainiddomainiddomainiddoma0001:key/4f1cd4de-ab64-4807-920a-47fc42e7f0d0                                                                              |                                                                                  |
   +-------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+----------------------------------------------------------------------------------+
   | x-amz-server-side-encryption-customer-algorithm | Indicates an encryption algorithm. The header is used in SSE-C mode.                                                                                                                                                            | No. This header is mandatory when SSE-C is used.                                 |
   |                                                 |                                                                                                                                                                                                                                 |                                                                                  |
   |                                                 | Type: string                                                                                                                                                                                                                    |                                                                                  |
   |                                                 |                                                                                                                                                                                                                                 |                                                                                  |
   |                                                 | Example: x-amz-server-side-encryption-customer-algorithm:AES256                                                                                                                                                                 |                                                                                  |
   |                                                 |                                                                                                                                                                                                                                 |                                                                                  |
   |                                                 | Constraints: This header must be used together with **x-amz-server-side-encryption-customer-key** and **x-amz-server-side-encryption-customer-key-MD5**.                                                                        |                                                                                  |
   +-------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+----------------------------------------------------------------------------------+
   | x-amz-server-side-encryption-customer-key       | Indicates a key used to encrypt objects. The header is used in SSE-C mode.                                                                                                                                                      | No. This header is mandatory when SSE-C is used.                                 |
   |                                                 |                                                                                                                                                                                                                                 |                                                                                  |
   |                                                 | Type: string                                                                                                                                                                                                                    |                                                                                  |
   |                                                 |                                                                                                                                                                                                                                 |                                                                                  |
   |                                                 | Example: x-amz-server-side-encryption-customer-key:K7QkYpBkM5+hcs27fsNkUnNVaobncnLht/rCB2o/9Cw=                                                                                                                                 |                                                                                  |
   |                                                 |                                                                                                                                                                                                                                 |                                                                                  |
   |                                                 | Constraints: This header is a base64-encoded 256-bit or 512-bit key and must be used together with **x-amz-server-side-encryption-customer-algorithm** and **x-amz-server-side-encryption-customer-key-MD5**.                   |                                                                                  |
   +-------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+----------------------------------------------------------------------------------+
   | x-amz-server-side-encryption-customer-key-MD5   | Indicates the MD5 value of a key used to encrypt objects. The header is used in SSE-C mode. The MD5 value is used to check whether any error occurs during the transmission of the key.                                         | No. This header is mandatory when SSE-C is used.                                 |
   |                                                 |                                                                                                                                                                                                                                 |                                                                                  |
   |                                                 | Type: string                                                                                                                                                                                                                    |                                                                                  |
   |                                                 |                                                                                                                                                                                                                                 |                                                                                  |
   |                                                 | Example: x-amz-server-side-encryption-customer-key-MD5:4XvB3tbNTN+tIEVa0/fGaQ==                                                                                                                                                 |                                                                                  |
   |                                                 |                                                                                                                                                                                                                                 |                                                                                  |
   |                                                 | Constraints: This header is a base64-encoded 128-bit MD5 value and must be used together with **x-amz-server-side-encryption-customer-algorithm** and **x-amz-server-side-encryption-customer-key**.                            |                                                                                  |
   +-------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+----------------------------------------------------------------------------------+
   | x-amz-security-token                            | Header field used to identify the request of a federated user. When the federal authentication function is enabled, users sending such requests are identified as federated users.                                              | Optional. This parameter must be carried in the request sent by federated users. |
   |                                                 |                                                                                                                                                                                                                                 |                                                                                  |
   |                                                 | Type: string                                                                                                                                                                                                                    |                                                                                  |
   +-------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+----------------------------------------------------------------------------------+
   | x-amz-object-lock-mode                          | WORM mode that will be applied to the object. Currently, only **COMPLIANCE** is supported. This header must be used together with **x-amz-object-lock-retain-until-date**.                                                      | No, but required when **x-amz-object-lock-retain-until-date** is present.        |
   |                                                 |                                                                                                                                                                                                                                 |                                                                                  |
   |                                                 | Type: string                                                                                                                                                                                                                    |                                                                                  |
   |                                                 |                                                                                                                                                                                                                                 |                                                                                  |
   |                                                 | Example: **x-amz-object-lock-mode:COMPLIANCE**                                                                                                                                                                                  |                                                                                  |
   +-------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+----------------------------------------------------------------------------------+
   | x-amz-object-lock-retain-until-date             | Indicates the expiration time of the Object Lock retention. The value must be a UTC time that complies with ISO 8601, for example, **2015-07-01T04:11:15Z**. This header must be used together with **x-amz-object-lock-mode**. | No, but required when **x-amz-object-lock-mode** is present.                     |
   |                                                 |                                                                                                                                                                                                                                 |                                                                                  |
   |                                                 | Type: string                                                                                                                                                                                                                    |                                                                                  |
   |                                                 |                                                                                                                                                                                                                                 |                                                                                  |
   |                                                 | Example: **x-amz-object-lock-retain-until-date:2015-07-01T04:11:15Z**                                                                                                                                                           |                                                                                  |
   +-------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+----------------------------------------------------------------------------------+

For details about common request headers, see section :ref:`Common Request Headers <en-us_topic_0125560462>`.

Request Elements
----------------

This request involves no elements.

Response Syntax
---------------

.. code-block::

   HTTP/1.1 status_code
    Server: server
    x-amz-id-2: id
    x-amz-request-id: request id
    x-reserved: amazon, aws and amazon web services are trademarks or registered trademarks of Amazon Technologies, Inc
    Content-Type: type
    Content-Length: length
    Date: date

    <?xml version="1.0" encoding="UTF-8" standalone="yes"?>
    <InitiateMultipartUploadResult xmlns="http://obs.example.com/doc/2015-06-30/">
    <Bucket>BucketName</Bucket>
    <Key>ObjectName</Key>
    <UploadId>uploadID</UploadId>
    </InitiateMultipartUploadResult>

Response Headers
----------------

This response uses common headers. For details about common response headers, see section :ref:`Common Response Headers <en-us_topic_0125560484>`.

.. table:: **Table 3** Response Headers

   +-------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------+
   | Header                                          | Description                                                                                                                                        |
   +=================================================+====================================================================================================================================================+
   | x-amz-server-side-encryption                    | This header is included in a response if SSE-KMS is used.                                                                                          |
   |                                                 |                                                                                                                                                    |
   |                                                 | Type: string                                                                                                                                       |
   |                                                 |                                                                                                                                                    |
   |                                                 | Example: x-amz-server-side-encryption:aws:kms                                                                                                      |
   +-------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------+
   | x-amz-server-side-encryption-aws-kms-key-id     | Indicates the master key ID. This header is included in a response if SSE-KMS is used.                                                             |
   |                                                 |                                                                                                                                                    |
   |                                                 | Example: x-amz-server-side-encryption-aws-kms-key-id:arn:aws:kms:sichuan:domainiddomainiddomainiddoma0001:key/4f1cd4de-ab64-4807-920a-47fc42e7f0d0 |
   +-------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------+
   | x-amz-server-side-encryption-customer-algorithm | Indicates an encryption algorithm. This header is included in a response if SSE-C is used.                                                         |
   |                                                 |                                                                                                                                                    |
   |                                                 | Type: string                                                                                                                                       |
   |                                                 |                                                                                                                                                    |
   |                                                 | Example: x-amz-server-side-encryption-customer-algorithm:AES256                                                                                    |
   +-------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------+
   | x-amz-server-side-encryption-customer-key-MD5   | Indicates the MD5 value of a key used to encrypt objects. This header is included in a response if SSE-C is used.                                  |
   |                                                 |                                                                                                                                                    |
   |                                                 | Type: string                                                                                                                                       |
   |                                                 |                                                                                                                                                    |
   |                                                 | Example: x-amz-server-side-encryption-customer-key-MD5:4XvB3tbNTN+tIEVa0/fGaQ==                                                                    |
   +-------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------+

Response Elements
-----------------

This response contains elements to indicate the upload ID and the key (name) of the object (bucket) for which the multipart upload was initiated. The returned information is used in the subsequent **Upload Part** and **Complete Multipart Upload** operations. :ref:`Table 4 <en-us_topic_0125560339__table6651816>` describes the elements.

.. _en-us_topic_0125560339__table6651816:

.. table:: **Table 4** Response elements

   +-----------------------------------+--------------------------------------------------------------------------------------------------------------------+
   | Element                           | Description                                                                                                        |
   +===================================+====================================================================================================================+
   | InitiateMultipartUploadResult     | Indicates the container for the response.                                                                          |
   |                                   |                                                                                                                    |
   |                                   | Type: XML                                                                                                          |
   +-----------------------------------+--------------------------------------------------------------------------------------------------------------------+
   | Bucket                            | Indicates the name of the bucket for which the multipart upload was initiated.                                     |
   |                                   |                                                                                                                    |
   |                                   | Type: String                                                                                                       |
   +-----------------------------------+--------------------------------------------------------------------------------------------------------------------+
   | Key                               | Indicates the key of the object for which the multipart upload was initiated.                                      |
   |                                   |                                                                                                                    |
   |                                   | Type: String                                                                                                       |
   +-----------------------------------+--------------------------------------------------------------------------------------------------------------------+
   | UploadId                          | Indicates the ID for the initiated multipart upload. This ID is used for the subsequent **Upload Part** operation. |
   |                                   |                                                                                                                    |
   |                                   | Type: String                                                                                                       |
   +-----------------------------------+--------------------------------------------------------------------------------------------------------------------+

Error Responses
---------------

-  If an AK or signature is invalid, OBS returns status code **403 Forbidden** and error code **AccessDenied**.
-  If the requested bucket does not exist, OBS returns status code **404 Not Found** and error code **NoSuchBucket**.
-  If the requester does not have **WRITE** permission for the requested bucket, OBS returns status code **403 Forbidden** and error code **AccessDenied**.

For details about other error responses, see :ref:`Table 1 <en-us_topic_0125560440__table30733758>`.

Sample Request
--------------

.. code-block:: text

   POST /objectkey?uploads  HTTP/1.1
    User-Agent: Jakarta Commons-HttpClient/3.1
    Host: bucketname.obs.example.com
    Accept: */*
    Date: Mon, 1 Nov 2010 20:34:56 GMT
    Authorization: AWS AKIAIOSFODNN7EXAMPLE:VGhpcyBtZXNzYWdlIHNpZ25lZGGieSRlbHZpbmc=

Sample Response
---------------

.. code-block::

   HTTP/1.1 200 OK
    Server: OBS
    x-amz-id-2: Weag1LuByRx9e6j5Onimru9pO4ZVKnJ2Qz7/C1NPcfTWAtRPfTaOFg==
    x-amz-request-id: 996c76696e6727732072657175657374
    x-reserved: amazon, aws and amazon web services are trademarks or registered trademarks of Amazon Technologies, Inc
    Date: Mon, 1 Nov 2010 20:34:56 GMT
    Content-Type: application/xml
    Content-Length: 146

    <?xml version="1.0" encoding="UTF-8" standalone="yes"?>
    <InitiateMultipartUploadResult xmlns="http://obs.example.com/doc/2015-06-30/">
    <Bucket>bucket01</Bucket>
    <Key>objectkey</Key>
    <UploadId>DCD2FC98B4F70000013DF578ACA318E7</UploadId>
    </InitiateMultipartUploadResult>
