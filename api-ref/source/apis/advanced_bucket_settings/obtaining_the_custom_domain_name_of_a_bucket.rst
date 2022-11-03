:original_name: obs_04_0060.html

.. _obs_04_0060:

Obtaining the Custom Domain Name of a Bucket
============================================

Functions
---------

OBS uses the GET method to obtain the custom domain name of a bucket.

Request Syntax
--------------

.. code-block:: text

   GET /?customdomain HTTP/1.1
   User-Agent: curl/7.29.0
   Host: bucketname.obs.region.example.com
   Accept: */*
   Date: date
   Authorization: authorization string

Request Parameters
------------------

This request message does not contain the request parameters.

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
   x-obs-id-2: id
   Content-Type: application/xml
   Date: date
   Content-Length: 272

   <?xml version="1.0" encoding="UTF-8" standalone="yes"?>
   <ListBucketCustomDomainsResult xmlns="http://obs.example.com/doc/2015-06-30/">
     <Domains>
       <DomainName>domainname</DomainName>
       <CreateTime>createtime</CreateTime>
     </Domains>
   </ListBucketCustomDomainsResult>

Response Headers
----------------

The response to the request uses common headers. For details, see :ref:`Table 1 <obs_04_0013__d0e686>`.

Response Elements
-----------------

The response returns the custom domain name of the bucket in the form of message elements. :ref:`Table 1 <obs_04_0060__d0e8370>` lists details about each element.

.. _obs_04_0060__d0e8370:

.. table:: **Table 1** Response elements

   +-----------------------------------+--------------------------------------------------+
   | Element                           | Description                                      |
   +===================================+==================================================+
   | ListBucketCustomDomainsResult     | Container of the returned result                 |
   |                                   |                                                  |
   |                                   | Type: container                                  |
   |                                   |                                                  |
   |                                   | Children: Domains                                |
   |                                   |                                                  |
   |                                   | Ancestor: none                                   |
   +-----------------------------------+--------------------------------------------------+
   | Domains                           | Element indicating the custom domain name        |
   |                                   |                                                  |
   |                                   | Type: element                                    |
   |                                   |                                                  |
   |                                   | Children: DomainName, CreateTime                 |
   |                                   |                                                  |
   |                                   | Ancestor: ListBucketCustomDomainsResult          |
   +-----------------------------------+--------------------------------------------------+
   | DomainName                        | Custom domain name                               |
   |                                   |                                                  |
   |                                   | Type: string                                     |
   |                                   |                                                  |
   |                                   | Children: none                                   |
   |                                   |                                                  |
   |                                   | Ancestor: Domains                                |
   +-----------------------------------+--------------------------------------------------+
   | CreateTime                        | Time when a custom domain name is created        |
   |                                   |                                                  |
   |                                   | Type: string, expressed in the form of UTC time. |
   |                                   |                                                  |
   |                                   | Children: none                                   |
   |                                   |                                                  |
   |                                   | Ancestor: Domains                                |
   +-----------------------------------+--------------------------------------------------+

Error Responses
---------------

No special error responses are returned. For details about error responses, see :ref:`Table 2 <obs_04_0115__d0e843>`.

Sample Request
--------------

.. code-block:: text

   GET /?customdomain HTTP/1.1
   User-Agent: curl/7.29.0
   Host: examplebucket.obs.region.example.com
   Accept: */*
   Date: Mon, 14 Jan 2019 08:31:45 +0000
   Authorization: OBS UDSIAMSTUBTEST000094:veTm8B18MPLFqNyGh2wmQqovZ2U=

Sample Response
---------------

::

   HTTP/1.1 200 OK
   Server: OBS
   x-obs-request-id: 000001697693130C80E9D2D29FA84FC2
   x-obs-id-2: 32AAAQAAEAABAAAQAAEAABAAAQAAEAABCSM80AI9weqGUsIFJScVxSKlG4DmypX9
   Content-Type: application/xml
   Date: Wed, 13 Mar 2019 10:22:24 GMT
   Content-Length: 272

   <?xml version="1.0" encoding="UTF-8" standalone="yes"?>
   <ListBucketCustomDomainsResult xmlns="http://obs.example.com/doc/2015-06-30/">
     <Domains>
       <DomainName>obs.ccc.com</DomainName>
       <CreateTime>2019-03-13T10:22:05.912Z</CreateTime>
     </Domains>
   </ListBucketCustomDomainsResult>
