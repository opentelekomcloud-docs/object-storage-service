:original_name: obs_04_0037.html

.. _obs_04_0037:

Configuring Versioning for a Bucket
===================================

Functions
---------

This operation restores an object that is mistakenly overwritten or deleted. You can use versioning to save, query, and restore objects of different versions. Versioning allows you to easily recover lost data due to misoperations or program faults. Versioning can also be used for retaining and archiving data.

By default, versioning is disabled for a bucket.

You can perform this operation to enable or suspend versioning for a bucket.

After versioning is enabled for a bucket:

-  OBS creates a unique version ID for each uploaded object. Namesake objects are not overwritten and are distinguished by their own version IDs.
-  You can download objects by specifying version IDs. By default, the latest object is downloaded if the version ID is not specified.
-  Objects can be deleted by version ID. If an object is deleted with no version ID specified, the object is only attached with a deletion marker and a unique version ID but is not physically deleted.
-  The latest objects in a bucket are returned by default after a GET Object request. You can also send a request to obtain a bucket's objects with all version IDs.
-  Except deletion markers and object metadata, storage space occupied by objects with all version IDs is charged.

After versioning is suspended for a bucket:

-  Existing objects with version IDs are not affected.
-  The system creates version ID **null** to an uploaded object and the object will be overwritten after a namesake one is uploaded.
-  You can download objects by specifying version IDs. By default, the latest object is downloaded if the version ID is not specified.
-  Objects can be deleted by version ID. If an object is deleted with no version ID specified, the object is attached with a deletion marker whose version ID is **null**. The object with version ID **null** is physically deleted.
-  Except deletion markers and object metadata, storage space occupied by objects with all version IDs is charged.

Only the bucket owner can set versioning for the bucket.

Request Syntax
--------------

.. code-block:: text

   PUT /?versioning HTTP/1.1
   Host: bucketname.obs.region.example.com
   Date: date
   Authorization: authorization
   Content-Length: length

   <VersioningConfiguration>
       <Status>status</Status>
   </VersioningConfiguration>

Request Parameters
------------------

This request contains no parameter.

Request Headers
---------------

This request uses common headers. For details, see :ref:`Table 3 <obs_04_0007__table25197309>`.

Request Elements
----------------

This request contains elements to configure the bucket versioning in XML format. :ref:`Table 1 <obs_04_0037__d0e7246>` lists the request elements.

.. _obs_04_0037__d0e7246:

.. table:: **Table 1** Elements for configuring bucket versioning

   +-------------------------+----------------------------------------+-----------------------+
   | Element                 | Description                            | Mandatory             |
   +=========================+========================================+=======================+
   | VersioningConfiguration | Root node for configuring versioning   | Yes                   |
   |                         |                                        |                       |
   |                         | Ancestor node: none                    |                       |
   +-------------------------+----------------------------------------+-----------------------+
   | Status                  | Versioning status of the bucket        | Yes                   |
   |                         |                                        |                       |
   |                         | Type: enumeration                      |                       |
   |                         |                                        |                       |
   |                         | Ancestor node: VersioningConfiguration |                       |
   |                         |                                        |                       |
   |                         | Value options: Enabled, Suspended      |                       |
   +-------------------------+----------------------------------------+-----------------------+

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

No special error responses are involved. For details about error responses, see :ref:`Table 2 <obs_04_0115__d0e843>`.

Sample Request
--------------

.. code-block:: text

   PUT /?versioning HTTP/1.1
   User-Agent: curl/7.29.0
   Host: examplebucket.obs.region.example.com
   Accept: */*
   Date: WED, 01 Jul 2015 03:14:18 GMT
   Authorization: OBS H4IPJX0TQTHTHEBQQCEC:sc2PM13Wlfcoc/YZLK0MwsI2Zpo=
   Content-Length: 89

   <VersioningConfiguration>
       <Status>Enabled</Status>
   </VersioningConfiguration>

Sample Response
---------------

::

   HTTP/1.1 200 OK
   Server: OBS
   x-obs-request-id: BF26000001643672B973EEBC5FBBF909
   x-obs-id-2: 32AAAQAAEAABSAAgAAEAABAAAQAAEAABCSH6rPRHjQCa62fcNpCCPs7+1Aq/hKzE
   Date: Date: WED, 01 Jul 2015 03:14:18 GMT
   Content-Length: 0
