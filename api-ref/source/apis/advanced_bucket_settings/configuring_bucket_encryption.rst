:original_name: obs_04_0062.html

.. _obs_04_0062:

Configuring Bucket Encryption
=============================

Functions
---------

OBS uses the PUT method to create or update the default server-side encryption for a bucket.

After encryption is enabled for a bucket, objects uploaded to the bucket are encrypted with the encryption configuration the bucket. Currently, it only supports the server-side encryption using keys hosted by KMS (SSE-KMS). For details about SSE-KMS, see :ref:`Server-Side Encryption (SSE-KMS) <obs_04_0106>`.

To perform this operation, you must have the permission to configure encryption for the bucket. By default, the bucket owner has this permission and can assign this permission to other users.

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
               <SSEAlgorithm>kms</SSEAlgorithm>
               <KMSMasterKeyID>kmskeyid-value</KMSMasterKeyID>
               <ProjectID>projectid</ProjectID>
           </ApplyServerSideEncryptionByDefault>
       </Rule>
   </ServerSideEncryptionConfiguration>

Request parameters
------------------

This request contains no message parameters.

Request Headers
---------------

This request uses common headers. For details, see :ref:`Table 3 <obs_04_0007__table25197309>`.

Request Elements
----------------

In this request, you need to carry the bucket encryption configuration in the request body. The bucket encryption configuration information is uploaded in the XML format. :ref:`Table 1 <obs_04_0062__table1181123018399>` lists the configuration elements.

.. _obs_04_0062__table1181123018399:

.. table:: **Table 1** Configuration elements of bucket encryption

   +------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
   | Header                             | Description                                                                                                                                       | Mandatory             |
   +====================================+===================================================================================================================================================+=======================+
   | ServerSideEncryptionConfiguration  | Root element of the default encryption configuration of a bucket.                                                                                 | Yes                   |
   |                                    |                                                                                                                                                   |                       |
   |                                    | Type: container                                                                                                                                   |                       |
   |                                    |                                                                                                                                                   |                       |
   |                                    | Ancestor: none                                                                                                                                    |                       |
   |                                    |                                                                                                                                                   |                       |
   |                                    | Children: Rule                                                                                                                                    |                       |
   +------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
   | Rule                               | Sub-element of the default encryption configuration of a bucket.                                                                                  | Yes                   |
   |                                    |                                                                                                                                                   |                       |
   |                                    | Type: container                                                                                                                                   |                       |
   |                                    |                                                                                                                                                   |                       |
   |                                    | Ancestor: ServerSideEncryptionConfiguration                                                                                                       |                       |
   |                                    |                                                                                                                                                   |                       |
   |                                    | Children: ApplyServerSideEncryptionByDefault                                                                                                      |                       |
   +------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
   | ApplyServerSideEncryptionByDefault | Sub-element of the default encryption configuration of a bucket.                                                                                  | Yes                   |
   |                                    |                                                                                                                                                   |                       |
   |                                    | Type: container                                                                                                                                   |                       |
   |                                    |                                                                                                                                                   |                       |
   |                                    | Ancestor: Rule                                                                                                                                    |                       |
   |                                    |                                                                                                                                                   |                       |
   |                                    | Children: SSEAlgorithm, KMSMasterKeyID                                                                                                            |                       |
   +------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
   | SSEAlgorithm                       | Server-side encryption algorithm used for the default encryption configuration of a bucket.                                                       | Yes                   |
   |                                    |                                                                                                                                                   |                       |
   |                                    | Type: string                                                                                                                                      |                       |
   |                                    |                                                                                                                                                   |                       |
   |                                    | Value options: **kms**                                                                                                                            |                       |
   |                                    |                                                                                                                                                   |                       |
   |                                    | Ancestor: ApplyServerSideEncryptionByDefault                                                                                                      |                       |
   +------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
   | KMSMasterKeyID                     | Customer master key (CMK) used in SSE-KMS encryption mode. If you do not specify this header, the default master key will be used.                | No                    |
   |                                    |                                                                                                                                                   |                       |
   |                                    | Type: string                                                                                                                                      |                       |
   |                                    |                                                                                                                                                   |                       |
   |                                    | Valid value formats are as follows:                                                                                                               |                       |
   |                                    |                                                                                                                                                   |                       |
   |                                    | #. *regionID:domainID (account ID)*\ **:key/**\ *key_id*                                                                                          |                       |
   |                                    | #. *key_id*                                                                                                                                       |                       |
   |                                    |                                                                                                                                                   |                       |
   |                                    | In the preceding formats:                                                                                                                         |                       |
   |                                    |                                                                                                                                                   |                       |
   |                                    | -  *regionID* indicates the ID of the region where the key resides.                                                                               |                       |
   |                                    | -  *domainID* indicates the ID of the domain to which the key belongs. For details, see :ref:`Obtaining the Domain ID and User ID <obs_04_0117>`. |                       |
   |                                    | -  *key_id* indicates the ID of the key created inKMS.                                                                                            |                       |
   |                                    |                                                                                                                                                   |                       |
   |                                    | Ancestor: ApplyServerSideEncryptionByDefault                                                                                                      |                       |
   +------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
   | ProjectID                          | ID of the project to which the KMS master key belongs in the SSE-KMS mode.                                                                        | No                    |
   |                                    |                                                                                                                                                   |                       |
   |                                    | Type: string                                                                                                                                      |                       |
   |                                    |                                                                                                                                                   |                       |
   |                                    | Value options:                                                                                                                                    |                       |
   |                                    |                                                                                                                                                   |                       |
   |                                    | #. Project ID that matches **KMSMasterKeyID**.                                                                                                    |                       |
   |                                    | #. If **KMSMasterKeyID** is not specified, do not set the project ID.                                                                             |                       |
   |                                    |                                                                                                                                                   |                       |
   |                                    | Ancestor: **ApplyServerSideEncryptionByDefault**                                                                                                  |                       |
   +------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+

Response Syntax
---------------

::

   HTTP/1.1 status_code
   Date: date
   Content-Length: length

Response Headers
----------------

The response to the request uses common headers. For details, see :ref:`Table 1 <obs_04_0013__d0e686>`.

Response Elements
-----------------

This response contains no element.

Error Responses
---------------

No special error responses are returned. For details about error responses, see :ref:`Table 2 <obs_04_0115__d0e843>`.

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
               <SSEAlgorithm>kms</SSEAlgorithm>
               <KMSMasterKeyID>4f1cd4de-ab64-4807-920a-47fc42e7f0d0</KMSMasterKeyID>
           </ApplyServerSideEncryptionByDefault>
       </Rule>
   </ServerSideEncryptionConfiguration>

Sample Response
---------------

::

   HTTP/1.1 200 OK
   Server: OBS
   x-obs-request-id: BF26000001643670AC06E7B9A7767921
   x-obs-id-2: 32AAAQAAEAABSAAgAAEAABAAAQAAEAABCSvK6z8HV6nrJh49gsB5vqzpgtohkiFm
   Date: Thu, 21 Feb 2019 03:05:34 GMT
   Content-Length: 0
