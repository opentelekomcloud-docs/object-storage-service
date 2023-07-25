:original_name: obs_04_0030.html

.. _obs_04_0030:

Configuring a Bucket ACL
========================

Functions
---------

This operation controls access permissions for buckets. By default, only the creator of a bucket has the permission to read and write the bucket. You can also set other access permissions. For example, you can set a public read policy to grant the read permission to all users.

You can configure an ACL when creating a bucket, and modify or obtain the ACLs of existing buckets using the API operations. A bucket ACL supports a maximum of 100 grants. The PUT method is idempotent. With this method, a new bucket ACL will overwrite the previous bucket ACL. To modify or delete an ACL, you just need to create a new one using the PUT method.

Request Syntax
--------------

.. code-block:: text

   PUT /?acl HTTP/1.1
   Host: bucketname.obs.region.example.com
   Date: date
   Authorization: authorization
   Content-Type: application/xml
   Content-Length: length

   <AccessControlPolicy>
       <Owner>
           <ID>ID</ID>
       </Owner>
       <AccessControlList>
           <Grant>
               <Grantee>
                  <ID>domainId</ID>
               </Grantee>
               <Permission>permission</Permission>
               <Delivered>false</Delivered>
           </Grant>
       </AccessControlList>
   </AccessControlPolicy>

Request Parameters
------------------

This request contains no parameters.

Request Headers
---------------

You can change the ACL of a bucket by using the header settings. Each ACL configured with the header setting has a set of predefined grantees and authorized permissions. If you want to authorize access permissions by adding the header to a request, you must add the following header and specify the value.

.. table:: **Table 1** Optional header for specifying canned ACLs

   +-----------------------+--------------------------------------------------------------------------------------------------------------------------------+-----------------------+
   | Name                  | Description                                                                                                                    | Mandatory             |
   +=======================+================================================================================================================================+=======================+
   | x-obs-acl             | Uses the canned ACL for a bucket.                                                                                              | No                    |
   |                       |                                                                                                                                |                       |
   |                       | Value options: **private**, **public-read**, **public-read-write**, **public-read-delivered**, **public-read-write-delivered** |                       |
   |                       |                                                                                                                                |                       |
   |                       | Type: string                                                                                                                   |                       |
   +-----------------------+--------------------------------------------------------------------------------------------------------------------------------+-----------------------+

Request Elements
----------------

This request carries ACL information in elements to specify an ACL. :ref:`Table 3 <obs_04_0007__table25197309>` describes the elements.

.. table:: **Table 2** Additional request elements

   +-----------------------+----------------------------------------------------------------------------------------------------------------+-----------------------+
   | Element               | Description                                                                                                    | Mandatory             |
   +=======================+================================================================================================================+=======================+
   | Owner                 | Bucket owner information, including the ID                                                                     | Yes                   |
   |                       |                                                                                                                |                       |
   |                       | Type: XML                                                                                                      |                       |
   +-----------------------+----------------------------------------------------------------------------------------------------------------+-----------------------+
   | ID                    | Account ID of the authorized user                                                                              | Yes                   |
   |                       |                                                                                                                |                       |
   |                       | Type: string                                                                                                   |                       |
   +-----------------------+----------------------------------------------------------------------------------------------------------------+-----------------------+
   | Grant                 | Container for the grantee and the granted permissions A single bucket ACL can contain no more than 100 grants. | No                    |
   |                       |                                                                                                                |                       |
   |                       | Type: XML                                                                                                      |                       |
   +-----------------------+----------------------------------------------------------------------------------------------------------------+-----------------------+
   | Grantee               | Grantee information                                                                                            | No                    |
   |                       |                                                                                                                |                       |
   |                       | Type: XML                                                                                                      |                       |
   +-----------------------+----------------------------------------------------------------------------------------------------------------+-----------------------+
   | Canned                | Grants permissions to all users.                                                                               | No                    |
   |                       |                                                                                                                |                       |
   |                       | Value range: Everyone                                                                                          |                       |
   |                       |                                                                                                                |                       |
   |                       | Type: string                                                                                                   |                       |
   +-----------------------+----------------------------------------------------------------------------------------------------------------+-----------------------+
   | Delivered             | Indicates whether the bucket ACL is applied to all objects in the bucket.                                      | No                    |
   |                       |                                                                                                                |                       |
   |                       | Type: boolean                                                                                                  |                       |
   |                       |                                                                                                                |                       |
   |                       | Default value: **false**                                                                                       |                       |
   +-----------------------+----------------------------------------------------------------------------------------------------------------+-----------------------+
   | Permission            | Permissions to be granted.                                                                                     | No                    |
   |                       |                                                                                                                |                       |
   |                       | Value options: **READ**, **READ_ACP**, **WRITE**, **WRITE_ACP**, **FULL_CONTROL**                              |                       |
   |                       |                                                                                                                |                       |
   |                       | Type: string                                                                                                   |                       |
   +-----------------------+----------------------------------------------------------------------------------------------------------------+-----------------------+
   | AccessControlList     | Indicates an ACL, which consists of three elements: **Grant**, **Grantee**, and **Permission**.                | Yes                   |
   |                       |                                                                                                                |                       |
   |                       | Type: XML                                                                                                      |                       |
   +-----------------------+----------------------------------------------------------------------------------------------------------------+-----------------------+

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

This response involves no elements.

Error Responses
---------------

No special error responses are returned. For details, see :ref:`Table 2 <obs_04_0115__d0e843>`.

Sample Request
--------------

.. code-block:: text

   PUT /?acl HTTP/1.1
   User-Agent: curl/7.29.0
   Host: examplebucket.obs.region.example.com
   Accept: */*
   Date: WED, 01 Jul 2015 02:37:22 GMT
   Authorization: OBS H4IPJX0TQTHTHEBQQCEC:iqSPeUBl66PwXDApxjRKk6hlcN4=
   Content-Length: 727

   <AccessControlPolicy xmlns="http://obs.example.com/doc/2015-06-30/">
     <Owner>
       <ID>b4bf1b36d9ca43d984fbcb9491b6fce9</ID>
     </Owner>
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
         <Delivered>false</Delivered>
       </Grant>
       <Grant>
         <Grantee>
           <Canned>Everyone</Canned>
         </Grantee>
         <Permission>READ_ACP</Permission>
       </Grant>
     </AccessControlList>
   </AccessControlPolicy>

Sample Response
---------------

::

   HTTP/1.1 200 OK
   Server: OBS
   x-obs-request-id: BF2600000164361F2954B4D063164704
   x-obs-id-2: 32AAAQAAEAABSAAgAAEAABAAAQAAEAABCT78HTIBuhe0FbtSptrb/akwELtwyPKs
   Date: WED, 01 Jul 2015 02:37:22 GMT
   Content-Length: 0
