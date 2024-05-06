:original_name: en-us_topic_0000001684183953.html

.. _en-us_topic_0000001684183953:

PUT Bucket Replication
======================

Cross-region replication refers to the automatic and asynchronous replication of objects across buckets in different regions. By enabling cross-region replication, OBS can copy newly uploaded objects and object updates from a source bucket to a destination bucket in a different region.

The following two requirements must be met when configuring the cross-region replication for a bucket:

#. Cross-region replication can be configured only when the versioning statuses of the source bucket and the destination bucket are the same. You can find more information about how to configure versioning in the section :ref:`PUT Bucket versioning <en-us_topic_0125560444>`.
#. The owner and agency (OBS) of the source bucket must have the permission to write the destination bucket (configured with the bucket policy), and the agency (OBS) must have the permission to read the source bucket. This permission delegation needs to be implemented by calling the **BucketPolicy** API.

For details about how to set a bucket policy, see the section :ref:`PUT Bucket policy <en-us_topic_0125560316>`. After the bucket policy is set, the agency (OBS) can read objects in the source bucket and copy objects to the destination bucket.

Request Syntax
--------------

.. code-block:: text

   PUT /?replication HTTP/1.1
   Host: bucketname.obs.region.example.com
   x-amz-date: date
   Content-MD5: content-MD5
   Authorization: authorization string
   Content-Length: contentlength
   <ReplicationConfiguration>
        <Rule>
           <ID>rule1</ID>
           <Prefix>key-prefix</Prefix>
           <Status>rule-status</Status>
           <Prefix>key-prefix</Prefix>
           <Destination>
              <Bucket>arn:aws:s3:::targetbucketname</Bucket>
              <StorageClass>GLACIER</StorageClass>
              <DeleteData>Enabled</DeleteData>
           </Destination>
           <HistoricalObjectReplication>Enabled</HistoricalObjectReplication>
        </Rule>
   </ReplicationConfiguration>

Request Parameters
------------------

This request contains no parameter.

Request Headers
---------------

The request uses one header, as described in the following table.

Request header for cross-region replication

+-------------+------------------------------------------------------------------------+-----------+
| Parameter   | Description                                                            | Mandatory |
+=============+========================================================================+===========+
| Content-MD5 | Base64-encoded 128-bit MD5 digest of the message according to RFC 1864 | Yes       |
+-------------+------------------------------------------------------------------------+-----------+

Request Elements
----------------

This request contains elements to specify the replication configuration for the bucket in XML format. The following table lists the request elements:

Bucket replication configuration elements

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
| Agency                      | Name of the agency with a maximum length of 64 characters.                                                                                                                 | Yes                   |
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
| Prefix                      | Prefix of an object key name, applicable to one or more objects.If the Prefix is left blank, the cross-region replication rule is applied to the whole bucket.             | Yes                   |
|                             |                                                                                                                                                                            |                       |
|                             | The maximum length of a prefix is 1,024 characters. Duplicated prefixes are not supported.                                                                                 |                       |
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
| StorageClass                | Storage class of an object.                                                                                                                                                | No                    |
|                             |                                                                                                                                                                            |                       |
|                             | Type: enumeration                                                                                                                                                          |                       |
|                             |                                                                                                                                                                            |                       |
|                             | Ancestor: Destination                                                                                                                                                      |                       |
|                             |                                                                                                                                                                            |                       |
|                             | Value options: **STANDARD, STANDARD_IA, GLACIER**                                                                                                                          |                       |
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

.. code-block::

   HTTP/1.1 status_code
   Server: OBS
   x-amz-id-2:id
   x-amz-request-id:id
   Date:date
   Content-Length: contentlength

Response Headers
----------------

This response uses common headers. For details about common response headers, see the section :ref:`Common Response Headers <en-us_topic_0125560484>`.

Response Elements
-----------------

This response involves no elements.

Error Responses
---------------

No special error responses are returned. For details about error responses, see :ref:`Table 1 <en-us_topic_0125560440__table30733758>`.

Sample Request
--------------

.. code-block:: text

   PUT /?replication HTTP/1.1
   Host: examplebucket.obs.region.example.com
   x-amz-date: Wed, 11 Feb 2015 02:11:21 GMT
   Content-MD5: q6yJDlIkcBaGGfb3QLY69A==
   Authorization: authorization string
   Content-Length: 406

   <ReplicationConfiguration>
    <Agency>testAcy</Agency>
    <Rule>
          <ID>Rule-1</ID>
          <Status>Enabled</Status>
          <Prefix></Prefix>
          <Destination>
             <Bucket>arn:aws:s3:::dstbucket</Bucket>
             <StorageClass>STANDARD</StorageClass>
          </Destination>
        </Rule>
   </ReplicationConfiguration>

Sample Response
---------------

.. code-block::

   HTTP/1.1 200 OK
   Server: OBS
   x-amz-id-2: r+qR7+nhXtJDDIJ0JJYcd+1j5nM/rUFiiiZ/fNbDOsd3JUE8NWMLNHXmvPfwMpdc
   x-amz-request-id: 9E26D08072A8EF9E
   Date: Wed, 11 Feb 2015 02:11:22 GMT
   Content-Length: 0
