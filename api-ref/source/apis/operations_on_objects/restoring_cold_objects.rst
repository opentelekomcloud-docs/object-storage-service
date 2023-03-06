:original_name: obs_04_0087.html

.. _obs_04_0087:

Restoring Cold Objects
======================

Functions
---------

To obtain the content of an object in the Cold storage class, you need to restore the object first and then you can download it. After an object is restored, a copy of the object is saved in the Standard storage class. By doing so, the object in the Cold storage class and its copy in the Standard storage class co-exist in the bucket. The copy will be automatically deleted once its retention period expires.

Versioning
----------

By default, this operation returns the latest version of an object. If the object has a delete marker, status code 404 is returned. To restore an object of a specified version, the **versionId** parameter can be used to specify the desired version.

Request Syntax
--------------

.. code-block:: text

   POST /ObjectName?restore&versionId=VersionID HTTP/1.1
   Host: bucketname.obs.region.example.com
   Date: date
   Authorization: authorization string
   Content-MD5: MD5

   <RestoreRequest>
      <Days>NumberOfDays</Days>
      <RestoreJob>
          <Tier>RetrievalOption</Tier>
      </RestoreJob>
   </RestoreRequest>

Request Parameters
------------------

+-----------------------+----------------------------------------------+-----------------------+
| Parameter             | Description                                  | Mandatory             |
+=======================+==============================================+=======================+
| versionId             | Version ID of the Cold object to be restored | No                    |
|                       |                                              |                       |
|                       | Type: string                                 |                       |
+-----------------------+----------------------------------------------+-----------------------+

Request Headers
---------------

This request uses common headers. For details, see :ref:`Table 3 <obs_04_0007__table25197309>`.

Request Elements
----------------

.. table:: **Table 1** Request elements

   +-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
   | Element               | Description                                                                                                                                                | Mandatory             |
   +=======================+============================================================================================================================================================+=======================+
   | RestoreRequest        | Container for the restore information                                                                                                                      | Yes                   |
   |                       |                                                                                                                                                            |                       |
   |                       | Type: container                                                                                                                                            |                       |
   +-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
   | Days                  | Indicates the storage duration of the restored object. The minimum value is 1 and the maximum value is 30.                                                 | Yes                   |
   |                       |                                                                                                                                                            |                       |
   |                       | Type: integer                                                                                                                                              |                       |
   +-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
   | RestoreJob            | Container for the restore options                                                                                                                          | No                    |
   |                       |                                                                                                                                                            |                       |
   |                       | Type: container                                                                                                                                            |                       |
   +-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
   | Tier                  | Restore options: **Expedited** \| **Standard**                                                                                                             | No                    |
   |                       |                                                                                                                                                            |                       |
   |                       | **Expedited** indicates that objects can be quickly restored within 1 to 5 minutes from Archive storage and within 3 to 5 hours from Deep Archive storage. |                       |
   |                       |                                                                                                                                                            |                       |
   |                       | **Standard** indicates that objects can be restored within 3 to 5 hours from Archive storage and within 5 to 12 hours from Deep Archive storage.           |                       |
   |                       |                                                                                                                                                            |                       |
   |                       | The default value is **Standard**.                                                                                                                         |                       |
   |                       |                                                                                                                                                            |                       |
   |                       | Type: string                                                                                                                                               |                       |
   +-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+

Response Syntax
---------------

::

   HTTP/1.1 status_code
   Date: date

Response Headers
----------------

The response to the request uses common headers. For details, see :ref:`Table 1 <obs_04_0013__d0e686>`.

Response Elements
-----------------

This response involves no elements.

Error Responses
---------------

.. table:: **Table 2** List of OBS access error codes

   +--------------------------+--------------------------------------------------------------------------------------------------------------------+-----------------------+
   | Error Code               | Description                                                                                                        | HTTP Status Code      |
   +==========================+====================================================================================================================+=======================+
   | RestoreAlreadyInProgress | The object is being restored. The request conflicts with another.                                                  | 409 Conflict          |
   |                          |                                                                                                                    |                       |
   |                          | ErrorMessage: Object restore is already in progress                                                                |                       |
   +--------------------------+--------------------------------------------------------------------------------------------------------------------+-----------------------+
   | ObjectHasAlreadyRestored | The objects have been restored and the retention period of the objects cannot be shortened.                        | 409 Conflict          |
   |                          |                                                                                                                    |                       |
   |                          | ErrorMessage: After restoring an archived object, you cannot shorten the restoration period of the archived object |                       |
   +--------------------------+--------------------------------------------------------------------------------------------------------------------+-----------------------+
   | MalformedXML             | Invalid value for the **Days** field (not an integer)                                                              | 400 Bad Request       |
   |                          |                                                                                                                    |                       |
   |                          | ErrorMessage: The XML you provided was not well-formed or did not validate against our published schema            |                       |
   +--------------------------+--------------------------------------------------------------------------------------------------------------------+-----------------------+
   | InvalidArgument          | The value of the **Days** field is not within the range of 1 to 30.                                                | 400 Bad Request       |
   |                          |                                                                                                                    |                       |
   |                          | ErrorMessage: restoration days should be at least 1 and at most 30                                                 |                       |
   +--------------------------+--------------------------------------------------------------------------------------------------------------------+-----------------------+
   | MalformedXML             | Invalid value for the **Tier** field.                                                                              | 400 Bad Request       |
   |                          |                                                                                                                    |                       |
   |                          | ErrorMessage: The XML you provided was not well-formed or did not validate against our published schema            |                       |
   +--------------------------+--------------------------------------------------------------------------------------------------------------------+-----------------------+
   | InvalidObjectState       | The restored object is not in the Cold storage.                                                                    | 403 Forbidden         |
   |                          |                                                                                                                    |                       |
   |                          | ErrorMessage: Restore is not allowed, as object's storage class is not COLD                                        |                       |
   +--------------------------+--------------------------------------------------------------------------------------------------------------------+-----------------------+

Sample Request
--------------

.. code-block:: text

   POST /object?restore HTTP/1.1
   Host: examplebucket.obs.region.example.com
   Accept: */*
   Date: WED, 01 Jul 2015 04:39:46 GMT
   Authorization: OBS H4IPJX0TQTHTHEBQQCEC:kaEwOixnSVuS6If3Q0Lnd6kxm5A=
   Content-Length: 183

   <RestoreRequest>
      <Days>2</Days>
      <RestoreJob>
        <Tier>Expedited</Tier>
      </RestoreJob>
   </RestoreRequest>

Sample Response
---------------

::

   HTTP/1.1 202 Accepted
   Server: OBS
   x-obs-request-id: A2F500000163F374CCBB2063F834C6C4
   x-obs-id-2: 32AAAUgAIAABAAAQAAEAABAAAQAAEAABCSLbWIs23RR95NVpkbWlJdlm8Dq+wQBw
   Date: WED, 01 Jul 2015 04:39:46 GMT
   Content-Length: 0
