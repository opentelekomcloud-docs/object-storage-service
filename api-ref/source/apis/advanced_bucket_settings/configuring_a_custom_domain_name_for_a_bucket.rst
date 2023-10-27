:original_name: obs_04_0059.html

.. _obs_04_0059:

Configuring a Custom Domain Name for a Bucket
=============================================

Functions
---------

OBS uses the PUT method to configure a custom domain name for a bucket. After the configuration is successful, you can access the bucket through the domain name.

Ensure that the custom domain name can correctly resolve to the OBS service through DNS.

Request Syntax
--------------

.. code-block:: text

   PUT /?customdomain=domainname HTTP/1.1
   User-Agent: curl/7.29.0
   Host: bucketname.obs.region.example.com
   Accept: */*
   Date: date
   Authorization: authorization string
   Content-Length: 0

Request Parameters
------------------

.. table:: **Table 1** Request parameters

   +-----------------------+--------------------------------------------------------------------------------------------------------------------+-----------------------+
   | Parameter             | Description                                                                                                        | Mandatory             |
   +=======================+====================================================================================================================+=======================+
   | customdomain          | Custom domain name of a bucket.                                                                                    | Yes                   |
   |                       |                                                                                                                    |                       |
   |                       | Type: string, which must meet the naming conventions of domain names.                                              |                       |
   |                       |                                                                                                                    |                       |
   |                       | Specifications: The value contains a maximum of 256 characters.                                                    |                       |
   |                       |                                                                                                                    |                       |
   |                       | No default value.                                                                                                  |                       |
   |                       |                                                                                                                    |                       |
   |                       | Constraints: A bucket can have a maximum of 30 domain names. A custom domain name can be used for only one bucket. |                       |
   +-----------------------+--------------------------------------------------------------------------------------------------------------------+-----------------------+

Request Header
--------------

This request uses common headers. For details, see :ref:`Table 3 <obs_04_0007__table25197309>`.

Request Elements
----------------

This request involves no elements.

Response Syntax
---------------

::

   HTTP/1.1 200 OK
   Server: OBS
   x-obs-request-id: request id
   x-obs-id-2:  id
   Date: date
   Content-Length: 0

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

   PUT /?customdomain=obs.ccc.com HTTP/1.1
   User-Agent: curl/7.29.0
   Host: examplebucket.obs.region.example.com
   Accept: */*
   Date: Mon, 14 Jan 2019 08:31:36 +0000
   Authorization: OBS UDSIAMSTUBTEST000094:u2kJF4kENs6KlIDcAZpAKSKPtnc=
   Content-Length: 0

Sample Response
---------------

::

   HTTP/1.1 200 OK
   Server: OBS
   x-obs-request-id: 000001697692CC5380E9D272E6D8F830
   x-obs-id-2: 32AAAQAAEAABSAAgAAEAABAAAQAAEAABCSsfu2GXj9gScHhFnrrTPY2cFOEZuvta
   Date: Wed, 13 Mar 2019 10:22:05 GMT
   Content-Length: 0
