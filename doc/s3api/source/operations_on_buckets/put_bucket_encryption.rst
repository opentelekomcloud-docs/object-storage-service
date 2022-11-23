:original_name: en-us_topic_0000001080838596.html

.. _en-us_topic_0000001080838596:

PUT Bucket Encryption
=====================

OBS uses the PUT method to create or update the default server-side encryption for a bucket.

After encryption is enabled for a bucket, objects uploaded to the bucket are encrypted with the encryption configuration the bucket. Currently, it only supports the server-side encryption using keys hosted by KMS (SSE-KMS). For details about SSE-KMS, see :ref:`SSE-KMS <en-us_topic_0125560445>`.

To perform this operation, you must have the **s3:PutEncryptionConfiguration** permission. By default, the bucket owner has this permission and can assign this permission to other users.

Request Syntax
--------------

.. code-block:: text

   PUT /?encryption  HTTP/1.1
   User-Agent: curl/7.29.0
   Host: bucketname.obs.region.example.com
   Accept: */*
   Date: date
   Authorization: authorization string
   Content-Length: length

   <ServerSideEncryptionConfiguration>
       <Rule>
           <ApplyServerSideEncryptionByDefault>
               <SSEAlgorithm>aws:kms</SSEAlgorithm>
               <KMSMasterKeyID>kmskeyid-value</KMSMasterKeyID>
           </ApplyServerSideEncryptionByDefault>
       </Rule>
   </ServerSideEncryptionConfiguration>

Request Parameters
------------------

This request contains no parameter.

Request Headers
---------------

This request uses common headers. For details about common request headers, see the section :ref:`Common Request Headers <en-us_topic_0125560462>`.

Request Elements
----------------

In this request, you need to carry the bucket encryption configuration in the request body. The bucket encryption configuration information is uploaded in the XML format. :ref:`Table 1 <en-us_topic_0000001080838596__table1181123018399>` lists the configuration elements.

.. _en-us_topic_0000001080838596__table1181123018399:

.. table:: **Table 1** Configuration elements of bucket encryption

   +------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
   | Header                             | Description                                                                                                                                                                                                  | Mandatory             |
   +====================================+==============================================================================================================================================================================================================+=======================+
   | ServerSideEncryptionConfiguration  | Root element of the default encryption configuration of a bucket.                                                                                                                                            | Yes                   |
   |                                    |                                                                                                                                                                                                              |                       |
   |                                    | Type: element                                                                                                                                                                                                |                       |
   |                                    |                                                                                                                                                                                                              |                       |
   |                                    | Ancestor: none                                                                                                                                                                                               |                       |
   |                                    |                                                                                                                                                                                                              |                       |
   |                                    | Children: Rule                                                                                                                                                                                               |                       |
   +------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
   | Rule                               | Sub-element of the default encryption configuration of a bucket.                                                                                                                                             | Yes                   |
   |                                    |                                                                                                                                                                                                              |                       |
   |                                    | Type: element                                                                                                                                                                                                |                       |
   |                                    |                                                                                                                                                                                                              |                       |
   |                                    | Root element: ServerSideEncryptionConfiguration                                                                                                                                                              |                       |
   |                                    |                                                                                                                                                                                                              |                       |
   |                                    | Sub-element: ApplyServerSideEncryptionByDefault                                                                                                                                                              |                       |
   +------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
   | ApplyServerSideEncryptionByDefault | Sub-element of the default encryption configuration of a bucket.                                                                                                                                             | Yes                   |
   |                                    |                                                                                                                                                                                                              |                       |
   |                                    | Type: element                                                                                                                                                                                                |                       |
   |                                    |                                                                                                                                                                                                              |                       |
   |                                    | Ancestor: Rule                                                                                                                                                                                               |                       |
   |                                    |                                                                                                                                                                                                              |                       |
   |                                    | Children: SSEAlgorithm, KMSMasterKeyID                                                                                                                                                                       |                       |
   +------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
   | SSEAlgorithm                       | Server-side encryption algorithm used for the default encryption configuration of a bucket.                                                                                                                  | Yes                   |
   |                                    |                                                                                                                                                                                                              |                       |
   |                                    | Type: string                                                                                                                                                                                                 |                       |
   |                                    |                                                                                                                                                                                                              |                       |
   |                                    | Valid values: **aws:kms**                                                                                                                                                                                    |                       |
   |                                    |                                                                                                                                                                                                              |                       |
   |                                    | Root element: ApplyServerSideEncryptionByDefault                                                                                                                                                             |                       |
   +------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
   | KMSMasterKeyID                     | Customer master key (CMK) used in SSE-KMS encryption mode. If you do not specify this header, the default master key will be used.                                                                           | No                    |
   |                                    |                                                                                                                                                                                                              |                       |
   |                                    | Type: string                                                                                                                                                                                                 |                       |
   |                                    |                                                                                                                                                                                                              |                       |
   |                                    | Valid value formats are as follows:                                                                                                                                                                          |                       |
   |                                    |                                                                                                                                                                                                              |                       |
   |                                    | #. *regionID:domainID (account ID)*:key/*key_id*                                                                                                                                                             |                       |
   |                                    | #. key_id                                                                                                                                                                                                    |                       |
   |                                    |                                                                                                                                                                                                              |                       |
   |                                    | **regionID** is the ID of the region to which the key belongs. **domainID** is the account ID of the tenant to which the key belongs. **key_id** is the key ID created with the Key Management Service(KMS). |                       |
   |                                    |                                                                                                                                                                                                              |                       |
   |                                    | Root element: ApplyServerSideEncryptionByDefault                                                                                                                                                             |                       |
   +------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+

Response Syntax
---------------

::

   HTTP/1.1 status_code
   Date: date
   Content-Length: length

Response Headers
----------------

This response uses common headers. For details about common response headers, see the section :ref:`Common Response Headers <en-us_topic_0125560484>`.

Response Elements
-----------------

This response involves no elements.

Error Responses
---------------

No special error responses are returned. For details about error responses, see :ref:`Table 1 <en-us_topic_0125560440__table30733758>`.

Sample Request
--------------

.. code-block:: text

   PUT /?encryption HTTP/1.1
   User-Agent: curl/7.29.0
   Host: examplebucket.obs.region.example.com
   Accept: */*
   Date:  Thu, 21 Feb 2019 03:05:34 GMT
   Authorization: OBS H4IPJX0TQTHTHEBQQCEC:DpSAlmLX/BTdjxU5HOEwflhM0WI=
   Content-Length: 778

   <?xml version="1.0" encoding="UTF-8" standalone="yes"?>
   <ServerSideEncryptionConfiguration xmlns="http://obs.region.example.com/doc/2015-06-30/">
       <Rule>
           <ApplyServerSideEncryptionByDefault>
               <SSEAlgorithm>aws:kms</SSEAlgorithm>
               <KMSMasterKeyID>4f1cd4de-ab64-4807-920a-47fc42e7f0d0</KMSMasterKeyID>
           </ApplyServerSideEncryptionByDefault>
       </Rule>
   </ServerSideEncryptionConfiguration>

Sample Response
---------------

::

   HTTP/1.1 200 OK
   Server: OBS
   x-amz-request-id: BF26000001643670AC06E7B9A7767921
   x-amz-id-2: 32AAAQAAEAABSAAgAAEAABAAAQAAEAABCSvK6z8HV6nrJh49gsB5vqzpgtohkiFm
   Date: Thu, 21 Feb 2019 03:05:34 GMT
   Content-Length: 0
