:original_name: obs_04_0069.html

.. _obs_04_0069:

Obtaining the Requester-Pays Configuration Information of a Bucket
==================================================================

Functions
---------

This API obtains the requester-pays configuration information of a bucket.

Request Syntax
--------------

.. code-block:: text

   GET /?requestPayment HTTP/1.1
   Host: bucketname.obs.region.example.com
   Date: date
   Authorization: authorization
   Content-Length: length

Request Parameters
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
   Content-Type: type
   Date: date
   Content-Length: length

   <?xml version="1.0" encoding="UTF-8" standalone="yes"?>
   <RequestPaymentConfiguration xmlns="http://obs.example.com/doc/2015-06-30/">
     <Payer>Payer</Payer>
   </RequestPaymentConfiguration>

Response Headers
----------------

The response to the request uses common headers. For details, see :ref:`Table 1 <obs_04_0013__d0e686>`.

Response Elements
-----------------

This response contains the following elements:

+-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| Element                           | Description                                                                                                                                                                         |
+===================================+=====================================================================================================================================================================================+
| RequestPaymentConfiguration       | Elements of the requester-pays configuration.                                                                                                                                       |
|                                   |                                                                                                                                                                                     |
|                                   | Type: container                                                                                                                                                                     |
+-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| Payer                             | Identifier of who pays for the bucket.                                                                                                                                              |
|                                   |                                                                                                                                                                                     |
|                                   | Type: string                                                                                                                                                                        |
|                                   |                                                                                                                                                                                     |
|                                   | Ancestor: **RequestPaymentConfiguration**                                                                                                                                           |
|                                   |                                                                                                                                                                                     |
|                                   | Value options:                                                                                                                                                                      |
|                                   |                                                                                                                                                                                     |
|                                   | -  **BucketOwner**: The bucket owner pays all fees associated with the bucket.                                                                                                      |
|                                   | -  **Requester**: The requester pays for data transfer and API calls associated with accessing resources in the bucket, while the bucket owner pays for data storage in the bucket. |
+-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Error Responses
---------------

No special error responses are returned. For details about error responses, see :ref:`Table 2 <obs_04_0115__d0e843>`.

Sample Request
--------------

.. code-block:: text

   GET /?requestPayment HTTP/1.1
   User-Agent: curl/7.29.0
   Host: examplebucket.obs.region.example.com
   Accept: */*
   Date: Tue, 03 Mar 2020 12:07:05 GMT
   Authorization: OBS H4IPJX0TQTHTHEBQQCEC:5DGAS7SBbMC1YTC4tNXY57Zl2Fo=

Sample Response
---------------

::

   HTTP/1.1 200 OK
   Server: OBS
   x-obs-request-id: 0000016A6C21AD79654C09D9AA45EB5D
   x-obs-id-2: 32AAAQAAEAABAAAQAAEAABAAAQAAEAABCSmfq4hegf1QZv8/ewfveE4B566v5DZ8
   Content-Type: application/xml
   Date: Tue, 30 Apr 2019 02:45:07 GMT
   Content-Length: 0

   <?xml version="1.0" encoding="UTF-8" standalone="yes"?>
   <RequestPaymentConfiguration xmlns="http://obs.example.com/doc/2015-06-30/">
     <Payer>Requester</Payer>
   </RequestPaymentConfiguration>
