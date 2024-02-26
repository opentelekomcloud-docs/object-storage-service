:original_name: en-us_topic_0000001635744308.html

.. _en-us_topic_0000001635744308:

GET Bucket Replication
======================

This operation obtains the replication configuration information of a specified bucket. Only users have the **s3:GetReplicationConfiguration** permission can perform this operation.

Request Syntax
--------------

.. code-block:: text

   GET /?replication HTTP/1.1
   Host: bucketname.obs.region.example.com
   Date: date
   Authorization:authorization string

Request Parameters
------------------

This request contains no parameter.

Request Headers
---------------

This request uses common headers. For details about common request headers, see the section :ref:`Common Request Headers <en-us_topic_0125560462>`.

Request Elements
----------------

This request involves no elements.

Response Syntax
---------------

.. code-block::

   HTTP/1.1 status_code
   x-amz-id-2: id
   x-amz-request-id:id
   Date: date
   Server:OBS
   Content-Length: contentlength
   <?xml version="1.0" encoding="UTF-8"?>
   <ReplicationConfiguration xmlns="http://obs.example.com/doc/2006-03-01/">
     <Rule>
         <ID>rule1</ID>
         <Status>Enabled</Status>
         <Prefix></Prefix>
         <Destination>
            <Bucket>arn:aws:s3:::exampletargetbucket</Bucket>
            <StorageClass>GLACIER</StorageClass>
            <DeleteData>Enabled</DeleteData>
         </Destination>
         <HistoricalObjectReplication>Enabled</HistoricalObjectReplication>
     </Rule>
     <Agency>testAgency</Agency>
   </ReplicationConfiguration>

Response Headers
----------------

This response uses common headers. For details about common response headers, see the section :ref:`Common Response Headers <en-us_topic_0125560484>`.

Response Elements
-----------------

This response contains elements to detail the configuration. The following table describes the elements.

Bucket replication configuration elements

+-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| Element                           | Description                                                                                                                                                                |
+===================================+============================================================================================================================================================================+
| ReplicationConfiguration          | Container for the replication rules. A maximum of 100 rules can be configured. The size of the XML file can reach 50 KB.                                                   |
|                                   |                                                                                                                                                                            |
|                                   | Type: container                                                                                                                                                            |
|                                   |                                                                                                                                                                            |
|                                   | Children: Rule                                                                                                                                                             |
|                                   |                                                                                                                                                                            |
|                                   | Ancestor: none                                                                                                                                                             |
+-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| Agency                            | Name of the agency, which can have a maximum of 64 characters.                                                                                                             |
|                                   |                                                                                                                                                                            |
|                                   | Type: string                                                                                                                                                               |
|                                   |                                                                                                                                                                            |
|                                   | Ancestor: ReplicationConfiguration                                                                                                                                         |
+-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| Rule                              | Container of a specified replication rule.                                                                                                                                 |
|                                   |                                                                                                                                                                            |
|                                   | The replication configuration must contain at least one rule. The maximum number of rules is 100.                                                                          |
|                                   |                                                                                                                                                                            |
|                                   | Type: container                                                                                                                                                            |
|                                   |                                                                                                                                                                            |
|                                   | Ancestor: ReplicationConfiguration                                                                                                                                         |
+-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| ID                                | Unique identifier of a rule, with a maximum length of 255 characters.                                                                                                      |
|                                   |                                                                                                                                                                            |
|                                   | Type: string                                                                                                                                                               |
|                                   |                                                                                                                                                                            |
|                                   | Ancestor: Rule                                                                                                                                                             |
+-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| Status                            | If the value of this element is **Disabled**, this rule will be ignored.                                                                                                   |
|                                   |                                                                                                                                                                            |
|                                   | Type: string                                                                                                                                                               |
|                                   |                                                                                                                                                                            |
|                                   | Ancestor: Rule                                                                                                                                                             |
|                                   |                                                                                                                                                                            |
|                                   | Value options: **Enabled**, **Disabled**                                                                                                                                   |
+-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| Prefix                            | Prefix of an object key name, applicable to one or more objects.If the Prefix is left blank, the cross-region replication rule is applied to the whole bucket.             |
|                                   |                                                                                                                                                                            |
|                                   | The maximum length of a prefix is 1,024 characters. Duplicated prefixes are not supported.                                                                                 |
|                                   |                                                                                                                                                                            |
|                                   | Type: string                                                                                                                                                               |
|                                   |                                                                                                                                                                            |
|                                   | Ancestor: Rule                                                                                                                                                             |
+-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| Destination                       | Container for the destination bucket information.                                                                                                                          |
|                                   |                                                                                                                                                                            |
|                                   | Type: container                                                                                                                                                            |
|                                   |                                                                                                                                                                            |
|                                   | Ancestor: Rule                                                                                                                                                             |
+-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| Bucket                            | Bucket used to store object copies that are marked by rules.                                                                                                               |
|                                   |                                                                                                                                                                            |
|                                   | If the replication configuration contains multiple rules, the rules must specify the same bucket as the destination bucket.                                                |
|                                   |                                                                                                                                                                            |
|                                   | Type: string                                                                                                                                                               |
|                                   |                                                                                                                                                                            |
|                                   | Ancestor: Destination                                                                                                                                                      |
+-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| StorageClass                      | Storage class of an object.                                                                                                                                                |
|                                   |                                                                                                                                                                            |
|                                   | Type: enumeration                                                                                                                                                          |
|                                   |                                                                                                                                                                            |
|                                   | Ancestor: Destination                                                                                                                                                      |
|                                   |                                                                                                                                                                            |
|                                   | Value options: **STANDARD, STANDARD_IA, GLACIER**                                                                                                                          |
+-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| DeleteData                        | Keyword for synchronizing object deletion operations. If the value is **Enabled**, the object deletion for the source bucket will be replicated to the destination bucket. |
|                                   |                                                                                                                                                                            |
|                                   | Type: string                                                                                                                                                               |
|                                   |                                                                                                                                                                            |
|                                   | Ancestor: Destination                                                                                                                                                      |
|                                   |                                                                                                                                                                            |
|                                   | Value options: **Enabled** and **Disabled** (If this element is absent from the request, **Disabled** is applied by default.)                                              |
+-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| HistoricalObjectReplication       | Keyword for copying a historical object. If the value is **Enabled**, historical objects meeting this rule are copied.                                                     |
|                                   |                                                                                                                                                                            |
|                                   | Type: string                                                                                                                                                               |
|                                   |                                                                                                                                                                            |
|                                   | Ancestor: Rule                                                                                                                                                             |
|                                   |                                                                                                                                                                            |
|                                   | Value options: **Enabled** and **Disabled** (If this element is absent from the request, **Disabled** is applied by default.)                                              |
+-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Error Responses
---------------

The following table describes the error response for this request.

Error response elements

+--------------------------------+--------------------------------------------------------+--------------------+------------------------+
| Error Code                     | Description                                            | HTTP Response Code | SOAP Error Code Prefix |
+================================+========================================================+====================+========================+
| NoSuchReplicationConfiguration | Cross-region replication configuration does not exist. | 404 not found      | Client                 |
+--------------------------------+--------------------------------------------------------+--------------------+------------------------+

Sample Request
--------------

.. code-block:: text

   GET /?replication HTTP/1.1
   Host: examplebucket.obs.region.example.com
   x-amz-date: Tue, 10 Feb 2015 00:17:21 GMT
   Authorization: signatureValue

Sample Response
---------------

.. code-block::

   HTTP/1.1 200 OK
   x-amz-id-2: ITnGT1y4RyTmXa3rPi4hklTXouTf0hccUjo0iCPjz6FnfIutBj3M7fPGlWO2SEWp
   x-amz-request-id: 51991C342example
   Date: Tue, 10 Feb 2015 00:17:23 GMT
   Server: OBS
   Content-Length: contentlength

   <?xml version="1.0" encoding="UTF-8"?>
   <ReplicationConfiguration xmlns="http://obs.example.com/doc/2006-03-01/">
     <Rule>
       <ID>rule1</ID>
       <Status>Enabled</Status>
       <Prefix></Prefix>
       <Destination>
         <Bucket>arn:aws:s3:::exampletargetbucket</Bucket>
         <StorageClass>STANDARD</StorageClass>
         <DeleteData>Disabled</DeleteData>
       </Destination>
       <HistoricalObjectReplication>Disabled</HistoricalObjectReplication>
     </Rule>
     <Agency>testAgency</Agency>
   </ReplicationConfiguration>
