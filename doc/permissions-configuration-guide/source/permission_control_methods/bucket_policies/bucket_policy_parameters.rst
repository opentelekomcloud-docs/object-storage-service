:original_name: obs_40_0041.html

.. _obs_40_0041:

Bucket Policy Parameters
========================

A bucket policy in JSON format:

.. code-block::

   {
   "Statement" : [{
        statement1
     },
     {
        statement2
     },
     ......
    ]
   }

Example:

.. code-block::

   {
   "Statement" : [{
        "Sid": "ExampleStatementID1",
        "Principal": "*",
        "Effect": "Allow",
        "Action": ["ListBucket"],
        "Resource": "examplebucket",
        "Condition": "some conditions"
     },
     {
        "Sid": "ExampleStatementID2",
        "Principal": "*",
        "Effect": "Allow",
        "Action": ["PutObject"],
        "Resource": "examplebucket",
        "Condition": "some conditions"
     },
   ......
   ]
   }

A policy consists of one or more statements. Each statement contains the following elements:

.. table:: **Table 1** Elements of a bucket policy statement

   +--------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+------------------------------------------------------------+
   | Element      | Description                                                                                                                                                                                                                                                                                                                                                                                      | Mandatory/Optional                                         |
   +==============+==================================================================================================================================================================================================================================================================================================================================================================================================+============================================================+
   | Sid          | ID of the statement. The value is a string that describes the statement.                                                                                                                                                                                                                                                                                                                         | Optional                                                   |
   +--------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+------------------------------------------------------------+
   | Principal    | Domains and users that a statement applies to. The value can be a wildcard (``*``), indicating all users. To grant permissions to all users in a domain, set **Principal** to **domain/**\ *domainid*\ **:user/\***. To grant permissions to a specific user in a domain, set **Principal** to **domain/**\ *domainid*\ **:user/**\ *userId* or **domain/**\ *domainid*\ **:user/**\ *userName*. | Optional. Select either **Principal** or **NotPrincipal**. |
   +--------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+------------------------------------------------------------+
   | NotPrincipal | Users that the statement does not apply to. Its value has the same format as **Principal**.                                                                                                                                                                                                                                                                                                      | Optional. Select either **NotPrincipal** or **Principal**. |
   +--------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+------------------------------------------------------------+
   | Action       | Actions that the statement applies to. This parameter specifies a set of all the operations supported by OBS. Its values are case insensitive. The value can be a wildcard character (``*``) that indicates all operations. For example: **"Action":["List*","Get*"]**.                                                                                                                          | Optional. Select either **Action** or **NotAction**.       |
   +--------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+------------------------------------------------------------+
   | NotAction    | Actions that are not controlled by this statement. Its value has the same format as **Action**.                                                                                                                                                                                                                                                                                                  | Optional. Select either **Action** or **NotAction**.       |
   +--------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+------------------------------------------------------------+
   | Effect       | Whether the permission in a statement is **Allow** or **Deny**.                                                                                                                                                                                                                                                                                                                                  | Mandatory                                                  |
   +--------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+------------------------------------------------------------+
   | Resource     | Resources that the statement will apply to. You can use a wildcard (``*``) to indicate all resources.                                                                                                                                                                                                                                                                                            | Optional. Select either **Resource** or **NotResource**.   |
   +--------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+------------------------------------------------------------+
   | NotResource  | Resources that the statement will not apply to. Its value has the same format as **Resource**.                                                                                                                                                                                                                                                                                                   | Optional. Select either **Resource** or **NotResource**.   |
   +--------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+------------------------------------------------------------+
   | Condition    | Conditions for the statement to take effect.                                                                                                                                                                                                                                                                                                                                                     | Optional                                                   |
   +--------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+------------------------------------------------------------+

.. note::

   A statement must contain **Action** or **NotAction**, **Resource** or **NotResource**, and **Principal** or **NotPrincipal**.

Principal/NotPrincipal
----------------------

**Principal** or **NotPrincipal** can be anonymous users, specific tenants, specific users, federated users, or agencies.

-  All (anonymous users)

   .. code-block::

      "Principal": {"ID": "*"}

   In the example, the wildcard (``*``) indicates Everyone/Anonymous. Do not use the wildcard for **Principal** of the role's trust policy unless you have restricted access by using the **Condition** element in the policy.

-  Specific tenants

   If a tenant identifier is used as the **Principal** of a policy, permissions are granted to all users of this tenant. This includes all subscribers under the account. The following example demonstrates how to specify an account as an authorized person.

   .. code-block::

      "Principal": { "ID": " domain/domainIdxxxx:user/*" }

   You can also grant permissions to multiple tenants at a time:

   .. code-block::

      "Principal": {
        "ID": [
          "domain/domainIDxx1:user/useridxxxx",
          "domain/domainIDxx2:user/*"
        ]
      }

-  Specific users

   User names in the **Principal** element are case-sensitive.

   .. code-block::

      "Principal": {"ID": "domain/domainIDxxx:user/user-name" }
      "Principal": {
        "ID": [
          "domain/domainIDxxx:user/UserID1",
          "domain/domainIDxxx:user/UserID2"
        ]
      }

-  Federated users (using SAML identity provider)

   .. code-block::

      "Principal": { "Federated": "domain/domainIDxxx:identity-provider/provider-name" }
      "Principal": { "Federated": "domain/domainIDxxx:group/groupname" }

-  Agencies

   **\*** indicates all agencies of a tenant.

   .. code-block::

      "Principal": { "ID": "domain/domainIDxxx:agency/agencyname" }
      "Principal": { "ID": "domain/domainIDxxx:agency/*" }

The principals on OBS Console refer to the users that the bucket policies apply to. These users can be accounts, federated users or federated user groups, or IAM users. You can specify the principals to include or exclude.

-  **Include**: The policy applies to specified users.
-  **Exclude**: The policy applies to users except the specified ones.

**Specifying IAM users under the current account**

You can set **Principal** to **Current account** and select one or more IAM users under this account, so that the bucket policy applies to the selected IAM users.

**Specifying another account**

You can set **Principal** to **Other account**, enter an account ID, and then enter one or more user IDs to apply the bucket policy to only the IAM users under that account. You need to use commas (,) to separate user IDs.

.. note::

   To obtain the account ID and user ID, log in to the console as an IAM user and go to the **My Credentials** page to obtain them.

**Specifying** **anonymous users**

To grant access to anyone, set **Principal** to **Other account** and enter a wildcard (``*``) as the account ID.

.. important::

   Exercise caution when granting permissions to anonymous users. If you grant the permissions to anonymous users, anyone can access your bucket. You are advised to restrict access requests. For example, you can allow access only from a specific IP address.

.. _obs_40_0041__en-us_topic_0118394684_section1623516525350:

Action/NotAction
----------------

If a policy applies to a bucket, configure bucket-related actions. If the policy applies to the objects in a bucket, configure object-related actions.

Actions can be specified in either of the following ways:

-  **Include**: The bucket policy applies to specified actions.
-  **Exclude**: The bucket policy applies to actions except the specified ones.

**Bucket Actions**

.. table:: **Table 2** Description of bucket-related actions

   +---------+---------------------------------+---------------------------------------+-----------------------------------------------------------------+
   | Type    | Value                           |                                       | Description                                                     |
   +=========+=================================+=======================================+=================================================================+
   | General | \*                              |                                       | Indicates all actions on a bucket.                              |
   +---------+---------------------------------+---------------------------------------+-----------------------------------------------------------------+
   |         | Get\*                           |                                       | Indicates all GET actions on a bucket.                          |
   +---------+---------------------------------+---------------------------------------+-----------------------------------------------------------------+
   |         | Put\*                           |                                       | Indicates all PUT actions on a bucket.                          |
   +---------+---------------------------------+---------------------------------------+-----------------------------------------------------------------+
   |         | List\*                          |                                       | Indicates all LIST actions on a bucket.                         |
   +---------+---------------------------------+---------------------------------------+-----------------------------------------------------------------+
   | Bucket  | Operations on buckets           | ListBucket                            | Lists objects in a bucket, and obtains the bucket metadata.     |
   +---------+---------------------------------+---------------------------------------+-----------------------------------------------------------------+
   |         |                                 | DeleteBucket                          | Deletes a bucket.                                               |
   +---------+---------------------------------+---------------------------------------+-----------------------------------------------------------------+
   |         |                                 | GetBucketLocation                     | Gets the location of a bucket.                                  |
   +---------+---------------------------------+---------------------------------------+-----------------------------------------------------------------+
   |         |                                 | GetBucketStorage                      | Obtains bucket storage information.                             |
   +---------+---------------------------------+---------------------------------------+-----------------------------------------------------------------+
   |         | Bucket policies                 | GetBucketPolicy                       | Gets a bucket policy.                                           |
   +---------+---------------------------------+---------------------------------------+-----------------------------------------------------------------+
   |         |                                 | PutBucketPolicy                       | Configures a bucket policy.                                     |
   +---------+---------------------------------+---------------------------------------+-----------------------------------------------------------------+
   |         |                                 | DeleteBucketPolicy                    | Deletes a bucket policy.                                        |
   +---------+---------------------------------+---------------------------------------+-----------------------------------------------------------------+
   |         | Bucket ACL                      | GetBucketAcl                          | Gets the ACL information of a bucket.                           |
   +---------+---------------------------------+---------------------------------------+-----------------------------------------------------------------+
   |         |                                 | PutBucketAcl                          | Configures ACL for a bucket.                                    |
   +---------+---------------------------------+---------------------------------------+-----------------------------------------------------------------+
   |         | Bucket logs                     | GetBucketLogging                      | Gets the logs of a bucket.                                      |
   +---------+---------------------------------+---------------------------------------+-----------------------------------------------------------------+
   |         |                                 | PutBucketLogging                      | Configures logging for a bucket.                                |
   +---------+---------------------------------+---------------------------------------+-----------------------------------------------------------------+
   |         | Lifecycle rules                 | GetLifecycleConfiguration             | Obtains the lifecycle rules of a bucket.                        |
   +---------+---------------------------------+---------------------------------------+-----------------------------------------------------------------+
   |         |                                 | PutLifecycleConfiguration             | Configures a lifecycle rule for a bucket.                       |
   +---------+---------------------------------+---------------------------------------+-----------------------------------------------------------------+
   |         | Static website hosting          | GetBucketWebsite                      | Obtains the static website configuration of a bucket.           |
   +---------+---------------------------------+---------------------------------------+-----------------------------------------------------------------+
   |         |                                 | PutBucketWebsite                      | Configures static website hosting for a bucket.                 |
   +---------+---------------------------------+---------------------------------------+-----------------------------------------------------------------+
   |         |                                 | DeleteBucketWebsite                   | Cancels static website hosting for a bucket.                    |
   +---------+---------------------------------+---------------------------------------+-----------------------------------------------------------------+
   |         | Bucket versioning               | GetBucketVersioning                   | Gets the versioning information of a bucket.                    |
   +---------+---------------------------------+---------------------------------------+-----------------------------------------------------------------+
   |         |                                 | PutBucketVersioning                   | Configures versioning for a bucket.                             |
   +---------+---------------------------------+---------------------------------------+-----------------------------------------------------------------+
   |         |                                 | ListBucketVersions                    | Lists object versions in a bucket.                              |
   +---------+---------------------------------+---------------------------------------+-----------------------------------------------------------------+
   |         | Bucket tags                     | GetBucketTagging                      | Gets bucket tags.                                               |
   +---------+---------------------------------+---------------------------------------+-----------------------------------------------------------------+
   |         |                                 | PutBucketTagging                      | Configures tags for a bucket.                                   |
   +---------+---------------------------------+---------------------------------------+-----------------------------------------------------------------+
   |         |                                 | DeleteBucketTagging                   | Deletes bucket tags.                                            |
   +---------+---------------------------------+---------------------------------------+-----------------------------------------------------------------+
   |         | CORS rules                      | GetBucketCORS                         | Gets the CORS configuration of a bucket.                        |
   +---------+---------------------------------+---------------------------------------+-----------------------------------------------------------------+
   |         |                                 | PutBucketCORS                         | Configures CORS for a bucket.                                   |
   +---------+---------------------------------+---------------------------------------+-----------------------------------------------------------------+
   |         | Message notifications           | GetBucketNotification                 | Gets event notifications of a bucket.                           |
   +---------+---------------------------------+---------------------------------------+-----------------------------------------------------------------+
   |         |                                 | PutBucketNotification                 | Configures event notifications for a bucket.                    |
   +---------+---------------------------------+---------------------------------------+-----------------------------------------------------------------+
   |         | Bucket storage class            | GetBucketStoragePolicy                | Gets the default storage class of a bucket.                     |
   +---------+---------------------------------+---------------------------------------+-----------------------------------------------------------------+
   |         |                                 | PutBucketStoragePolicy                | Configures the default storage class for a bucket.              |
   +---------+---------------------------------+---------------------------------------+-----------------------------------------------------------------+
   |         | Bucket storage quota            | GetBucketQuota                        | Gets storage quotas of a bucket.                                |
   +---------+---------------------------------+---------------------------------------+-----------------------------------------------------------------+
   |         |                                 | PutBucketQuota                        | Configures storage quotas for a bucket.                         |
   +---------+---------------------------------+---------------------------------------+-----------------------------------------------------------------+
   |         | User-defined domain names       | GetBucketCustomDomainConfiguration    | Gets the user-defined domain name of a bucket.                  |
   +---------+---------------------------------+---------------------------------------+-----------------------------------------------------------------+
   |         |                                 | PutBucketCustomDomainConfiguration    | Binds a user-defined domain name to a bucket.                   |
   +---------+---------------------------------+---------------------------------------+-----------------------------------------------------------------+
   |         |                                 | DeleteBucketCustomDomainConfiguration | Unbinds a user-defined domain name from a bucket.               |
   +---------+---------------------------------+---------------------------------------+-----------------------------------------------------------------+
   |         | Bucket encryption               | GetEncryptionConfiguration            | Obtains the server-side encryption configuration of a bucket.   |
   +---------+---------------------------------+---------------------------------------+-----------------------------------------------------------------+
   |         |                                 | PutEncryptionConfiguration            | Configures server-side encryption for a bucket.                 |
   +---------+---------------------------------+---------------------------------------+-----------------------------------------------------------------+
   |         | Default bucket retention policy | GetBucketObjectLockConfiguration      | Obtains the default retention settings of a bucket.             |
   +---------+---------------------------------+---------------------------------------+-----------------------------------------------------------------+
   |         |                                 | PutBucketObjectLockConfiguration      | Configures a default retention policy for a bucket.             |
   +---------+---------------------------------+---------------------------------------+-----------------------------------------------------------------+
   |         | Bucket inventories              | GetBucketInventoryConfiguration       | Gets the inventory configuration of a bucket.                   |
   +---------+---------------------------------+---------------------------------------+-----------------------------------------------------------------+
   |         |                                 | PutBucketInventoryConfiguration       | Configures inventories for a bucket.                            |
   +---------+---------------------------------+---------------------------------------+-----------------------------------------------------------------+
   |         |                                 | DeleteBucketInventoryConfiguration    | Deletes the inventory configuration of a bucket.                |
   +---------+---------------------------------+---------------------------------------+-----------------------------------------------------------------+
   |         | Other                           | GetReplicationConfiguration           | Gets the cross-region replication configuration of a bucket.    |
   +---------+---------------------------------+---------------------------------------+-----------------------------------------------------------------+
   |         |                                 | PutReplicationConfiguration           | Configures cross-region replication for a bucket.               |
   +---------+---------------------------------+---------------------------------------+-----------------------------------------------------------------+
   |         |                                 | DeleteReplicationConfiguration        | Deletes the cross-region replication configuration of a bucket. |
   +---------+---------------------------------+---------------------------------------+-----------------------------------------------------------------+
   |         |                                 | ListBucketMultipartUploads            | Lists multipart upload tasks.                                   |
   +---------+---------------------------------+---------------------------------------+-----------------------------------------------------------------+

**Object Actions**

.. table:: **Table 3** Description of object-related actions

   +---------+-------------------------+--------------------------+----------------------------------------------------------------------------------------------------------------+
   | Type    | Value                   |                          | Description                                                                                                    |
   +=========+=========================+==========================+================================================================================================================+
   | General | \*                      |                          | Indicates all actions on an object.                                                                            |
   +---------+-------------------------+--------------------------+----------------------------------------------------------------------------------------------------------------+
   |         | Get\*                   |                          | Indicates all GET actions on an object.                                                                        |
   +---------+-------------------------+--------------------------+----------------------------------------------------------------------------------------------------------------+
   |         | Put\*                   |                          | Indicates all PUT actions on an object.                                                                        |
   +---------+-------------------------+--------------------------+----------------------------------------------------------------------------------------------------------------+
   |         | List\*                  |                          | Indicates all LIST actions on an object.                                                                       |
   +---------+-------------------------+--------------------------+----------------------------------------------------------------------------------------------------------------+
   | Object  | Operations on objects   | GetObject                | Gets the content and metadata of an object.                                                                    |
   +---------+-------------------------+--------------------------+----------------------------------------------------------------------------------------------------------------+
   |         |                         | PutObject                | Performs PUT upload, POST upload, multipart upload, initialization of uploaded parts, and assembling of parts. |
   +---------+-------------------------+--------------------------+----------------------------------------------------------------------------------------------------------------+
   |         |                         | RestoreObject            | Restores Cold objects.                                                                                         |
   +---------+-------------------------+--------------------------+----------------------------------------------------------------------------------------------------------------+
   |         |                         | DeleteObject             | Deletes an object.                                                                                             |
   +---------+-------------------------+--------------------------+----------------------------------------------------------------------------------------------------------------+
   |         | Object ACL              | GetObjectAcl             | Gets the ACL information of an object.                                                                         |
   +---------+-------------------------+--------------------------+----------------------------------------------------------------------------------------------------------------+
   |         |                         | PutObjectAcl             | Configures ACL for an object.                                                                                  |
   +---------+-------------------------+--------------------------+----------------------------------------------------------------------------------------------------------------+
   |         | Versioning              | GetObjectVersion         | Gets the content and metadata of a specified object version.                                                   |
   +---------+-------------------------+--------------------------+----------------------------------------------------------------------------------------------------------------+
   |         |                         | DeleteObjectVersion      | Deletes a specified object version.                                                                            |
   +---------+-------------------------+--------------------------+----------------------------------------------------------------------------------------------------------------+
   |         | Object version ACL      | GetObjectVersionAcl      | Gets the ACL information of a specified object version.                                                        |
   +---------+-------------------------+--------------------------+----------------------------------------------------------------------------------------------------------------+
   |         |                         | PutObjectVersionAcl      | Configures ACL for a specified object version.                                                                 |
   +---------+-------------------------+--------------------------+----------------------------------------------------------------------------------------------------------------+
   |         | Object retention policy | PutObjectRetention       | Configures a retention policy for an object.                                                                   |
   +---------+-------------------------+--------------------------+----------------------------------------------------------------------------------------------------------------+
   |         | Other                   | AbortMultipartUpload     | Cancels a multipart upload.                                                                                    |
   +---------+-------------------------+--------------------------+----------------------------------------------------------------------------------------------------------------+
   |         |                         | ListMultipartUploadParts | Lists uploaded parts.                                                                                          |
   +---------+-------------------------+--------------------------+----------------------------------------------------------------------------------------------------------------+
   |         |                         | ModifyObjectMetadata     | Modifies object metadata.                                                                                      |
   +---------+-------------------------+--------------------------+----------------------------------------------------------------------------------------------------------------+

Resource/NotResource
--------------------

The resources supported by OBS are as follows:

-  *bucketname*: The **Action** drop-down list box lists all actions allowed on a bucket. To allow an action on a bucket, set **Resource** to the bucket name.
-  *bucketname/objectname*: The **Action** drop-down list box lists all actions allowed on an object. To allow an action on an object in a bucket, set **Resource** to *bucketname/objectname*. You can use a wildcard for **objectname** to allow an action on all objects in the bucket. For example, if you want to allow an action on all objects in a directory of a bucket, set **Resource** to ``"bucketname/directory/*"``. If you have permissions on all the objects in a bucket, set **Resource** to ``"bucketname/*"``. If you want to allow an action on both a bucket and its objects, set **Resource** to **["examplebucket/*","examplebucket"]**.

The following example policy grants the permissions to allow user1 with the ID of **71f3901173514e6988115ea2c26d1999** under account **b4bf1b36d9ca43d984fbcb9491b6fce9** (account ID) to take all actions on the **examplebucket** bucket and all objects in it.

.. code-block::

   {
       "Statement":[
       {
         "Sid":"test",
         "Effect":"Allow",
         "Principal": {"ID": ["domain/b4bf1b36d9ca43d984fbcb9491b6fce9:user/71f3901173514e6988115ea2c26d1999"]},
         "Action":["*"],
         "Resource":["examplebucket/*","examplebucket"]
       }
     ]
   }

On OBS Console, you can apply a bucket policy to the following resources: the current bucket, and all objects in a bucket.

You can specify the resources to include or exclude:

-  **Include**: The bucket policy applies to specified OBS resources.
-  **Exclude**: The bucket policy applies to OBS resources except the specified ones.

**Applying a bucket policy to a bucket**

To apply a bucket policy to the current bucket, keep the resource text box empty. When configuring actions for the policy, select bucket related actions.

**Applying a bucket policy to specified objects**

To apply a bucket policy to specified objects in a bucket, object-related actions must be configured in the policy.

-  For an object, enter the object name (including its folder name if any). For example, if the resource is the **example.jpg** file in the **imgs-folder** folder in the bucket, enter the following in the resource text box:

   **imgs-folder/example.jpg**

-  For an object set, use the wildcard asterisk (*). The asterisk (*) indicates an empty string or any combination of characters.

   -  Use only one asterisk (*) to indicate all objects in a bucket.

   -  Use *Object name prefix*\ \* to indicate objects with this prefix in a bucket. Example:

      imgs\*

   -  Use \*\ *Object name suffix* to indicate objects with this suffix in a bucket. Example:

      \*.jpg

.. note::

   Use commas (,) to separate one object (or object set) from another.

Condition
---------

In addition to the effect, principals, resources, and actions, you can also specify the conditions for a bucket policy to take effect. The bucket policy is applied only when its condition expressions match the values contained in the request. Conditions are optional. You can choose whether to configure them.

For example, if account A needs to have full control over an object uploaded by account B to bucket **example** of account A, the **acl** key must be specified in the upload request and the policy effect must be set to **Allow** for account A. The complete condition expression is as follows:

================== === =========================
Condition Operator Key Value
================== === =========================
StringEquals       acl bucket-owner-full-control
================== === =========================

A condition consists of condition operator, key, and value. Condition operators and keys are correlated. If you select a string type, for example, **StringEquals**, for a condition operator, the key can only be a string type, for example, **UserAgent**. Likewise, if you select a key of the date type, for example, **CurrentTime**, the condition operator can only be a date type, for example, **DateEquals**.

A condition can contain multiple combinations of a condition key, a condition operator, and a condition value. The **Condition** combination in the following figure indicates that the request time ranges from **2015-07-01T12:00:00Z** to **2018-04-16T15:00:00Z** and the request IP address range is **192.168.176.0/24** or **192.168.143.0/24**.

.. code-block::

   "Condition" : {
     "DateGreaterThan" : {
     "CurrentTime" : "2015-07-01T12:00:00Z"
     },
     "DateLessThan": {
     "CurrentTime" : "2018-04-16T15:00:00Z"
     },
     "IpAddress" : {
     "SourceIp" : ["192.168.176.0/24","192.168.143.0/24"]
     }
   }

Condition Operators
-------------------

A condition operator, a condition key, and a condition value together constitute a complete condition statement. A policy can be applied only when its request conditions are met. :ref:`Table 4 <obs_40_0041__en-us_topic_0118394684_table18965458>` lists the condition operators available for statements. If a condition operator corresponds to multiple identical keys, only the last key is retained.

.. _obs_40_0041__en-us_topic_0118394684_table18965458:

.. table:: **Table 4** Condition operators

   +-----------------------+---------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Type                  | Element                   | Description                                                                                                                                                                                  |
   +=======================+===========================+==============================================================================================================================================================================================+
   | String                | StringEquals              | Strict matching. Short version: streq                                                                                                                                                        |
   +-----------------------+---------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   |                       | StringNotEquals           | Strict negated matching. Short version: strneq                                                                                                                                               |
   +-----------------------+---------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   |                       | StringEqualsIgnoreCase    | Strict matching, ignoring case. Short version: streqi                                                                                                                                        |
   +-----------------------+---------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   |                       | StringNotEqualsIgnoreCase | Strict negated matching, ignoring case. Short version: strneqi                                                                                                                               |
   +-----------------------+---------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   |                       | StringLike                | Loose case-sensitive matching. The values can include a multi-character match wildcard (``*``) or a single-character match wildcard (?) anywhere in the string. Short version: strl          |
   +-----------------------+---------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   |                       | StringNotLike             | Negated loose case-sensitive matching. The values can include a multi-character match wildcard (``*``) or a single-character match wildcard (?) anywhere in the string. Short version: strnl |
   +-----------------------+---------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Numeric               | NumericEquals             | Matching. Short version: numeq                                                                                                                                                               |
   |                       |                           |                                                                                                                                                                                              |
   |                       |                           | **Numeric** indicates a data type expressed in numbers.                                                                                                                                      |
   +-----------------------+---------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   |                       | NumericNotEquals          | Negated matching. Short version: numneq                                                                                                                                                      |
   +-----------------------+---------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   |                       | NumericLessThan           | "Less than" matching. Short version: numlt                                                                                                                                                   |
   +-----------------------+---------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   |                       | NumericLessThanEquals     | "Less than or equals" matching. Short version: numlteq                                                                                                                                       |
   +-----------------------+---------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   |                       | NumericGreaterThan        | "Greater than" matching. Short version: numgt                                                                                                                                                |
   +-----------------------+---------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   |                       | NumericGreaterThanEquals  | "Greater than or equals" matching. Short version: numgteq                                                                                                                                    |
   +-----------------------+---------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Date                  | DateEquals                | Matching a specific date. Short version: dateeq                                                                                                                                              |
   +-----------------------+---------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   |                       | DateNotEquals             | Negated matching. Short version: dateneq                                                                                                                                                     |
   +-----------------------+---------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   |                       | DateLessThan              | The date is earlier than a specific date. Short version: datelt                                                                                                                              |
   +-----------------------+---------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   |                       | DateLessThanEquals        | The date is earlier than or equal to a specific date. Short version: datelteq                                                                                                                |
   +-----------------------+---------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   |                       | DateGreaterThan           | The date is later than a specific date. Short version: dategt                                                                                                                                |
   +-----------------------+---------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   |                       | DateGreaterThanEquals     | The date is later than or equal to a specific date. Short version: dategteq                                                                                                                  |
   +-----------------------+---------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Boolean               | Bool                      | Strict Boolean matching                                                                                                                                                                      |
   +-----------------------+---------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | IP address            | IpAddress                 | Specified IP address or range                                                                                                                                                                |
   +-----------------------+---------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   |                       | NotIpAddress              | All IP addresses excluding the specified IP address or range                                                                                                                                 |
   +-----------------------+---------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Condition Keys
--------------

Condition keys can be classified into general keys, keys related to actions on buckets, and keys related to actions on objects. :ref:`Table 5 <obs_40_0041__table6707152645718>` lists the general keys.

.. _obs_40_0041__table6707152645718:

.. table:: **Table 5** General keys

   +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------+
   | Key                   | Type                  | Description                                                                                                                                    |
   +=======================+=======================+================================================================================================================================================+
   | CurrentTime           | Date                  | Date when the request was received by the server. The date format must comply with ISO 8601.                                                   |
   +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------+
   | EpochTime             | Numeric               | Time when the request was received by the server, which was expressed as seconds since 1970.01.01 00:00:00 UTC, regardless of the leap seconds |
   +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------+
   | SecureTransport       | Bool                  | Whether the request was encrypted using SSL                                                                                                    |
   |                       |                       |                                                                                                                                                |
   |                       |                       | .. note::                                                                                                                                      |
   |                       |                       |                                                                                                                                                |
   |                       |                       |    The value can be either **true** or **false**. Any other values you enter will become **false** by default.                                 |
   +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------+
   | SourceIp              | IP address            | Source (client) IP address of the request                                                                                                      |
   +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------+
   | UserAgent             | String                | Requested client software agent                                                                                                                |
   +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------+
   | Referer               | String                | Link from which the request was sent                                                                                                           |
   +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------+

Action-related condition keys can be used only when a specific action is selected. :ref:`Table 6 <obs_40_0041__table1972610267573>` and :ref:`Table 7 <obs_40_0041__table14742526145718>` list the mapping between actions and condition keys.

.. _obs_40_0041__table1972610267573:

.. table:: **Table 6** Keys related to bucket actions

   +--------------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Action             | Optional Key    | Description                                                                                                                                                                                                                                                           | Remarks                                                                                                                                                                                                                                                                                                                                                                                     |
   +====================+=================+=======================================================================================================================================================================================================================================================================+=============================================================================================================================================================================================================================================================================================================================================================================================+
   | ListBucket         | prefix          | Type: String. Lists objects with the specified prefix.                                                                                                                                                                                                                | If **prefix**, **delimiter**, and **max-keys** are configured for a bucket policy, the List requests must contain the matched key-value pair.                                                                                                                                                                                                                                               |
   |                    |                 |                                                                                                                                                                                                                                                                       |                                                                                                                                                                                                                                                                                                                                                                                             |
   |                    |                 |                                                                                                                                                                                                                                                                       | For example, if a bucket policy (with the condition operator set to **NumericEquals**, the key to **max-keys**, and the value to **100**) is configured to allow anonymous users to read data from a bucket, the List requests from the anonymous users must have **?max-keys=100** at the end of the bucket domain name. The listed objects are the first 100 objects in alphabetic order. |
   +--------------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   |                    | delimiter       | Type: String. Groups objects in a bucket.                                                                                                                                                                                                                             |                                                                                                                                                                                                                                                                                                                                                                                             |
   +--------------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   |                    | max-keys        | Type: Numeric. Sets the maximum number of objects. Returned objects are listed in alphabetic order.                                                                                                                                                                   |                                                                                                                                                                                                                                                                                                                                                                                             |
   +--------------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | ListBucketVersions | prefix          | Type: String. Lists multi-version objects with the specified prefix.                                                                                                                                                                                                  |                                                                                                                                                                                                                                                                                                                                                                                             |
   +--------------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   |                    | delimiter       | Type: String. Groups objects of different versions in a bucket.                                                                                                                                                                                                       |                                                                                                                                                                                                                                                                                                                                                                                             |
   +--------------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   |                    | max-keys        | Type: Numeric. Sets the maximum number of objects. Returned objects are listed in alphabetic order.                                                                                                                                                                   |                                                                                                                                                                                                                                                                                                                                                                                             |
   +--------------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | PutBucketAcl       | acl             | Type: String. Configures the bucket ACL. When modifying a bucket ACL, you can use the request that contains a canned ACL setting in its header. Value options of a canned ACL setting: **private|public-read|public-read-write|bucketowner-read|log-delivery-write**. | None                                                                                                                                                                                                                                                                                                                                                                                        |
   +--------------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

.. _obs_40_0041__table14742526145718:

.. table:: **Table 7** Keys related to object actions

   +---------------------+------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Action              | Optional Key           | Description                                                                                                                                                                                                                                                                                                                       |
   +=====================+========================+===================================================================================================================================================================================================================================================================================================================================+
   | PutObject           | acl                    | Type: String. Configures the object ACL. When uploading an object, you can use the request that contains a canned ACL setting in its header. Value options of a canned ACL setting: **private|public-read|public-read-write|bucketowner-read|bucket-owner-full-control|log-delivery-write**.                                      |
   +---------------------+------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   |                     | copy-source            | Type: String. Specifies names of the source bucket and the source object. Format: **/**\ *bucketname*\ **/**\ *keyname*                                                                                                                                                                                                           |
   +---------------------+------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   |                     | metadata-directive     | Type: String. Specifies whether to copy the metadata of the source object or replace with the metadata in the request. The value can be **COPY** or **REPLACE**.                                                                                                                                                                  |
   +---------------------+------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   |                     | server-side-encryption | Type: String. Specifies that objects in a bucket are encrypted using SSE-KMS before they are stored. The value is **kms**.                                                                                                                                                                                                        |
   +---------------------+------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | PutObjectAcl        | acl                    | Type: String. Configures the object ACL. When uploading an object, you can use the request that contains a canned ACL setting in its header. Value options of a canned ACL setting: **private|public-read|public-read-write|bucketowner-read|bucket-owner-full-control|log-delivery-write**.                                      |
   +---------------------+------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | GetObjectVersion    | versionId              | Type: String. Obtains the object with the specified version ID.                                                                                                                                                                                                                                                                   |
   +---------------------+------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | GetObjectVersionAcl | versionId              | Type: String. Obtains the ACL of the object with the specified version ID.                                                                                                                                                                                                                                                        |
   +---------------------+------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | PutObjectVersionAcl | versionId              | Type: String. Specifies a version ID.                                                                                                                                                                                                                                                                                             |
   +---------------------+------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   |                     | acl                    | Type: String. Configures the ACL of the object with the specified version ID. When uploading an object, you can use the request that contains a canned ACL setting in its header. Value options of a canned ACL setting: **private|public-read|public-read-write|bucketowner-read|bucket-owner-full-control|log-delivery-write**. |
   +---------------------+------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | DeleteObjectVersion | versionId              | Type: String. Deletes the object with the specified version ID.                                                                                                                                                                                                                                                                   |
   +---------------------+------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Policy Permission Judgment Logic
--------------------------------

Each statement in a policy can have the action **Explicit Deny**, **Allow**, or **Default Deny**. If a bucket policy contains multiple statements with different actions, the final action is determined according to the following rules:

- If there are no **Explicit Deny** or **Allow**, **Default Deny** will apply.

- An explicit deny overrides an allow.

- An allow overrides a default deny.

- Statements can be in any order in a policy.

.. table:: **Table 8** Statement results

   +---------------+-------------------------------------------------------------------------------------------------------------------------------------+
   | Result        | Description                                                                                                                         |
   +===============+=====================================================================================================================================+
   | explicit deny | A statement defines effect="deny". All requests for resources to which the statement applies are denied. No permission is returned. |
   +---------------+-------------------------------------------------------------------------------------------------------------------------------------+
   | allow         | A statement defines effect="allow". All requests for resources to which the statement applies are allowed.                          |
   +---------------+-------------------------------------------------------------------------------------------------------------------------------------+
   | default deny  | Conditions defined in a statement are not met. Requests are denied.                                                                 |
   +---------------+-------------------------------------------------------------------------------------------------------------------------------------+

If both an ACL and a bucket policy apply, an explicit deny in the bucket policy overrides the allow in the ACL.

If both a bucket policy and an IAM policy apply, an explicit deny overrides an allow, and an allow overrides the default deny.

Bucket ACL/Policy for cross-tenant authorization does not apply to SSE-KMS server-side encrypted objects.
