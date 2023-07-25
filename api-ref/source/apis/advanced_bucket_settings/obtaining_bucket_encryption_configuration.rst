:original_name: obs_04_0063.html

.. _obs_04_0063:

Obtaining Bucket Encryption Configuration
=========================================

Functions
---------

OBS uses the GET method to obtain the encryption configuration of a specified bucket.

To perform this operation, you must have the **GetEncryptionConfiguration** permission. By default, only the bucket owner can delete the tags of a bucket. The bucket owner can allow other users to perform this operation by setting a bucket policy or granting them the permission.

Request Syntax
--------------

.. code-block:: text

   GET /?encryption  HTTP/1.1
   User-Agent: curl/7.29.0
   Host: bucketname.obs.region.example.com
   Accept: */*
   Date: date
   Authorization: authorization string

Request parameters
------------------

This request contains no message parameters.

Request Headers
---------------

This request uses common headers. For details, see :ref:`Table 3 <obs_04_0007__table25197309>`.

Request Elements
----------------

This request involves no elements.

Response Syntax
---------------

::

   HTTP/1.1 status_code
   x-obs-request-id: request id
   x-obs-id-2: id
   Content-Type: application/xml
   Content-Length: length
   Date: date

   <?xml version="1.0" encoding="UTF-8" standalone="yes"?>
   <ServerSideEncryptionConfiguration xmlns="http://obs.region.example.com/doc/2015-06-30/">
       <Rule>
           <ApplyServerSideEncryptionByDefault>
               <SSEAlgorithm>kms</SSEAlgorithm>
               <KMSMasterKeyID>kmskeyid-value</KMSMasterKeyID>
               <ProjectID>projectid</ProjectID>
           </ApplyServerSideEncryptionByDefault>
       </Rule>
   </ServerSideEncryptionConfiguration>

Response Headers
----------------

The response to the request uses common headers. For details, see :ref:`Table 1 <obs_04_0013__d0e686>`.

Response Elements
-----------------

This response contains the following elements to detail bucket encryption configuration:

.. table:: **Table 1** Configuration elements of bucket encryption

   +------------------------------------+-------------------------------------------------------------------------------------+
   | Header                             | Description                                                                         |
   +====================================+=====================================================================================+
   | ServerSideEncryptionConfiguration  | Root element of the default encryption configuration of a bucket.                   |
   |                                    |                                                                                     |
   |                                    | Type: container                                                                     |
   |                                    |                                                                                     |
   |                                    | Ancestor: none                                                                      |
   |                                    |                                                                                     |
   |                                    | Children: Rule                                                                      |
   +------------------------------------+-------------------------------------------------------------------------------------+
   | Rule                               | Sub-element of the default encryption configuration of a bucket.                    |
   |                                    |                                                                                     |
   |                                    | Type: container                                                                     |
   |                                    |                                                                                     |
   |                                    | Ancestor: ServerSideEncryptionConfiguration                                         |
   |                                    |                                                                                     |
   |                                    | Children: ApplyServerSideEncryptionByDefault                                        |
   +------------------------------------+-------------------------------------------------------------------------------------+
   | ApplyServerSideEncryptionByDefault | Sub-element of the default encryption configuration of a bucket.                    |
   |                                    |                                                                                     |
   |                                    | Type: container                                                                     |
   |                                    |                                                                                     |
   |                                    | Ancestor: Rule                                                                      |
   |                                    |                                                                                     |
   |                                    | Children: SSEAlgorithm, KMSMasterKeyID                                              |
   +------------------------------------+-------------------------------------------------------------------------------------+
   | SSEAlgorithm                       | The server-side encryption algorithm used for encryption configuration of a bucket. |
   |                                    |                                                                                     |
   |                                    | Type: string                                                                        |
   |                                    |                                                                                     |
   |                                    | Value options: **kms**                                                              |
   |                                    |                                                                                     |
   |                                    | Ancestor: ApplyServerSideEncryptionByDefault                                        |
   +------------------------------------+-------------------------------------------------------------------------------------+
   | KMSMasterKeyID                     | ID of the customer master key (CMK) used for SSE-KMS.                               |
   |                                    |                                                                                     |
   |                                    | Type: string                                                                        |
   |                                    |                                                                                     |
   |                                    | Ancestor: ApplyServerSideEncryptionByDefault                                        |
   +------------------------------------+-------------------------------------------------------------------------------------+
   | ProjectID                          | ID of the project to which the KMS master key belongs in the SSE-KMS mode.          |
   |                                    |                                                                                     |
   |                                    | Type: string                                                                        |
   |                                    |                                                                                     |
   |                                    | Ancestor: ApplyServerSideEncryptionByDefault                                        |
   +------------------------------------+-------------------------------------------------------------------------------------+

Error Responses
---------------

In addition to common error codes, this API also returns others. The following table lists common errors and possible causes. For details, see :ref:`Table 2 <obs_04_0063__table1488314173514>`.

.. _obs_04_0063__table1488314173514:

.. table:: **Table 2** Error codes related to getting bucket encryption configuration

   +-------------------------------+------------------------------------------------------------------+------------------+
   | Error Code                    | Description                                                      | HTTP Status Code |
   +===============================+==================================================================+==================+
   | NoSuchEncryptionConfiguration | The specified bucket does not have any encryption configurations | 404 Not Found    |
   +-------------------------------+------------------------------------------------------------------+------------------+

Sample Request
--------------

.. code-block:: text

   GET /?encryption HTTP/1.1
   User-Agent: curl/7.29.0
   Host: examplebucket.obs.region.example.com
   Accept: */*
   Date:  Thu, 21 Feb 2019 03:05:34 GMT
   Authorization: OBS H4IPJX0TQTHTHEBQQCEC:DpSAlmLX/BTdjxU5HOEwflhM0WI=

Sample Response
---------------

::

   HTTP/1.1 200 OK
   Server: OBS
   x-obs-request-id: BF26000001643670AC06E7B9A7767921
   x-obs-id-2: 32AAAQAAEAABSAAgAAEAABAAAQAAEAABCSvK6z8HV6nrJh49gsB5vqzpgtohkiFm
   Date: Thu, 21 Feb 2019 03:05:34 GMT
   Content-Length: 788

   <?xml version="1.0" encoding="UTF-8" standalone="yes"?>
   <ServerSideEncryptionConfiguration xmlns="http://obs.region.example.com/doc/2015-06-30/">
       <Rule>
           <ApplyServerSideEncryptionByDefault>
               <SSEAlgorithm>kms</SSEAlgorithm>
               <KMSMasterKeyID>4f1cd4de-ab64-4807-920a-47fc42e7f0d0</KMSMasterKeyID>
           </ApplyServerSideEncryptionByDefault>
       </Rule>
   </ServerSideEncryptionConfiguration>
