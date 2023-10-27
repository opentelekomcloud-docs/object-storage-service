:original_name: obs_04_0046.html

.. _obs_04_0046:

Configuring Cross-Region Replication for a Bucket
=================================================

Functions
---------

Cross-region replication refers to the automatic and asynchronous replication of objects across buckets in different regions. By activating cross-region replication, OBS can copy new objects and modified objects from a source bucket in one region to a destination bucket in a different region.

The following two requirements must be met when configuring the cross-region replication for a bucket:

#. Cross-region replication can be configured only when the versioning statuses of the source and destination buckets are the same. For details about how to configure bucket versioning, see :ref:`Configuring Versioning for a Bucket <obs_04_0037>`.
#. The owner and agency (OBS) of the source bucket must have the permission to write the destination bucket (configured with **BucketPolicy**), and the agency (OBS) must have the read permission for the source bucket. This permission delegation needs to be implemented by calling the **BucketPolicy** API.

For details about how to configure the bucket policy, see :ref:`Configuring a Bucket Policy <obs_04_0027>`. After the bucket policy is set, the agency (OBS) can read objects from the source bucket and copy objects to the destination bucket.

Request Syntax
--------------

.. code-block:: text

   PUT /?replication HTTP/1.1
   Host: bucketname.obs.region.example.com
   x-obs-date: date
   Content-MD5: MD5
   Authorization: authorization string
   Content-Length: contentlength

   <ReplicationConfiguration>
       <Agency>testAcy</Agency>
       <Rule>
           <ID>rule1</ID>
           <Prefix>key-prefix</Prefix>
           <Status>rule-status</Status>
           <Destination>
               <Bucket>targetbucketname</Bucket>
               <StorageClass>STANDARD</StorageClass>
               <DeleteData>Enabled</DeleteData>
           </Destination>
           <HistoricalObjectReplication>Enabled</HistoricalObjectReplication>
       </Rule>
   </ReplicationConfiguration>

Request Parameters
------------------

This request contains no message parameters.

Request Headers
---------------

The request uses one header, as described in the following table.

.. table:: **Table 1** Request header for cross-region replication

   +-------------+-------------------------------------------------------------------------+-----------+
   | Element     | Description                                                             | Mandatory |
   +=============+=========================================================================+===========+
   | Content-MD5 | Base64-encoded 128-bit MD5 digest of the message according to RFC 1864. | Yes       |
   +-------------+-------------------------------------------------------------------------+-----------+

Request Elements
----------------

This request contains elements to specify the replication configuration for the bucket in XML format. The following table lists request elements:

.. table:: **Table 2** Bucket replication configuration elements

   +-----------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
   | Element                     | Description                                                                                                                                                                | Mandatory             |
   +=============================+============================================================================================================================================================================+=======================+
   | ReplicationConfiguration    | Container for the replication rules. A maximum of 100 rules can be configured. The size of the XML file can reach 50 KB.                                                   | Yes                   |
   |                             |                                                                                                                                                                            |                       |
   |                             | Type: container                                                                                                                                                            |                       |
   |                             |                                                                                                                                                                            |                       |
   |                             | Children: Rule                                                                                                                                                             |                       |
   |                             |                                                                                                                                                                            |                       |
   |                             | Ancestor: none                                                                                                                                                             |                       |
   +-----------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
   | Agency                      | Name of the agency, which can have a maximum of 64 characters.                                                                                                             | Yes                   |
   |                             |                                                                                                                                                                            |                       |
   |                             | Type: string                                                                                                                                                               |                       |
   |                             |                                                                                                                                                                            |                       |
   |                             | Ancestor: ReplicationConfiguration                                                                                                                                         |                       |
   +-----------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
   | Rule                        | Container of a specified replication rule.                                                                                                                                 | Yes                   |
   |                             |                                                                                                                                                                            |                       |
   |                             | The replication configuration must contain at least one rule. The maximum number of rules is 100.                                                                          |                       |
   |                             |                                                                                                                                                                            |                       |
   |                             | Type: container                                                                                                                                                            |                       |
   |                             |                                                                                                                                                                            |                       |
   |                             | Ancestor:                                                                                                                                                                  |                       |
   |                             |                                                                                                                                                                            |                       |
   |                             | ReplicationConfiguration                                                                                                                                                   |                       |
   +-----------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
   | ID                          | Unique identifier of a rule, with a maximum length of 255 characters.                                                                                                      | No                    |
   |                             |                                                                                                                                                                            |                       |
   |                             | Type: string                                                                                                                                                               |                       |
   |                             |                                                                                                                                                                            |                       |
   |                             | Ancestor: Rule                                                                                                                                                             |                       |
   +-----------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
   | Status                      | If the value of this element is **Disabled**, this rule will be ignored.                                                                                                   | Yes                   |
   |                             |                                                                                                                                                                            |                       |
   |                             | Type: string                                                                                                                                                               |                       |
   |                             |                                                                                                                                                                            |                       |
   |                             | Ancestor: Rule                                                                                                                                                             |                       |
   |                             |                                                                                                                                                                            |                       |
   |                             | Value options: **Enabled**, **Disabled**                                                                                                                                   |                       |
   +-----------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
   | Prefix                      | Prefix of an object key name, applicable to one or more objects. If the **Prefix** is left blank, the cross-region replication rule is applied to the whole bucket.        | Yes                   |
   |                             |                                                                                                                                                                            |                       |
   |                             | The maximum length of a prefix is 1024 characters. Duplicated prefixes are not supported.                                                                                  |                       |
   |                             |                                                                                                                                                                            |                       |
   |                             | Type: string                                                                                                                                                               |                       |
   |                             |                                                                                                                                                                            |                       |
   |                             | Ancestor: Rule                                                                                                                                                             |                       |
   +-----------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
   | Destination                 | Container for the destination bucket information.                                                                                                                          | Yes                   |
   |                             |                                                                                                                                                                            |                       |
   |                             | Type: container                                                                                                                                                            |                       |
   |                             |                                                                                                                                                                            |                       |
   |                             | Ancestor: Rule                                                                                                                                                             |                       |
   +-----------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
   | Bucket                      | Bucket used to store object copies that are marked by rules.                                                                                                               | Yes                   |
   |                             |                                                                                                                                                                            |                       |
   |                             | If the replication configuration contains multiple rules, the rules must specify the same bucket as the destination bucket.                                                |                       |
   |                             |                                                                                                                                                                            |                       |
   |                             | Type: string                                                                                                                                                               |                       |
   |                             |                                                                                                                                                                            |                       |
   |                             | Ancestor: Destination                                                                                                                                                      |                       |
   +-----------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
   | StorageClass                | Storage class of an object                                                                                                                                                 | No                    |
   |                             |                                                                                                                                                                            |                       |
   |                             | Type: string                                                                                                                                                               |                       |
   |                             |                                                                                                                                                                            |                       |
   |                             | Ancestor: Destination                                                                                                                                                      |                       |
   |                             |                                                                                                                                                                            |                       |
   |                             | Value options: **STANDARD**, **WARM**, **COLD**                                                                                                                            |                       |
   +-----------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
   | DeleteData                  | Keyword for synchronizing object deletion operations. If the value is **Enabled**, the object deletion for the source bucket will be replicated to the destination bucket. | No                    |
   |                             |                                                                                                                                                                            |                       |
   |                             | Type: string                                                                                                                                                               |                       |
   |                             |                                                                                                                                                                            |                       |
   |                             | Ancestor: Destination                                                                                                                                                      |                       |
   |                             |                                                                                                                                                                            |                       |
   |                             | Value options: **Enabled** and **Disabled** (If this element is absent from the request, **Disabled** is applied by default.)                                              |                       |
   +-----------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
   | HistoricalObjectReplication | Keyword for copying a historical object. If the value is **Enabled**, historical objects meeting this rule are copied.                                                     | No                    |
   |                             |                                                                                                                                                                            |                       |
   |                             | Type: string                                                                                                                                                               |                       |
   |                             |                                                                                                                                                                            |                       |
   |                             | Ancestor: Rule                                                                                                                                                             |                       |
   |                             |                                                                                                                                                                            |                       |
   |                             | Value options: **Enabled** and **Disabled** (If this element is absent from the request, **Disabled** is applied by default.)                                              |                       |
   +-----------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+

Response Syntax
---------------

::

   HTTP/1.1 status_code
   Server: OBS
   Date:date
   Content-Length: contentlength

Response Headers
----------------

The response to the request uses common headers. For details, see :ref:`Table 1 <obs_04_0013__d0e686>`.

Response Elements
-----------------

This response contains no elements.

Error Responses
---------------

No special error responses are returned for this request.

Sample Request
--------------

.. code-block:: text

   PUT /?replication HTTP/1.1
   User-Agent: curl/7.29.0
   Host: examplebucket.obs.region.example.com
   Accept: */*
   Date: Wed, 27 Jun 2018 13:39:15 +0000
   Authorization: OBS H4IPJX0TQTHTHEBQQCEC:CdeqU0Vg9xNdJMZ0PGPgh5EnkO0=
   Content-MD5: l/Z8mfSX+VyV8k5EhIQz5Q==
   Content-Length: 330

   <ReplicationConfiguration>
      <Agency>testAcy</Agency>
      <Rule>
          <ID>Rule-1</ID>
          <Status>Enabled</Status>
          <Prefix></Prefix>
          <Destination>
             <Bucket>dstbucket</Bucket>
             <StorageClass>STANDARD</StorageClass>
             <DeleteData>Enabled</DeleteData>
          </Destination>
          <HistoricalObjectReplication>Enabled</HistoricalObjectReplication>
        </Rule>
   </ReplicationConfiguration>

Sample Response
---------------

::

   HTTP/1.1 200 OK
   Server: OBS
   x-obs-request-id: B59500000164417839932E5A2295674C
   x-obs-id-2: 32AAAQAAEAABKAAQAAEAABAAAQAAEAABCStv51t2NMMx+Ou+ow7IWV4Sxo231fKe
   Date: Wed, 27 Jun 2018 13:39:15 GMT
   Content-Length: 0
