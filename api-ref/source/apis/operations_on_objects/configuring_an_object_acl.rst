:original_name: obs_04_0089.html

.. _obs_04_0089:

Configuring an Object ACL
=========================

Functions
---------

OBS supports the control of access permission for objects. By default, only the object creator has the read and write permissions for the object. However, the creator can set a public access policy to assign the read permission to all other users. Even if the ACL is configured for an object encrypted in the SSE-KMS mode, the inter-tenant access is unavailable.

You can set an access control policy when uploading an object or make a call of an API operation to modify or obtain the object ACL. An object ACL supports a maximum of 100 grants.

This section explains how to modify an object ACL and change access permission on an object.

Versioning
----------

By default, this operation modifies the ACL of the latest version of an object. To specify a specified version, the request can carry the **versionId** parameter.

Request Syntax
--------------

.. code-block:: text

   PUT /ObjectName?acl HTTP/1.1
   Host: bucketname.obs.region.example.com
   Date: date
   Authorization: authorization

   <AccessControlPolicy>
       <Owner>
           <ID>ID</ID>
       </Owner>
       <Delivered>true</Delivered>
       <AccessControlList>
           <Grant>
               <Grantee>
                  <ID>ID</ID>
               </Grantee>
               <Permission>permission</Permission>
           </Grant>
       </AccessControlList>
   </AccessControlPolicy>

Request Parameters
------------------

:ref:`Table 1 <obs_04_0089__table44298471191845>` describes the request parameters.

.. _obs_04_0089__table44298471191845:

.. table:: **Table 1** Request parameters

   +-----------------------+------------------------------------------------------------------------------+-----------------------+
   | Parameter             | Description                                                                  | Mandatory (Yes/No)    |
   +=======================+==============================================================================+=======================+
   | versionId             | Object version ID. The ACL of the specified object version is to be changed. | No                    |
   |                       |                                                                              |                       |
   |                       | Type: string                                                                 |                       |
   +-----------------------+------------------------------------------------------------------------------+-----------------------+

Request Headers
---------------

This request uses common headers. For details, see :ref:`Table 3 <obs_04_0007__table25197309>`.

In addition to the common request headers, the header listed in :ref:`Table 2 <obs_04_0089__table101171333196>` may be used.

.. _obs_04_0089__table101171333196:

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

The request message carries the ACL information of the object by using message elements. For the meanings of the elements, see :ref:`Table 3 <obs_04_0089__table6365150>`.

.. _obs_04_0089__table6365150:

.. table:: **Table 3** Request elements

   +-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
   | Element               | Description                                                                                                                                                             | Mandatory (Yes/No)    |
   +=======================+=========================================================================================================================================================================+=======================+
   | AccessControlPolicy   | Access control policy. AccessControlPolicy is a parent node of Owner, Delivered, and AccessControlList.                                                                 | Yes                   |
   |                       |                                                                                                                                                                         |                       |
   |                       | Type: XML                                                                                                                                                               |                       |
   +-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
   | AccessControlList     | Access control list. AccessControlList is the parent node of Grant.                                                                                                     | Yes                   |
   |                       |                                                                                                                                                                         |                       |
   |                       | Type: XML                                                                                                                                                               |                       |
   +-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
   | Owner                 | Owner information of a bucket. Owner is a parent node of ID.                                                                                                            | Yes                   |
   |                       |                                                                                                                                                                         |                       |
   |                       | Type: XML                                                                                                                                                               |                       |
   +-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
   | ID                    | Domain ID of a user.                                                                                                                                                    | Yes                   |
   |                       |                                                                                                                                                                         |                       |
   |                       | Type: string                                                                                                                                                            |                       |
   +-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
   | Grant                 | Identifies the grantee and the permissions of the grantee. An ACL of an object can contain a maximum of 100 grants. Grant is the parent node of Grantee and Permission. | No                    |
   |                       |                                                                                                                                                                         |                       |
   |                       | Type: XML                                                                                                                                                               |                       |
   +-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
   | Grantee               | Used to record user information. Grantee is a parent node of ID.                                                                                                        | No                    |
   |                       |                                                                                                                                                                         |                       |
   |                       | Type: XML                                                                                                                                                               |                       |
   +-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
   | Canned                | Grants permissions to all users.                                                                                                                                        | No                    |
   |                       |                                                                                                                                                                         |                       |
   |                       | Range: Everyone                                                                                                                                                         |                       |
   |                       |                                                                                                                                                                         |                       |
   |                       | Type: string                                                                                                                                                            |                       |
   +-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
   | Delivered             | Indicates whether an object ACL inherits the ACL of a bucket.                                                                                                           | No                    |
   |                       |                                                                                                                                                                         |                       |
   |                       | Type: boolean                                                                                                                                                           |                       |
   |                       |                                                                                                                                                                         |                       |
   |                       | Default value: **true**                                                                                                                                                 |                       |
   +-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
   | Permission            | Authorized permission.                                                                                                                                                  | No                    |
   |                       |                                                                                                                                                                         |                       |
   |                       | Value options: **READ**, **READ_ACP**, **WRITE_ACP**, **FULL_CONTROL**                                                                                                  |                       |
   |                       |                                                                                                                                                                         |                       |
   |                       | Type: string                                                                                                                                                            |                       |
   +-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+

Response Syntax
---------------

::

   HTTP/1.1 status_code
   Content-Length: length
   Content-Type: application/xml

Response Headers
----------------

The response to the request uses common headers. For details, see :ref:`Table 1 <obs_04_0013__d0e686>`.

In addition to the common response headers, the headers listed in :ref:`Table 4 <obs_04_0089__table286211613564>` may be used.

.. _obs_04_0089__table286211613564:

.. table:: **Table 4** Additional response headers

   +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter             | Type                  | Description                                                                                                                                                               |
   +=======================+=======================+===========================================================================================================================================================================+
   | x-obs-version-id      | String                | **Definition**:                                                                                                                                                           |
   |                       |                       |                                                                                                                                                                           |
   |                       |                       | Version ID of the object whose ACL is modified.                                                                                                                           |
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

This response contains no elements.

Error Responses
---------------

No special error responses are returned. For details about error responses, see :ref:`Table 2 <obs_04_0115__d0e843>`.

Sample Request
--------------

.. code-block:: text

   PUT /obj2?acl HTTP/1.1
   User-Agent: curl/7.29.0
   Host: examplebucket.obs.region.example.com
   Accept: */*
   Date: WED, 01 Jul 2015 04:42:34 GMT
   Authorization: OBS H4IPJX0TQTHTHEBQQCEC:8xAODun1ofjkwHm8YhtN0QEcy9M=
   Content-Length: 727

   <AccessControlPolicy xmlns="http://obs.example.com/doc/2015-06-30/">
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
         <Permission>READ</Permission>
       </Grant>
     </AccessControlList>
   </AccessControlPolicy>

Sample Response
---------------

::

   HTTP/1.1 200 OK
   Server: OBS
   x-obs-request-id: 8DF400000163D3F0FD2A03D2D30B0542
   x-obs-id-2: 32AAAUgAIAABAAAQAAEAABAAAQAAEAABCTjCqTmsA1XRpIrmrJdvcEWvZyjbztdd
   Date: WED, 01 Jul 2015 04:42:34 GMT
   Content-Length: 0
