:original_name: obs_04_0047.html

.. _obs_04_0047:

Obtaining the Cross-Region Replication Configuration of a Bucket
================================================================

Functions
---------

This operation obtains the replication configuration information of a specified bucket. To perform this operation, you must have the **GetReplicationConfiguration** permission.

Request Syntax
--------------

.. code-block:: text

   GET /?replication HTTP/1.1
   Host: bucketname.obs.region.example.com
   Date: date
   Authorization:authorization string

Request Parameters
------------------

This request contains no message parameters.

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
   Server:OBS
   Content-Length: contentlength

   <?xml version="1.0" encoding="UTF-8"?>
   <ReplicationConfiguration xmlns="http://obs.example.com/doc/2006-03-01/">
     <Agency>testAcy</Agency>
     <Rule>
         <ID>rule1</ID>
         <Status>Enabled</Status>
         <Prefix></Prefix>
         <Destination>
            <Bucket>exampletargetbucket</Bucket>
            <StorageClass>WARM</StorageClass>
            <DeleteData>Enabled</DeleteData>
         </Destination>
         <HistoricalObjectReplication>Enabled</HistoricalObjectReplication>
     </Rule>
   </ReplicationConfiguration>

Response Headers
----------------

The response to the request uses common headers. For details, see :ref:`Table 1 <obs_04_0013__d0e686>`.

Response Elements
-----------------

This response contains elements to detail the configuration. The following table describes the elements.

.. table:: **Table 1** Bucket replication configuration elements

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
   | Prefix                            | Prefix of an object key name, applicable to one or more objects. If the **Prefix** is left blank, the cross-region replication rule is applied to the whole bucket.        |
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
   |                                   | Type: string                                                                                                                                                               |
   |                                   |                                                                                                                                                                            |
   |                                   | Ancestor: Destination                                                                                                                                                      |
   |                                   |                                                                                                                                                                            |
   |                                   | Value options: **STANDARD**, **WARM**, **COLD**                                                                                                                            |
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

.. table:: **Table 2** Error response elements

   +--------------------------------+--------------------------------------------------------+--------------------+------------------------+
   | Error Code                     | Description                                            | HTTP Response Code | SOAP Error Code Prefix |
   +================================+========================================================+====================+========================+
   | NoSuchReplicationConfiguration | Cross-region replication configuration does not exist. | 404 not found      | Client                 |
   +--------------------------------+--------------------------------------------------------+--------------------+------------------------+

Sample Request
--------------

.. code-block:: text

   GET /?replication HTTP/1.1
   User-Agent: curl/7.29.0
   Host: examplebucket.obs.region.example.com
   Accept: */*
   Date: Wed, 27 Jun 2018 13:42:40 +0000
   Authorization: OBS H4IPJX0TQTHTHEBQQCEC:jGHviInfRyOkT/EpySpua1hlBuY=

Sample Response
---------------

::

   HTTP/1.1 200 OK
   Server: OBS
   x-obs-request-id: B59500000164417B57D02F7EF8823152
   x-obs-id-2: 32AAAQAAEAABAAAQAAEAABAAAQAAEAABCSHu6lz4vgk5G3E32OFcIPEZZgdOEYE/
   Content-Type: application/xml
   Date: Wed, 27 Jun 2018 13:42:39 GMT
   Content-Length: 337

   <?xml version="1.0" encoding="utf-8"?>
   <ReplicationConfiguration xmlns="http://obs.example.com/doc/2006-03-01/">
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
     <Agency>testAcy</Agency>
   </ReplicationConfiguration>
