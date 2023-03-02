:original_name: obs_04_0020.html

.. _obs_04_0020:

Listing Buckets
===============

Functions
---------

You can perform this operation to list all buckets that you have created.

Request Syntax
--------------

.. code-block:: text

   GET / HTTP/1.1
   Host: obs.region.example.com
   Date: date
   Authorization: authorization

Request Parameters
------------------

This request contains no parameters.

Request Headers
---------------

This request header uses common message fields. For details, see :ref:`Table 3 <obs_04_0007__table25197309>`.

The operation message header is the same as that of a common request. For details, see :ref:`Table 3 <obs_04_0007__table25197309>`. However, this request can contain additional headers. The following table describes the additional headers for this request.

.. table:: **Table 1** Additional request headers

   +-----------------------+-----------------------------------------------------------------------------------------------+-----------------------+
   | Header                | Description                                                                                   | Mandatory             |
   +=======================+===============================================================================================+=======================+
   | x-obs-bucket-type     | This header field is used to specify the content to be obtained.                              | No                    |
   |                       |                                                                                               |                       |
   |                       | Value:                                                                                        |                       |
   |                       |                                                                                               |                       |
   |                       | -  **OBJECT**: Obtain the list of all buckets.                                                |                       |
   |                       | -  **POSIX**: Obtain the list of all parallel file systems.                                   |                       |
   |                       |                                                                                               |                       |
   |                       | If this header is not carried, the list of all buckets and parallel file systems is obtained. |                       |
   |                       |                                                                                               |                       |
   |                       | Type: string                                                                                  |                       |
   |                       |                                                                                               |                       |
   |                       | Example: **x-obs-bucket-type: POSIX**                                                         |                       |
   +-----------------------+-----------------------------------------------------------------------------------------------+-----------------------+

Request Elements
----------------

The request does not use request elements.

Response Syntax
---------------

.. code-block:: text

   GET HTTP/1.1 status_code
   Content-Type: type
   Date: date
   Content-Length: length

   <?xml version="1.0" encoding="UTF-8" standalone="yes"?>
   <ListAllMyBucketsResult xmlns="http://obs.region.example.com/doc/2015-06-30/">
       <Owner>
           <ID>id</ID>
       </Owner>
       <Buckets>
           <Bucket>
               <Name>bucketName</Name>
               <CreationDate>date</CreationDate>
               <Location>region</Location>
               <BucketType>buckettype</BucketType>
           </Bucket>
           ...
       </Buckets>
   </ListAllMyBucketsResult>

Response Headers
----------------

The response to the request uses common headers. For details, see :ref:`Table 1 <obs_04_0013__d0e686>`.

Response Elements
-----------------

This response contains the XML list of buckets owned by the user. :ref:`Table 2 <obs_04_0020__table3679815894442>` describes the elements.

.. _obs_04_0020__table3679815894442:

.. table:: **Table 2** Response elements

   +-----------------------------------+----------------------------------------------------+
   | Element                           | Description                                        |
   +===================================+====================================================+
   | ListAllMyBucketsResult            | List of buckets created by the user                |
   |                                   |                                                    |
   |                                   | Type: XML                                          |
   +-----------------------------------+----------------------------------------------------+
   | Owner                             | Bucket owner information, including the tenant ID. |
   |                                   |                                                    |
   |                                   | Type: XML                                          |
   +-----------------------------------+----------------------------------------------------+
   | ID                                | Domain ID (account ID) of a user.                  |
   |                                   |                                                    |
   |                                   | Type: string                                       |
   +-----------------------------------+----------------------------------------------------+
   | Buckets                           | Buckets owned by the user                          |
   |                                   |                                                    |
   |                                   | Type: XML                                          |
   +-----------------------------------+----------------------------------------------------+
   | Bucket                            | Details about a bucket                             |
   |                                   |                                                    |
   |                                   | Type: XML                                          |
   +-----------------------------------+----------------------------------------------------+
   | Name                              | Bucket name                                        |
   |                                   |                                                    |
   |                                   | Type: string                                       |
   +-----------------------------------+----------------------------------------------------+
   | CreationDate                      | Creation time of the bucket                        |
   |                                   |                                                    |
   |                                   | Type: string                                       |
   +-----------------------------------+----------------------------------------------------+
   | Location                          | Location of the bucket                             |
   |                                   |                                                    |
   |                                   | Type: string                                       |
   +-----------------------------------+----------------------------------------------------+
   | BucketType                        | Bucket type                                        |
   |                                   |                                                    |
   |                                   | Type: string                                       |
   |                                   |                                                    |
   |                                   | -  **OBJECT**: indicates a bucket.                 |
   |                                   | -  **POSIX**: indicates a parallel file system.    |
   +-----------------------------------+----------------------------------------------------+

Error Responses
---------------

No special error responses are returned. For details about error responses, see :ref:`Table 2 <obs_04_0115__d0e843>`.

Sample Request
--------------

.. code-block:: text

   GET / HTTP/1.1
   User-Agent: curl/7.29.0
   Host: obs.region.example.com
   Accept: */*
   Date: Mon, 25 Jun 2018 05:37:12 +0000
   Authorization: OBS GKDF4C7Q6SI0IPGTXTJN:9HXkVQIiQKw33UEmyBI4rWrzmic=

Sample Response
---------------

::

   HTTP/1.1 200 OK
   Server: OBS
   x-obs-request-id: BF260000016435722C11379647A8A00A
   x-obs-id-2: 32AAAQAAEAABAAAQAAEAABAAAQAAEAABCSGGDRUM62QZi3hGP8Fz3gOloYCfZ39U
   Content-Type: application/xml
   Date: Mon, 25 Jun 2018 05:37:12 GMT
   Content-Length: 460

   <?xml version="1.0" encoding="UTF-8" standalone="yes"?>
   <ListAllMyBucketsResult xmlns="http://obs.example.com/doc/2015-06-30/">
     <Owner>
       <ID>783fc6652cf246c096ea836694f71855</ID>
     </Owner>
     <Buckets>
       <Bucket>
         <Name>examplebucket01</Name>
         <CreationDate>2018-06-21T09:15:01.032Z</CreationDate>
         <Location>region</Location>
         <BucketType>OBJECT</BucketType>
       </Bucket>
       <Bucket>
         <Name>examplebucket02</Name>
         <CreationDate>2018-06-22T03:56:33.700Z</CreationDate>
         <Location>region</Location>
         <BucketType>OBJECT</BucketType>
       </Bucket>
     </Buckets>
   </ListAllMyBucketsResult>
