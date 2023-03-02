:original_name: obs_04_0021.html

.. _obs_04_0021:

Creating a Bucket
=================

Functions
---------

This operation is used to create a bucket with a specified name.

.. note::

   -  By default, a user can have a maximum of 100 buckets.
   -  The name of a deleted bucket can be reused for a bucket or a parallel file system at least 30 minutes after the deletion.

A bucket name must be unique in OBS. If a user creates a bucket with the same name as that of an existing bucket under the same account and in the same region, a 200 code (indicating success) is returned. In scenarios other than the preceding one, the request for creating a bucket with the same name as that of an existing one will receive the 409 code (indicating that a namesake bucket already exists). To set an access control policy for the bucket to be created, you can add the **x-obs-acl** parameter to request headers.

Storage Class
-------------

You can create buckets with different storage classes. The **x-obs-storage-class** header in a bucket creation request specifies the storage class for a bucket. If you do not specify a storage class when you upload an object to the bucket, the object inherits the storage class of the bucket. There are three storage classes: STANDARD (Standard storage class), WARM (Warm storage class), and COLD (Cold storage class) If this header is not in the request, the storage class of the created bucket is Standard.

If the storage class of an object is not specified when it is uploaded to a bucket (see :ref:`Uploading Objects - PUT <obs_04_0080>`), the object will be stored in the default storage class of the bucket.

-  OBS Standard features low access latency and high throughput. It is most suitable for storing frequently accessed (multiple times per month) hot files. Potential application scenarios include big data, mobile applications, trending videos, and social media images.
-  OBS Warm storage class is suitable for storing data that is infrequently accessed (less than 12 times a year) yet has quick response requirements. Potential application scenarios include file synchronization or sharing and enterprise backup. It provides the same durability, access latency, and throughput as the Standard storage class but at a lower price. However, the Warm storage class has lower availability than the Standard one.
-  OBS Cold storage class is applicable to archiving rarely-accessed (averagely once a year) data. The application scenarios include data archiving and long-term data retention for backup. The Cold storage class is secure, durable, and inexpensive, which can replace tape libraries. To keep cost low, it may take hours to restore data from the Cold storage class.

Request Syntax
--------------

.. code-block:: text

   PUT / HTTP/1.1
   Host: bucketname.obs.region.example.com
   Content-Length: length
   Date: date
   Authorization: authorization

   <CreateBucketConfiguration xmlns="http://obs.region.example.com/doc/2015-06-30/">
       <Location>location</Location>
   </CreateBucketConfiguration>

Request Parameters
------------------

This request contains no parameters.

Request Headers
---------------

The operation message header is the same as that of a common request. For details, see :ref:`Table 3 <obs_04_0007__table25197309>`. However, this request can contain additional headers. The following table describes the additional headers for this request.

.. table:: **Table 1** Additional request headers

   +------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
   | Header                             | Description                                                                                                                                                                                                                                                                                                                         | Mandatory             |
   +====================================+=====================================================================================================================================================================================================================================================================================================================================+=======================+
   | x-obs-acl                          | When creating a bucket, you can add this header to set the permission control policy for the bucket. The predefined common policies are as follows: **private**, **public-read**, **public-read-write**, **public-read-delivered**, and **public-read-write-delivered**.                                                            | No                    |
   |                                    |                                                                                                                                                                                                                                                                                                                                     |                       |
   |                                    | Type: string                                                                                                                                                                                                                                                                                                                        |                       |
   +------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
   | x-obs-storage-class                | When creating a bucket, you can add this header to set the default storage class of the bucket. The default storage classes are as follows: STANDARD (Standard storage class), WARM (Warm storage class), and COLD (Cold storage class). If this header is not in the request, the storage class of the bucket created is Standard. | No                    |
   |                                    |                                                                                                                                                                                                                                                                                                                                     |                       |
   |                                    | Type: string                                                                                                                                                                                                                                                                                                                        |                       |
   +------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
   | x-obs-grant-read                   | This header grants the read permission to all users under an account. It allows you to list objects in a bucket, list multipart tasks in a bucket, list multi-version objects in a bucket, and obtain bucket metadata.                                                                                                              | No                    |
   |                                    |                                                                                                                                                                                                                                                                                                                                     |                       |
   |                                    | Type: string                                                                                                                                                                                                                                                                                                                        |                       |
   |                                    |                                                                                                                                                                                                                                                                                                                                     |                       |
   |                                    | Example: **x-obs-grant-read:id=Tenant ID**.                                                                                                                                                                                                                                                                                         |                       |
   +------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
   | x-obs-grant-write                  | This header grants the write permission to all users under an account. Therefore, the users can create, delete, and overwrite all objects in a bucket, and can initialize parts, upload parts, copy parts, merge parts, and cancel multipart upload tasks.                                                                          | No                    |
   |                                    |                                                                                                                                                                                                                                                                                                                                     |                       |
   |                                    | Type: string                                                                                                                                                                                                                                                                                                                        |                       |
   |                                    |                                                                                                                                                                                                                                                                                                                                     |                       |
   |                                    | Example: **x-obs-grant-write:id=Tenant ID**.                                                                                                                                                                                                                                                                                        |                       |
   +------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
   | x-obs-grant-read-acp               | This header grants the ACL read permission to all users under an account. Therefore, the users can read the bucket ACL information.                                                                                                                                                                                                 | No                    |
   |                                    |                                                                                                                                                                                                                                                                                                                                     |                       |
   |                                    | Type: string                                                                                                                                                                                                                                                                                                                        |                       |
   |                                    |                                                                                                                                                                                                                                                                                                                                     |                       |
   |                                    | Example: **x-obs-grant-read-acp:id=Account ID**.                                                                                                                                                                                                                                                                                    |                       |
   +------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
   | x-obs-grant-write-acp              | This header grants the ACL write permission to all users under an account. Therefore, the users can modify the ACL of the bucket.                                                                                                                                                                                                   | No                    |
   |                                    |                                                                                                                                                                                                                                                                                                                                     |                       |
   |                                    | Type: string                                                                                                                                                                                                                                                                                                                        |                       |
   |                                    |                                                                                                                                                                                                                                                                                                                                     |                       |
   |                                    | Example: **x-obs-grant-write-acp:id=Account ID**.                                                                                                                                                                                                                                                                                   |                       |
   +------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
   | x-obs-grant-full-control           | This header grants the full control permission to all users under an account.                                                                                                                                                                                                                                                       | No                    |
   |                                    |                                                                                                                                                                                                                                                                                                                                     |                       |
   |                                    | Type: string                                                                                                                                                                                                                                                                                                                        |                       |
   |                                    |                                                                                                                                                                                                                                                                                                                                     |                       |
   |                                    | Example: **x-obs-grant-full-control:id=Account ID**.                                                                                                                                                                                                                                                                                |                       |
   +------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
   | x-obs-grant-read-delivered         | This header grants the read permission to all users under an account. By default, the read permission is applied to all objects in the bucket.                                                                                                                                                                                      | No                    |
   |                                    |                                                                                                                                                                                                                                                                                                                                     |                       |
   |                                    | Type: string                                                                                                                                                                                                                                                                                                                        |                       |
   |                                    |                                                                                                                                                                                                                                                                                                                                     |                       |
   |                                    | Example: **x-obs-grant-read-delivered:id=Account ID**.                                                                                                                                                                                                                                                                              |                       |
   +------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
   | x-obs-grant-full-control-delivered | This header grants the full control permission to all users under an account. By default, the FULL_CONTROL permission is applied to all objects in the bucket.                                                                                                                                                                      | No                    |
   |                                    |                                                                                                                                                                                                                                                                                                                                     |                       |
   |                                    | Type: string                                                                                                                                                                                                                                                                                                                        |                       |
   |                                    |                                                                                                                                                                                                                                                                                                                                     |                       |
   |                                    | Example: **x-obs-grant-full-control-delivered:id=Account ID**.                                                                                                                                                                                                                                                                      |                       |
   +------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
   | x-obs-fs-file-interface            | This header can be carried when you create a bucket as a parallel file system.                                                                                                                                                                                                                                                      | No                    |
   |                                    |                                                                                                                                                                                                                                                                                                                                     |                       |
   |                                    | Type: string                                                                                                                                                                                                                                                                                                                        |                       |
   |                                    |                                                                                                                                                                                                                                                                                                                                     |                       |
   |                                    | Example: **x-obs-fs-file-interface:Enabled**                                                                                                                                                                                                                                                                                        |                       |
   +------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+

Request Elements
----------------

This request can use additional elements. For details about additional elements, see :ref:`Table 2 <obs_04_0021__table19762527>`.

.. _obs_04_0021__table19762527:

.. table:: **Table 2** Additional request elements

   +-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
   | Element               | Description                                                                                                                                       | Mandatory             |
   +=======================+===================================================================================================================================================+=======================+
   | Location              | Specifies the region where a bucket will be created.                                                                                              | No                    |
   |                       |                                                                                                                                                   |                       |
   |                       | -  When creating a bucket using the endpoint of the default region, note the following:                                                           |                       |
   |                       |                                                                                                                                                   |                       |
   |                       |    -  If **Location** is not specified, the bucket is created in the default region.                                                              |                       |
   |                       |    -  If Location is specified to other region, the bucket is created in the specified region.                                                    |                       |
   |                       |                                                                                                                                                   |                       |
   |                       | -  When creating a bucket using the endpoint of a non-default region, **Location** must be specified to the region corresponding to the endpoint. |                       |
   |                       |                                                                                                                                                   |                       |
   |                       | For details about OBS regions and endpoints, see `Regions and Endpoints <https://docs.otc.t-systems.com/en-us/endpoint/index.html>`__.            |                       |
   |                       |                                                                                                                                                   |                       |
   |                       | Type: string                                                                                                                                      |                       |
   +-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+

Response Syntax
---------------

::

   HTTP/1.1 status_code
   Location: location
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

No special error responses are returned. For details about error responses, see :ref:`Table 2 <obs_04_0115__d0e843>`.

Sample Request 1
----------------

Create a bucket.

.. code-block:: text

   PUT / HTTP/1.1
   User-Agent: curl/7.29.0
   Host: examplebucket.obs.region.example.com
   Accept: */*
   Date: WED, 01 Jul 2015 02:25:05 GMT
   Authorization: OBS H4IPJX0TQTHTHEBQQCEC:75/Y4Ng1izvzc1nTGxpMXTE6ynw=
   Content-Length: 157

   <CreateBucketConfiguration xmlns="http://obs.region.example.com/doc/2015-06-30/">
       <Location>region</Location>
   </CreateBucketConfiguration>

Sample Response 1
-----------------

::

   HTTP/1.1 200 OK
   Server: OBS
   x-obs-request-id: BF260000016435CE298386946AE4C482
   Location: /examplebucket
   x-obs-id-2: 32AAAQAAEAABSAAgAAEAABAAAQAAEAABCT9W2tcvLmMJ+plfdopaD62S0npbaRUz
   Date: WED, 01 Jul 2015 02:25:06 GMT
   Content-Length: 0

Sample Request 2
----------------

Create a bucket with a specified ACL and storage class.

.. code-block:: text

   PUT / HTTP/1.1
   User-Agent: curl/7.29.0
   Host: examplebucket.obs.region.example.com
   Accept: */*
   Date: WED, 01 Jul 2015 02:25:05 GMT
   x-obs-acl:public-read
   x-obs-storage-class:STANDARD
   Authorization: OBS H4IPJX0TQTHTHEBQQCEC:75/Y4Ng1izvzc1nTGxpMXTE6ynw=
   Content-Length: 157

   <CreateBucketConfiguration xmlns="http://obs.region.example.com/doc/2015-06-30/">
       <Location>region</Location>
   </CreateBucketConfiguration>

Sample Response 2
-----------------

::

   HTTP/1.1 200 OK
   Server: OBS
   x-obs-request-id: BF260000016435CE298386946AE4C482
   Location: /examplebucket
   x-obs-id-2: 32AAAQAAEAABSAAgAAEAABAAAQAAEAABCT9W2tcvLmMJ+plfdopaD62S0npbaRUz
   Date: WED, 01 Jul 2015 02:25:06 GMT
   Content-Length: 0

.. _obs_04_0021__section4293341135610:

Sample Request 4
----------------

Create a parallel file system.

.. code-block:: text

   PUT / HTTP/1.1
   User-Agent: curl/7.29.0
   Host: examplebucket.obs.region.example.com
   Accept: */*
   Date: WED, 01 Jul 2015 02:25:05 GMT
   Authorization: OBS H4IPJX0TQTHTHEBQQCEC:75/Y4Ng1izvzc1nTGxpMXTE6ynw=
   Content-Length: 157
   x-obs-fs-file-interface: Enabled

   <CreateBucketConfiguration xmlns="http://obs.region.example.com/doc/2015-06-30/">
   <Location>region</Location>
   </CreateBucketConfiguration>

Sample Response 4
-----------------

::

   HTTP/1.1 200 OK
   Server: OBS
   x-obs-request-id: BF260000016435CE298386946AE4C482
   Location: /examplebucket
   x-obs-id-2: 32AAAQAAEAABSAAgAAEAABAAAQAAEAABCT9W2tcvLmMJ+plfdopaD62S0npbaRUz
   Date: WED, 01 Jul 2015 02:25:06 GMT
   Content-Length: 0
