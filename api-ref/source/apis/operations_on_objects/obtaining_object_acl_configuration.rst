:original_name: obs_04_0090.html

.. _obs_04_0090:

Obtaining Object ACL Configuration
==================================

Functions
---------

The implementation of this operation returns the ACL configuration of an object. You can perform this operation to view the ACL of an object, as long as you have the read permission for the object ACL.

Versioning
----------

By default, this operation obtains the ACL of the latest version of an object. If the object has a delete marker, status code 404 is returned. To obtain the ACL of a specified version, the **versionId** parameter can be used to specify the desired version.

Request Syntax
--------------

.. code-block:: text

   GET /ObjectName?acl HTTP/1.1
   Host: bucketname.obs.region.example.com
   Date: date
   Authorization: authorization

Request Parameters
------------------

The request parameters required are described in :ref:`Table 1 <obs_04_0090__table22962068>`.

.. _obs_04_0090__table22962068:

.. table:: **Table 1** Request parameters

   +-----------------------+------------------------------+-----------------------+
   | Parameter             | Description                  | Mandatory (Yes/No)    |
   +=======================+==============================+=======================+
   | versionId             | Version number of an object. | No                    |
   |                       |                              |                       |
   |                       | Type: string                 |                       |
   +-----------------------+------------------------------+-----------------------+

Request Headers
---------------

This request uses common headers. For details, see :ref:`Table 3 <obs_04_0007__table25197309>`.

In addition to the common request headers, the header listed in :ref:`Table 2 <obs_04_0090__table101171333196>` may be used.

.. _obs_04_0090__table101171333196:

.. table:: **Table 2** Additional request header

   +---------------------+-----------------+--------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Header              | Type            | Mandatory (Yes/No) | Description                                                                                                                                                               |
   +=====================+=================+====================+===========================================================================================================================================================================+
   | x-obs-request-payer | String          | No                 | **Definition**:                                                                                                                                                           |
   |                     |                 |                    |                                                                                                                                                                           |
   |                     |                 |                    | Indicates that the requester agrees to pay for the request and traffic.                                                                                                   |
   |                     |                 |                    |                                                                                                                                                                           |
   |                     |                 |                    | **Constraints**:                                                                                                                                                          |
   |                     |                 |                    |                                                                                                                                                                           |
   |                     |                 |                    | If this header is not included in the request when the requester tries to access a requester-pays bucket, the authentication fails and error "403 Forbidden" is returned. |
   |                     |                 |                    |                                                                                                                                                                           |
   |                     |                 |                    | **Range**:                                                                                                                                                                |
   |                     |                 |                    |                                                                                                                                                                           |
   |                     |                 |                    | requester                                                                                                                                                                 |
   |                     |                 |                    |                                                                                                                                                                           |
   |                     |                 |                    | **Default value**:                                                                                                                                                        |
   |                     |                 |                    |                                                                                                                                                                           |
   |                     |                 |                    | None                                                                                                                                                                      |
   +---------------------+-----------------+--------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Request Elements
----------------

This request involves no elements.

Response Syntax
---------------

::

   HTTP/1.1 status_code
   Date: date
   Content-Length: length
   Content-Type: application/xml

   <?xml version="1.0" encoding="UTF-8" standalone="yes"?>
   <AccessControlPolicy xmlns="http://obs.region.example.com/doc/2015-06-30/">
       <Owner>
           <ID>id</ID>
       </Owner>
       <Delivered>true</Delivered>
       <AccessControlList>
           <Grant>
               <Grantee>
                   <ID>id</ID>
               </Grantee>
               <Permission>permission</Permission>
           </Grant>
       </AccessControlList>
   </AccessControlPolicy>

Response Headers
----------------

The response to the request uses common headers. For details, see :ref:`Table 1 <obs_04_0013__d0e686>`.

In addition to the common response headers, the headers listed in :ref:`Table 3 <obs_04_0090__table1784619142918>` may be used.

.. _obs_04_0090__table1784619142918:

.. table:: **Table 3** Additional response headers

   +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter             | Type                  | Description                                                                                                                                                               |
   +=======================+=======================+===========================================================================================================================================================================+
   | x-obs-version-id      | String                | **Definition**:                                                                                                                                                           |
   |                       |                       |                                                                                                                                                                           |
   |                       |                       | Version number of an object.                                                                                                                                              |
   |                       |                       |                                                                                                                                                                           |
   |                       |                       | **Range**:                                                                                                                                                                |
   |                       |                       |                                                                                                                                                                           |
   |                       |                       | The value must contain 32 characters.                                                                                                                                     |
   +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | x-obs-request-payer   | string                | **Definition**:                                                                                                                                                           |
   |                       |                       |                                                                                                                                                                           |
   |                       |                       | Indicates that the requester agrees to pay for the request and traffic.                                                                                                   |
   |                       |                       |                                                                                                                                                                           |
   |                       |                       | **Constraints**:                                                                                                                                                          |
   |                       |                       |                                                                                                                                                                           |
   |                       |                       | If this header is not included in the request when the requester tries to access a requester-pays bucket, the authentication fails and error "403 Forbidden" is returned. |
   |                       |                       |                                                                                                                                                                           |
   |                       |                       | **Range**:                                                                                                                                                                |
   |                       |                       |                                                                                                                                                                           |
   |                       |                       | requester                                                                                                                                                                 |
   |                       |                       |                                                                                                                                                                           |
   |                       |                       | **Default value**:                                                                                                                                                        |
   |                       |                       |                                                                                                                                                                           |
   |                       |                       | None                                                                                                                                                                      |
   +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Response Elements
-----------------

The response message of the request returns the ACL information of the object. :ref:`Table 4 <obs_04_0090__table23161487>` describes the elements.

.. _obs_04_0090__table23161487:

.. table:: **Table 4** Response elements

   +-----------------------------------+---------------------------------------------------------------+
   | Element                           | Description                                                   |
   +===================================+===============================================================+
   | ID                                | User account ID                                               |
   |                                   |                                                               |
   |                                   | Type: string                                                  |
   +-----------------------------------+---------------------------------------------------------------+
   | AccessControlList                 | List of users and their permissions for the bucket.           |
   |                                   |                                                               |
   |                                   | Type: XML                                                     |
   +-----------------------------------+---------------------------------------------------------------+
   | Grant                             | Identifies the grantee and the permissions of the grantee.    |
   |                                   |                                                               |
   |                                   | Type: XML                                                     |
   +-----------------------------------+---------------------------------------------------------------+
   | Grantee                           | Container for the details about the grantee.                  |
   |                                   |                                                               |
   |                                   | Type: XML                                                     |
   +-----------------------------------+---------------------------------------------------------------+
   | Delivered                         | Indicates whether an object ACL inherits the ACL of a bucket. |
   |                                   |                                                               |
   |                                   | Type: boolean                                                 |
   +-----------------------------------+---------------------------------------------------------------+
   | Permission                        | Permissions of a specified user for the bucket.               |
   |                                   |                                                               |
   |                                   | Type: string                                                  |
   +-----------------------------------+---------------------------------------------------------------+

Error Responses
---------------

No special error responses are returned. For details about error responses, see :ref:`Table 2 <obs_04_0115__d0e843>`.

Sample Request
--------------

.. code-block:: text

   GET /object011?acl HTTP/1.1
   User-Agent: curl/7.29.0
   Host: examplebucket.obs.region.example.com
   Accept: */*
   Date: WED, 01 Jul 2015 04:45:55 GMT
   Authorization: OBS H4IPJX0TQTHTHEBQQCEC:YcmvNQxItGjFeeC1K2HeUEp8MMM=

Sample Response
---------------

::

   HTTP/1.1 200 OK
   Server: OBS
   x-obs-request-id: 8DF400000163D3E650F3065C2295674C
   x-obs-id-2: 32AAAQAAEAABAAAQAAEAABAAAQAAEAABCS+wsHqRuA2Tx+mXUpNtBbWLPMle9CIx
   Content-Type: application/xml
   Date: WED, 01 Jul 2015 04:45:55 GMT
   Content-Length: 769

   <?xml version="1.0" encoding="utf-8"?>
   <AccessControlPolicy xmlns="http://obs.region.example.com/doc/2015-06-30/">
     <Owner>
       <ID>b4bf1b36d9ca43d984fbcb9491b6fce9</ID>
     </Owner>
     <Delivered>false</Delivered>
     <AccessControlList>
       <Grant>
         <Grantee>
           <ID>b4bf1b36d9ca43d984fbcb9491b6fce9</ID>
         </Grantee>
         <Permission>FULL_CONTROL</Permission>
       </Grant>
       <Grant>
         <Grantee>
           <ID>783fc6652cf246c096ea836694f71855</ID>
         </Grantee>
         <Permission>READ</Permission>
         </Grant>
       <Grant>
         <Grantee>
           <Canned>Everyone</Canned>
         </Grantee>
         <Permission>READ_ACP</Permission>
       </Grant>
     </AccessControlList>
   </AccessControlPolicy>
