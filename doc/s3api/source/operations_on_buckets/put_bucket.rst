:original_name: en-us_topic_0125560305.html

.. _en-us_topic_0125560305:

PUT Bucket
==========

You can send the **PUT Bucket** request to create a bucket with the specified name.

.. note::

   You can create a maximum of 100 buckets.

The name of a bucket must be unique in OBS. If a user repeatedly creates namesake buckets in the same region, status code **200** is returned. If namesake buckets are repeatedly created in other cases, status code **409** is returned. You can set the ACL of a bucket by adding optional header **x-amz-acl** to a request.

.. note::

   In multiple regions scenarios, if user A creates a bucket, deletes the bucket later, and immediately creates a bucket with the same name in different regions, the system will respond **409**. If user A creates a bucket with the same name in different regions 30 minutes later, the system will respond **200**.

   If a 5\ *xx* error is returned from the server or the request times out during bucket creation, the system takes about 10 minutes to make bucket information consistent. During the process, bucket information is inaccurate.

Storage Class
-------------

Users are allowed to create buckets of different storage classes. The **x-default-storage-class** header in a bucket creation request specifies the default storage class for a bucket. The storage class of the objects in a bucket is the same as that of the bucket. There are three storage classes: STANDARD (OBS Standard), STANDARD_IA (OBS Warm), and GLACIER (OBS Cold). If this header is not in the request, the storage class of the bucket created is OBS Standard. When users upload an object to a bucket, if they do not set the storage class of the object (see :ref:`PUT Object <en-us_topic_0125560399>`), the object will use the default storage class of the bucket.

Request Syntax
--------------

.. code-block:: text

   PUT / HTTP/1.1
    User-Agent: agent
    Host: Host Server
    Accept: */*
    Date: date
    Authorization: authorization
    x-amz-epid: epid
    Content-Length: 0
    <Optional Additional Header>

    <CreateBucketConfiguration xmlns="http://obs.example.com/doc/2015-06-30/">
    <LocationConstraint>location</LocationConstraint>
    </CreateBucketConfiguration>

Request Parameters
------------------

This request involves no parameters.

Request Headers
---------------

This request uses common headers. For details about common request headers, see section :ref:`Common Request Headers <en-us_topic_0125560462>`.

You can add optional headers to this request. :ref:`Table 1 <en-us_topic_0125560305__table31170320>` describes the optional headers.

.. _en-us_topic_0125560305__table31170320:

.. table:: **Table 1** Optional request headers

   +-------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+----------------------------------------------------------------------------------+
   | Header                  | Description                                                                                                                                                                                                                                                                                                                   | Remarks                                                                          |
   +=========================+===============================================================================================================================================================================================================================================================================================================================+==================================================================================+
   | x-amz-acl               | Indicates the ACL of a bucket. Possible values are **private**, **public-read**, **public-read-write**, **authenticated-read**, **bucket-owner-read**, and **bucket-owner-full-control**. For details, see :ref:`Table 4 <en-us_topic_0125560406__table40200743>`.                                                            | Optional                                                                         |
   |                         |                                                                                                                                                                                                                                                                                                                               |                                                                                  |
   |                         | Type: String                                                                                                                                                                                                                                                                                                                  |                                                                                  |
   +-------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+----------------------------------------------------------------------------------+
   | x-default-storage-class | When creating a bucket, you can add this header in the request to set the bucket's default storage class, which can be STANDARD (OBS Standard), STANDARD_IA (OBS Warm), and GLACIER (OBS Cold). If this header is not specified in the request, the storage class of the bucket created is OBS Standard.                      | Optional                                                                         |
   |                         |                                                                                                                                                                                                                                                                                                                               |                                                                                  |
   |                         | Type: String                                                                                                                                                                                                                                                                                                                  |                                                                                  |
   +-------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+----------------------------------------------------------------------------------+
   | x-amz-security-token    | Header field used to identify the request of a federated user. When the federal authentication function is enabled, users sending such requests are identified as federated users.                                                                                                                                            | Optional. This parameter must be carried in the request sent by federated users. |
   |                         |                                                                                                                                                                                                                                                                                                                               |                                                                                  |
   |                         | Type: string                                                                                                                                                                                                                                                                                                                  |                                                                                  |
   +-------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+----------------------------------------------------------------------------------+
   | x-amz-epid              | Enterprise project ID, which can be obtained from the enterprise project service. The value is a universally unique identifier (UUID). The value of a default enterprise project is **0** or does not contain this header. Users who have not enabled the enterprise project service do not need to carry this header either. | Optional                                                                         |
   |                         |                                                                                                                                                                                                                                                                                                                               |                                                                                  |
   |                         | Type: string                                                                                                                                                                                                                                                                                                                  |                                                                                  |
   |                         |                                                                                                                                                                                                                                                                                                                               |                                                                                  |
   |                         | Example: **x-amz-epid: 9892d768-2d13-450f-aac7-ed0e44c2585f**                                                                                                                                                                                                                                                                 |                                                                                  |
   +-------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+----------------------------------------------------------------------------------+

Request Elements
----------------

This request contains one element, as described in :ref:`Table 2 <en-us_topic_0125560305__table5512965>`

.. _en-us_topic_0125560305__table5512965:

.. table:: **Table 2** Request element

   +-----------------------+------------------------------------------------------------------------------------------------------------------+-----------------------+
   | Element               | Description                                                                                                      | Remarks               |
   +=======================+==================================================================================================================+=======================+
   | LocationConstraint    | Indicates the Region where a bucket will be created. This element is contained in **CreateBucketConfiguration**. | Optional              |
   |                       |                                                                                                                  |                       |
   |                       | Type: String                                                                                                     |                       |
   +-----------------------+------------------------------------------------------------------------------------------------------------------+-----------------------+

Response Syntax
---------------

.. code-block::

   HTTP/1.1 status_code
    x-amz-request-id: request id
    x-reserved: amazon, aws and amazon web services are trademarks or registered trademarks of Amazon Technologies, Inc
    Location: location
    x-amz-id-2: id
    Date: date
    Content-Length: 0

Response Headers
----------------

This response uses common headers. For details about common response headers, see section :ref:`Common Response Headers <en-us_topic_0125560484>`.

Response Elements
-----------------

This response involves no elements.

Error Responses
---------------

No special error responses are returned. For details about error responses, see :ref:`Table 1 <en-us_topic_0125560440__table30733758>`.

Sample Request
--------------

.. code-block:: text

   PUT / HTTP/1.1
    User-Agent: Jakarta Commons-HttpClient/3.1
    Host: bucketname.obs.example.com
    Accept: */*
    Date: Sat, 03 Dec 2011 06:31:58 +0000
    Authorization: AWS BF6C09F302931425E9A7:QBaO+tS/76QYHVnUoxvf9EPH/3o=
    x-amz-epid: 9892d768-2d13-450f-aac7-ed0e44c2585f
    Content-Length: 0

Sample Response
---------------

.. code-block::

   HTTP/1.1 200 OK
    Server: OBS
    x-amz-request-id: 001B21A61C6C00000134029F41D1527F
    x-reserved: amazon, aws and amazon web services are trademarks or registered trademarks of Amazon Technologies, Inc
    Location: /bucketname
    x-amz-id-2: MDAxQjIxQTYxQzZDMDAwMDAxMzQwMjlGNDFEMTUyN0ZBQUFBQUFBQWJiYmJiYmJi
    Date: Sat, 03 Dec 2011 06:31:58 GMT
    Content-Length: 0

Sample Request (Example of Setting the Region of a Bucket)
----------------------------------------------------------

.. code-block:: text

   PUT / HTTP/1.1
    User-Agent: Jakarta Commons-HttpClient/3.1
    Host: bucketname.obs.example.com
    Accept: */*
    Date: Sat, 03 Dec 2011 06:31:58 +0000
    Authorization: AWS BF6C09F302931425E9A7:QBaO+tS/76QYHVnUoxvf9EPH/3o=
    x-amz-epid: 9892d768-2d13-450f-aac7-ed0e44c2585f
    Content-Length: 149

   <CreateBucketConfiguration xmlns="http://obs.example.com/doc/2015-06-30/">
   <LocationConstraint>EU</LocationConstraint>
   </CreateBucketConfiguration>

Sample Response (Example of Setting the Region of a Bucket)
-----------------------------------------------------------

.. code-block::

   HTTP/1.1 200 OK
    Server: OBS
    x-amz-request-id: 001B21A61C6C00000134029F41D1527F
    x-reserved: amazon, aws and amazon web services are trademarks or registered trademarks of Amazon Technologies, Inc
    Location: /bucketname
    x-amz-id-2: MDAxQjIxQTYxQzZDMDAwMDAxMzQwMjlGNDFEMTUyN0ZBQUFBQUFBQWJiYmJiYmJi
    Date: Sat, 03 Dec 2011 06:31:58 GMT
    Content-Length: 0

Sample Request (Example of Creating a parallel file system)
-----------------------------------------------------------

.. code-block:: text

   PUT / HTTP/1.1
   User-Agent: curl/7.29.0
   Host: examplebucket.obs.region.example.com
   Accept: */*
   Date: WED, 01 Jul 2015 02:25:05 GMT
   Authorization: AWS H4IPJX0TQTHTHEBQQCEC:75/Y4Ng1izvzc1nTGxpMXTE6ynw=
   Content-Length: 157
   <CreateBucketConfiguration xmlns="http://obs.region.example.com/doc/2015-06-30/">
   <Location>region</Location>
   </CreateBucketConfiguration>

Sample Response (Example of Creating a parallel file system)
------------------------------------------------------------

::

   HTTP/1.1 200 OK
   Server: OBS
   x-amz-request-id: BF260000016435CE298386946AE4C482
   Location: /examplebucket
   x-amz-id-2: 32AAAQAAEAABSAAgAAEAABAAAQAAEAABCT9W2tcvLmMJ+plfdopaD62S0npbaRUz
   Date: WED, 01 Jul 2015 02:25:06 GMT
   Content-Length: 0
