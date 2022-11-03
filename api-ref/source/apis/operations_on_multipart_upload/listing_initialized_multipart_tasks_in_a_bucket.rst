:original_name: obs_04_0097.html

.. _obs_04_0097:

Listing Initialized Multipart Tasks in a Bucket
===============================================

Functions
---------

This operation queries all the multipart upload tasks that are initialized but have not been merged or canceled in a bucket.

Request Syntax
--------------

.. code-block:: text

   GET /?uploads&max-uploads=max HTTP/1.1
   Host: bucketname.obs.region.example.com
   Date: date
   Authorization: authorization

Request Parameters
------------------

This request uses parameters to specify the query range for multipart uploads. :ref:`Table 1 <obs_04_0097__table416285709507>` describes the parameters.

.. _obs_04_0097__table416285709507:

.. table:: **Table 1** Request parameters

   +-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
   | Parameter             | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                            | Mandatory             |
   +=======================+========================================================================================================================================================================================================================================================================================================================================================================================================================================================================+=======================+
   | delimiter             | For a multipart upload that contains delimiters, the string between the first character and the first delimiter in the object name (excluding the prefix specified in the request, if any) are returned as **CommonPrefix**. Multipart uploads with objects that contain **CommonPrefix** are considered as a group and returned as one record. The record contains no information about the tasks, only informing the user that the group involves multipart uploads. | No                    |
   |                       |                                                                                                                                                                                                                                                                                                                                                                                                                                                                        |                       |
   |                       | Type: string                                                                                                                                                                                                                                                                                                                                                                                                                                                           |                       |
   +-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
   | prefix                | If a prefix is specified, the response only contains tasks whose names start with the prefix value.                                                                                                                                                                                                                                                                                                                                                                    | No                    |
   |                       |                                                                                                                                                                                                                                                                                                                                                                                                                                                                        |                       |
   |                       | Type: string                                                                                                                                                                                                                                                                                                                                                                                                                                                           |                       |
   +-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
   | max-uploads           | Maximum number of multipart upload tasks returned. The value ranges from 1 to 1000. If the value has exceeded this range, 1000 tasks are returned by default.                                                                                                                                                                                                                                                                                                          | No                    |
   |                       |                                                                                                                                                                                                                                                                                                                                                                                                                                                                        |                       |
   |                       | Type: integer                                                                                                                                                                                                                                                                                                                                                                                                                                                          |                       |
   +-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
   | key-marker            | Lists multipart uploads that follow the value of **key-marker**.                                                                                                                                                                                                                                                                                                                                                                                                       | No                    |
   |                       |                                                                                                                                                                                                                                                                                                                                                                                                                                                                        |                       |
   |                       | Type: string                                                                                                                                                                                                                                                                                                                                                                                                                                                           |                       |
   +-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
   | upload-id-marker      | Lists multipart tasks that follow the value of **upload-id-marker** in **key-marker**. This parameter only functions together with **key-marker**.                                                                                                                                                                                                                                                                                                                     | No                    |
   |                       |                                                                                                                                                                                                                                                                                                                                                                                                                                                                        |                       |
   |                       | Type: string                                                                                                                                                                                                                                                                                                                                                                                                                                                           |                       |
   +-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+

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
   Date: date
   Content-Length: length

   <?xml version="1.0" encoding="UTF-8" standalone="yes"?>
   <ListMultipartUploadsResult xmlns="http://obs.region.example.com/doc/2015-06-30/">
       <Bucket>bucketname</Bucket>
       <KeyMarker/>
       <UploadIdMarker/>
       <NextKeyMarker>nextMarker</NextKeyMarker>
       <NextUploadIdMarker>idMarker</NextUploadIdMarker>
       <MaxUploads>maxUploads</MaxUploads>
       <IsTruncated>true</IsTruncated>
       <Upload>
           <Key>key</Key>
           <UploadId>uploadID</UploadId>
           <Initiator>
               <ID>domainID/domainID:userID/userID</ID>
           </Initiator>
           <Owner>
               <ID>ownerID</ID>
           </Owner>
           <StorageClass>storageclass</StorageClass>
           <Initiated>initiatedDate</Initiated>
       </Upload>
   </ListMultipartUploadsResult>

Response Headers
----------------

The response to the request uses common headers. For details, see :ref:`Table 1 <obs_04_0013__d0e686>`.

Response Elements
-----------------

This response contains elements of information about the multipart uploads. :ref:`Table 2 <obs_04_0097__table6365698795048>` describes the elements.

.. _obs_04_0097__table6365698795048:

.. table:: **Table 2** Response elements

   +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Element                           | Description                                                                                                                                               |
   +===================================+===========================================================================================================================================================+
   | ListMultipartUploadsResult        | Container for responses of requests.                                                                                                                      |
   |                                   |                                                                                                                                                           |
   |                                   | Type: container                                                                                                                                           |
   |                                   |                                                                                                                                                           |
   |                                   | Children: Bucket, KeyMarker, UploadIdMarker, NextKeyMarker, NextUploadIdMarker, MaxUploads, Delimiter, Prefix, Upload, CommonPrefixes, IsTruncated        |
   |                                   |                                                                                                                                                           |
   |                                   | Ancestor: none                                                                                                                                            |
   +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Bucket                            | Name of the bucket to which the multipart upload was initiated                                                                                            |
   |                                   |                                                                                                                                                           |
   |                                   | Type: string                                                                                                                                              |
   |                                   |                                                                                                                                                           |
   |                                   | Ancestor: ListMultipartUploadsResult                                                                                                                      |
   +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------+
   | KeyMarker                         | Object keys at or after which the multipart upload listing begins                                                                                         |
   |                                   |                                                                                                                                                           |
   |                                   | Type: string                                                                                                                                              |
   |                                   |                                                                                                                                                           |
   |                                   | Ancestor: ListMultipartUploadsResult                                                                                                                      |
   +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------+
   | UploadIdMarker                    | Upload ID after which the multipart upload listing begins                                                                                                 |
   |                                   |                                                                                                                                                           |
   |                                   | Type: string                                                                                                                                              |
   |                                   |                                                                                                                                                           |
   |                                   | Ancestor: ListMultipartUploadsResult                                                                                                                      |
   +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------+
   | NextKeyMarker                     | Value of **KeyMarker** in a subsequent request after a multipart upload list is truncated                                                                 |
   |                                   |                                                                                                                                                           |
   |                                   | Type: string                                                                                                                                              |
   |                                   |                                                                                                                                                           |
   |                                   | Ancestor: ListMultipartUploadsResult                                                                                                                      |
   +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------+
   | NextUploadIdMarker                | Value of UploadMarker in a subsequent request after a multipart upload list is truncated                                                                  |
   |                                   |                                                                                                                                                           |
   |                                   | Type: string                                                                                                                                              |
   |                                   |                                                                                                                                                           |
   |                                   | Ancestor: ListMultipartUploadsResult                                                                                                                      |
   +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------+
   | MaxUploads                        | Maximum of multipart uploads to be returned in the response                                                                                               |
   |                                   |                                                                                                                                                           |
   |                                   | Type: integer                                                                                                                                             |
   |                                   |                                                                                                                                                           |
   |                                   | Ancestor: ListMultipartUploadsResult                                                                                                                      |
   +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------+
   | IsTruncated                       | Indicates whether the returned list of multipart uploads is truncated. **true**: Not all results are returned. **false**: All results have been returned. |
   |                                   |                                                                                                                                                           |
   |                                   | Type: boolean                                                                                                                                             |
   |                                   |                                                                                                                                                           |
   |                                   | Ancestor: ListMultipartUploadsResult                                                                                                                      |
   +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Upload                            | Container for elements related to a specific multipart upload                                                                                             |
   |                                   |                                                                                                                                                           |
   |                                   | Type: container                                                                                                                                           |
   |                                   |                                                                                                                                                           |
   |                                   | Children: Key, UploadId, InitiatorOwner, StorageClass, Initiated                                                                                          |
   |                                   |                                                                                                                                                           |
   |                                   | Ancestor: ListMultipartUploadsResult                                                                                                                      |
   +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Key                               | Indicates the name of the object for which a multipart upload is initiated.                                                                               |
   |                                   |                                                                                                                                                           |
   |                                   | Type: string                                                                                                                                              |
   |                                   |                                                                                                                                                           |
   |                                   | Ancestor: Upload                                                                                                                                          |
   +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------+
   | UploadId                          | ID of the multipart upload                                                                                                                                |
   |                                   |                                                                                                                                                           |
   |                                   | Type: string                                                                                                                                              |
   |                                   |                                                                                                                                                           |
   |                                   | Ancestor: Upload                                                                                                                                          |
   +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Initiator                         | Container element that identifies who initiated the multipart upload                                                                                      |
   |                                   |                                                                                                                                                           |
   |                                   | Children: ID                                                                                                                                              |
   |                                   |                                                                                                                                                           |
   |                                   | Type: container                                                                                                                                           |
   |                                   |                                                                                                                                                           |
   |                                   | Ancestor: Upload                                                                                                                                          |
   +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------+
   | ID                                | ID of the account to which the owner belongs.                                                                                                             |
   |                                   |                                                                                                                                                           |
   |                                   | Type: string                                                                                                                                              |
   |                                   |                                                                                                                                                           |
   |                                   | Ancestor: Initiator or Owner                                                                                                                              |
   +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Owner                             | Owner of the part.                                                                                                                                        |
   |                                   |                                                                                                                                                           |
   |                                   | Type: container                                                                                                                                           |
   |                                   |                                                                                                                                                           |
   |                                   | Children: ID                                                                                                                                              |
   |                                   |                                                                                                                                                           |
   |                                   | Ancestor: **Upload**                                                                                                                                      |
   +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------+
   | StorageClass                      | Indicates the storage class that will be used for storing an object when the multipart is uploaded.                                                       |
   |                                   |                                                                                                                                                           |
   |                                   | Type: enumeration                                                                                                                                         |
   |                                   |                                                                                                                                                           |
   |                                   | Ancestor: Upload                                                                                                                                          |
   +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Initiated                         | Date and time when the multipart upload was initiated                                                                                                     |
   |                                   |                                                                                                                                                           |
   |                                   | Type: date                                                                                                                                                |
   |                                   |                                                                                                                                                           |
   |                                   | Ancestor: Upload                                                                                                                                          |
   +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------+
   | ListMultipartUploadsResult.Prefix | Specified prefix in a request.                                                                                                                            |
   |                                   |                                                                                                                                                           |
   |                                   | Type: string                                                                                                                                              |
   |                                   |                                                                                                                                                           |
   |                                   | Ancestor: ListMultipartUploadsResult                                                                                                                      |
   +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Delimiter                         | Delimiter in a request.                                                                                                                                   |
   |                                   |                                                                                                                                                           |
   |                                   | Type: string                                                                                                                                              |
   |                                   |                                                                                                                                                           |
   |                                   | Ancestor: ListMultipartUploadsResult                                                                                                                      |
   +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------+
   | CommonPrefixes                    | Indicates group information. If you specify a delimiter in the request, the response contains group information in **CommonPrefixes**.                    |
   |                                   |                                                                                                                                                           |
   |                                   | Type: container                                                                                                                                           |
   |                                   |                                                                                                                                                           |
   |                                   | Ancestor: ListMultipartUploadsResult                                                                                                                      |
   +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------+
   | CommonPrefixes. Prefix            | Indicates a different prefix in the group information in **CommonPrefixes**.                                                                              |
   |                                   |                                                                                                                                                           |
   |                                   | Type: string                                                                                                                                              |
   |                                   |                                                                                                                                                           |
   |                                   | Ancestor: **CommonPrefixes**                                                                                                                              |
   +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------+

Error Responses
---------------

If the value of **maxUploads** is a non-integer or smaller than 0, OBS returns **400 Bad Request**.

Other errors are included in :ref:`Table 2 <obs_04_0115__d0e843>`.

Sample Request 1
----------------

**List the initialized multipart tasks without any parameter**.

.. code-block:: text

   GET /?uploads HTTP/1.1
   User-Agent: curl/7.29.0
   Host: examplebucket.obs.region.example.com
   Accept: */*
   Date: WED, 01 Jul 2015 04:51:21 GMT
   Authorization: OBS UDSIAMSTUBTEST000008:XdmZgYQ+ZVy1rjxJ9/KpKq+wrU0=

Sample Response 1
-----------------

::

   HTTP/1.1 200 OK
   Server: OBS
   x-obs-request-id: 8DF400000163D405534D046A2295674C
   x-obs-id-2: 32AAAQAAEAABAAAQAAEAABAAAQAAEAABCSDaHP+a+Bp0RI6Mm9XvCOrf7q3qvBQW
   Content-Type: application/xml
   Date: WED, 01 Jul 2015 04:51:21 GMT
   Content-Length: 681

   <?xml version="1.0" encoding="UTF-8" standalone="yes"?>
   <ListMultipartUploadsResult xmlns="http://obs.example.com/doc/2015-06-30/">
     <Bucket>examplebucket</Bucket>
     <KeyMarker/>
     <UploadIdMarker/>
     <Delimiter/>
     <Prefix/>
     <MaxUploads>1000</MaxUploads>
     <IsTruncated>false</IsTruncated>
     <Upload>
       <Key>obj2</Key>
       <UploadId>00000163D40171ED8DF4050919BD02B8</UploadId>
       <Initiator>
         <ID>domainID/b4bf1b36d9ca43d984fbcb9491b6fce9:userID/71f390117351534r88115ea2c26d1999</ID>
       </Initiator>
       <Owner>
         <ID>b4bf1b36d9ca43d984fbcb9491b6fce9</ID>
       </Owner>
       <StorageClass>STANDARD</StorageClass>
       <Initiated>2015-07-01T02:30:54.582Z</Initiated>
     </Upload>
   </ListMultipartUploadsResult>

Sample Request 2
----------------

**List the initialized multipart tasks with the prefix and delimiter**.

The following example describes how to list initialized multipart tasks when there are two multipart tasks in the bucket **examplebucket**, and their object names are **multipart-object001** and **part2-key02**. Set **prefix** to **multipart** and set **delimiter** to **object001**.

.. code-block:: text

   GET /?uploads&delimiter=object001&prefix=multipart HTTP/1.1
   User-Agent: curl/7.29.0
   Host: examplebucket.obs.region.example.com
   Accept: */*
   Date: WED, 01 Jul 2015 04:51:21 GMT
   Authorization: OBS UDSIAMSTUBTEST000008:XdmZgYQ+ZVy1rjxJ9/KpKq+wrU0=

Sample Response 2
-----------------

::

   HTTP/1.1 200 OK
   Server: OBS
   x-obs-request-id: 5DEB00000164A27A1610B8250790D703
   x-obs-id-2: 32AAAQAAEAABAAAQAAEAABAAAQAAEAABCSq3ls2ZtLDD6pQLcJq1yGITXgspSvBR
   Content-Type: application/xml
   Date: WED, 01 Jul 2015 04:51:21 GMT
   Content-Length: 681
   <?xml version="1.0" encoding="UTF-8" standalone="yes"?>
   <ListMultipartUploadsResult xmlns="http://obs.example.com/doc/2015-06-30/">
     <Bucket>newbucket0001</Bucket>
     <KeyMarker></KeyMarker>
     <UploadIdMarker>
     </UploadIdMarker>
     <Delimiter>object</Delimiter>
     <Prefix>multipart</Prefix>
     <MaxUploads>1000</MaxUploads>
     <IsTruncated>false</IsTruncated>
     <CommonPrefixes>
       <Prefix>multipart-object001</Prefix>
     </CommonPrefixes>
   </ListMultipartUploadsResult>
