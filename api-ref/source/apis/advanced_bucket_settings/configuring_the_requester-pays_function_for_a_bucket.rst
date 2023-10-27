:original_name: obs_04_0068.html

.. _obs_04_0068:

Configuring the Requester-Pays Function for a Bucket
====================================================

Functions
---------

The requester-pays configuration allows the requester to pay for data transfer and API calls associated with accessing the requested OBS resources, while the bucket owner only pays for data storage.

.. note::

   To access a requester-pays bucket, users (except the bucket owner and IAM users under the same account as the bucket owner) must add the **x-obs-request-payer: requester** header in the request, indicating that the requester agrees to pay for the request and traffic. If this header is not included in the request, the authentication fails and error "403 Forbidden" is returned. If the response returned by the server includes the **x-obs-request-charged: requester** header, the requester is billed for the request. This rule is applicable to all API requests against requester-pays buckets.

Request Syntax
--------------

.. code-block:: text

   PUT /?requestPayment HTTP/1.1
   Host: bucketname.obs.region.example.com
   Date: date
   Authorization: authorization
   Content-Length: length

   <RequestPaymentConfiguration>
       <Payer>Payer</Payer>
   </RequestPaymentConfiguration>

Request Parameters
------------------

This request contains no message parameters.

Request Headers
---------------

This request uses common headers. For details, see :ref:`Table 3 <obs_04_0007__table25197309>`.

Request Elements
----------------

This request contains elements that specify the requester-pays configuration for the bucket. Configuration information is uploaded in the XML format. The following table lists request elements.

.. table:: **Table 1** Elements for configuring the requester-pays function

   +-----------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
   | Element                     | Description                                                                                                                                                                         | Mandatory             |
   +=============================+=====================================================================================================================================================================================+=======================+
   | RequestPaymentConfiguration | Root node of the requester-pays configuration.                                                                                                                                      | Yes                   |
   |                             |                                                                                                                                                                                     |                       |
   |                             | Ancestor: none                                                                                                                                                                      |                       |
   +-----------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
   | Payer                       | Specifies who pays for accessing resources in the bucket.                                                                                                                           | Yes                   |
   |                             |                                                                                                                                                                                     |                       |
   |                             | Type: string                                                                                                                                                                        |                       |
   |                             |                                                                                                                                                                                     |                       |
   |                             | Ancestor: **RequestPaymentConfiguration**                                                                                                                                           |                       |
   |                             |                                                                                                                                                                                     |                       |
   |                             | Value options:                                                                                                                                                                      |                       |
   |                             |                                                                                                                                                                                     |                       |
   |                             | -  **BucketOwner**: The bucket owner pays all fees associated with the bucket.                                                                                                      |                       |
   |                             | -  **Requester**: The requester pays for data transfer and API calls associated with accessing resources in the bucket, while the bucket owner pays for data storage in the bucket. |                       |
   +-----------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+

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

This response contains no elements.

Error Responses
---------------

No special error responses are returned. For details about error responses, see :ref:`Table 2 <obs_04_0115__d0e843>`.

Sample Request
--------------

.. code-block:: text

   PUT/?requestPayment HTTP/1.1
   User-Agent: curl/7.29.0
   Host: examplebucket.obs.region.example.com
   Accept: */*
   Date: Tue, 03 Mar 2020 12:07:05 GMT
   Authorization: OBS H4IPJX0TQTHTHEBQQCEC:5DGAS7SBbMC1YTC4tNXY57Zl2Fo=

   <RequestPaymentConfiguration>
       <Payer>Requester</Payer>
   </RequestPaymentConfiguration>

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
