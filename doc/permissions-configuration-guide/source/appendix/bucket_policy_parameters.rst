:original_name: obs_40_0041.html

.. _obs_40_0041:

Bucket Policy Parameters
========================

A policy in JSON format is described as follows:

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
        "Action": "ListBucket",
        "Resource": "examplebucket",
        "Condition": "some conditions"
     },
     {
        "Sid": "ExampleStatementID2",
        "Principal": "*",
        "Effect": "Allow",
        "Action": "PutObject",
        "Resource": "examplebucket",
        "Condition": "some conditions"
     },
   ......
   ]
   }

A policy is comprised of one or more statements. Each statement contains the following elements:

.. table:: **Table 1** Statement elements

   +--------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+------------------------------------------------------------+
   | Element      | Description                                                                                                                                                                                                                                                                                                                                                                                                                                     | Mandatory/Optional                                         |
   +==============+=================================================================================================================================================================================================================================================================================================================================================================================================================================================+============================================================+
   | Sid          | ID of a statement. The value is a string that describes the statement.                                                                                                                                                                                                                                                                                                                                                                          | Optional                                                   |
   +--------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+------------------------------------------------------------+
   | Principal    | Domains and users to which a statement applies. The wildcard (``*``) is supported, indicating all users. When permissions are authorized to all users under a domain, the format of **Principal** is **domain/**\ *domainid*\ **:user/\***. When permissions are authorized to a specific user under a domain, the format of **Principal** is **domain/**\ *domainid*\ **:user/**\ *userId* or **domain/**\ *domainid*\ **:user/**\ *userName*. | Optional. Select either **Principal** or **NotPrincipal**. |
   +--------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+------------------------------------------------------------+
   | NotPrincipal | An exception to a list of principals in the statement. You can deny access to all principals except the ones named in the **NotPrincipal** element. This parameter has the same value format as **Principal**.                                                                                                                                                                                                                                  | Optional. Select either **NotPrincipal** or **Principal**. |
   +--------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+------------------------------------------------------------+
   | Action       | Actions which a statement applies to. This parameter specifies a set of all the operations supported by OBS. Its values are case insensitive. The value supports a wildcard character (``*``) that indicates all actions, for example, **"Action":["List*", "Get*"]**.                                                                                                                                                                          | Optional. Select either **Action** or **NotAction**.       |
   +--------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+------------------------------------------------------------+
   | NotAction    | An exception to a list of actions in the statement. All actions are performed except the ones specified in **NotAction**. This parameter has the same value format as **Action**.                                                                                                                                                                                                                                                               | Optional. Select either **Action** or **NotAction**.       |
   +--------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+------------------------------------------------------------+
   | Effect       | Whether the permission in a statement is allowed or denied. The value is **Allow** or **Deny**.                                                                                                                                                                                                                                                                                                                                                 | Mandatory                                                  |
   +--------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+------------------------------------------------------------+
   | Resource     | Resources on which the statement takes effect. The wildcard (``*``) is supported, indicating all resources.                                                                                                                                                                                                                                                                                                                                     | Optional. Select either **Resource** or **NotResource**.   |
   +--------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+------------------------------------------------------------+
   | NotResource  | An exception to a list of resources in a statement. A policy is not applied to the resources specified in **NotResource**. This parameter has the same value format as **Resource**.                                                                                                                                                                                                                                                            | Optional. Select either **Resource** or **NotResource**.   |
   +--------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+------------------------------------------------------------+
   | Condition    | Conditions for a statement to take effect.                                                                                                                                                                                                                                                                                                                                                                                                      | Optional                                                   |
   +--------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+------------------------------------------------------------+

.. note::

   A statement must contain either **Action** or **NotAction**, either **Resource** or **NotResource**, and either **Principal** or **NotPrincipal**.

Principal/NotPrincipal
----------------------

**Principal** or **NotPrincipal** supported by OBS includes anonymous users, specific tenants, specific users, federated users, and agencies.

-  All (anonymous users)

   .. code-block::

      "Principal": {"ID": "*"}

   In the example, the wildcard (``*``) is used as a placeholder for Everyone/Anonymous. We strongly recommend that you do not use wildcards in the **Principal** element of the role's trust policy unless you have restricted access by using the **Condition** element in the policy.

-  Specific tenants

   If the tenant identifier is used as the authorizer in the policy, permissions in the policy statement can be granted to all roles, including all the users, contained in this tenant. The following example demonstrates how to specify a tenant as an authorizer.

   .. code-block::

      "Principal": { "ID": " domain/domainIdxxxx:user/*" }

   You can grant permissions to multiple tenants, as described in the following example:

   .. code-block::

      "Principal": {
        "ID": [
          "domain/domainIDxx1:user/useridxxxx",
          "domain/domainIDxx2:user/*"
        ]
      }

-  Specific users

   In the **Principal** element, user names are case sensitive.

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

The principals on OBS Console refer to the users which the bucket policies apply to. These users can be accounts, federated users or federated user groups, and IAM users. You can specify principals in either of the following ways:

-  **Include**: Specifies the users to whom the bucket policy applies.
-  **Exclude**: Specifies that to all users except the specified ones the bucket policy applies.

**Specifying IAM users under the current account**

With **Principal** set to **Current account**, you can select one or more IAM users under this account, so the bucket policy applies to the selected IAM users.

**Specifying another account**

With **Principal** set to **Other account**, you can enter an account ID. If you want to grant access only to IAM users under the account, you need to enter user IDs, and use commas (,) to separate one user ID from another.

.. note::

   To obtain the account ID and user ID, log in to the console as an IAM user and go to the **My Credentials** page.

**Specifying anonymous users**

To grant the bucket access to anyone, set **Principal** to **Other account** and enter a wildcard (``*``) as the account ID.

.. important::

   Exercise caution when granting bucket access permissions to anonymous users. If you grant the access permissions to anonymous users, anyone can access your bucket. You are advised to set restrictions on access requests. For example, you can allow the access requests from only one IP address.

.. _obs_40_0041__en-us_topic_0118394684_section1623516525350:

Action/NotAction
----------------

If a policy applies to a bucket, configure bucket-related actions; if the policy applies to the objects in a bucket, configure object-related actions.

Actions can be specified in either of the following ways:

-  **Include**: Specifies the actions on which the bucket policy takes effect.
-  **Exclude**: Specifies that on all actions except the specified ones the bucket policy takes effect.

**Bucket Actions**

.. table:: **Table 2** Action description

   +---------+----------------------------+--------------------------------------------------------------------+
   | Type    | Value                      | Description                                                        |
   +=========+============================+====================================================================+
   | General | \*                         | Indicates that all operations can be performed on a resource.      |
   +---------+----------------------------+--------------------------------------------------------------------+
   |         | Get\*                      | Indicates that all GET operations can be performed on a resource.  |
   +---------+----------------------------+--------------------------------------------------------------------+
   |         | Put\*                      | Indicates that all PUT operations can be performed on a resource.  |
   +---------+----------------------------+--------------------------------------------------------------------+
   |         | List\*                     | Indicates that all LIST operations can be performed on a resource. |
   +---------+----------------------------+--------------------------------------------------------------------+
   | Bucket  | CreateBucket               | Creates a bucket.                                                  |
   +---------+----------------------------+--------------------------------------------------------------------+
   |         | DeleteBucket               | Deletes a bucket.                                                  |
   +---------+----------------------------+--------------------------------------------------------------------+
   |         | ListBucket                 | Lists objects in a bucket, and gets the bucket metadata.           |
   +---------+----------------------------+--------------------------------------------------------------------+
   |         | ListBucketVersions         | Lists versioned objects in a bucket.                               |
   +---------+----------------------------+--------------------------------------------------------------------+
   |         | ListBucketMultipartUploads | Lists multipart upload tasks.                                      |
   +---------+----------------------------+--------------------------------------------------------------------+
   |         | GetBucketAcl               | Gets the bucket ACL information.                                   |
   +---------+----------------------------+--------------------------------------------------------------------+
   |         | PutBucketAcl               | Configures a bucket ACL.                                           |
   +---------+----------------------------+--------------------------------------------------------------------+
   |         | GetBucketCORS              | Gets the CORS configuration of a bucket.                           |
   +---------+----------------------------+--------------------------------------------------------------------+
   |         | PutBucketCORS              | Configures CORS for a bucket.                                      |
   +---------+----------------------------+--------------------------------------------------------------------+
   |         | GetBucketVersioning        | Gets the bucket versioning information.                            |
   +---------+----------------------------+--------------------------------------------------------------------+
   |         | PutBucketVersioning        | Configures versioning for a bucket.                                |
   +---------+----------------------------+--------------------------------------------------------------------+
   |         | GetBucketLocation          | Gets the bucket location.                                          |
   +---------+----------------------------+--------------------------------------------------------------------+
   |         | GetBucketLogging           | Gets the bucket logging information.                               |
   +---------+----------------------------+--------------------------------------------------------------------+
   |         | PutBucketLogging           | Configures logging for a bucket.                                   |
   +---------+----------------------------+--------------------------------------------------------------------+
   |         | GetBucketWebsite           | Obtains the static website configuration information of a bucket.  |
   +---------+----------------------------+--------------------------------------------------------------------+
   |         | PutBucketWebsite           | Configures static website hosting for a bucket.                    |
   +---------+----------------------------+--------------------------------------------------------------------+
   |         | DeleteBucketWebsite        | Cancels the static website hosting of a bucket.                    |
   +---------+----------------------------+--------------------------------------------------------------------+
   |         | GetLifecycleConfiguration  | Obtains the lifecycle rules of a bucket.                           |
   +---------+----------------------------+--------------------------------------------------------------------+
   |         | PutLifecycleConfiguration  | Configures a lifecycle rule for a bucket.                          |
   +---------+----------------------------+--------------------------------------------------------------------+

**Object Actions**

.. table:: **Table 3** Action description

   +---------+--------------------------+-------------------------------------------------------------------------------------------------------------+
   | Type    | Value                    | Description                                                                                                 |
   +=========+==========================+=============================================================================================================+
   | General | \*                       | Indicates that all operations can be performed on a resource.                                               |
   +---------+--------------------------+-------------------------------------------------------------------------------------------------------------+
   |         | Get\*                    | Indicates that all GET operations can be performed on a resource.                                           |
   +---------+--------------------------+-------------------------------------------------------------------------------------------------------------+
   |         | Put\*                    | Indicates that all PUT operations can be performed on a resource.                                           |
   +---------+--------------------------+-------------------------------------------------------------------------------------------------------------+
   |         | List\*                   | Indicates that all LIST operations can be performed on a resource.                                          |
   +---------+--------------------------+-------------------------------------------------------------------------------------------------------------+
   | Object  | GetObject                | Gets the content and metadata of an object.                                                                 |
   +---------+--------------------------+-------------------------------------------------------------------------------------------------------------+
   |         | GetObjectVersion         | Gets the content and metadata of a specified object version.                                                |
   +---------+--------------------------+-------------------------------------------------------------------------------------------------------------+
   |         | PutObject                | Performs PUT upload, POST upload, multipart upload, initialization of uploaded parts, and merging of parts. |
   +---------+--------------------------+-------------------------------------------------------------------------------------------------------------+
   |         | GetObjectAcl             | Gets the object ACL information.                                                                            |
   +---------+--------------------------+-------------------------------------------------------------------------------------------------------------+
   |         | GetObjectVersionAcl      | Gets the ACL information of a specified object version.                                                     |
   +---------+--------------------------+-------------------------------------------------------------------------------------------------------------+
   |         | PutObjectAcl             | Configures the ACL for an object.                                                                           |
   +---------+--------------------------+-------------------------------------------------------------------------------------------------------------+
   |         | PutObjectVersionAcl      | Configures the ACL for a specified object version.                                                          |
   +---------+--------------------------+-------------------------------------------------------------------------------------------------------------+
   |         | DeleteObject             | Deletes an object.                                                                                          |
   +---------+--------------------------+-------------------------------------------------------------------------------------------------------------+
   |         | DeleteObjectVersion      | Deletes a specified object version.                                                                         |
   +---------+--------------------------+-------------------------------------------------------------------------------------------------------------+
   |         | ListMultipartUploadParts | Lists uploaded parts.                                                                                       |
   +---------+--------------------------+-------------------------------------------------------------------------------------------------------------+
   |         | AbortMultipartUpload     | Cancels a multipart upload.                                                                                 |
   +---------+--------------------------+-------------------------------------------------------------------------------------------------------------+

Resource/NotResource
--------------------

The resources supported by OBS are as follows:

-  *bucketname* (bucket operation): The **Action** drop-down list box contains the list of supported bucket actions. If you want to perform the listed operations on the bucket, set **Resource** to the bucket name.
-  *bucketname/objectname* (object operation): The **Action** drop-down list box contains the list of supported object actions. If you want to respond to an object in a bucket, set **Resource** to *bucketname/objectname*. **objectname** supports wildcards. For example, if you have permissions on the directory object in a bucket, set **Resource** to ``"bucketname/directory/*"``. If you have permissions on all the objects in a bucket, set **Resource** to ``"bucketname/*"``. If permissions for both a bucket and its objects need to be granted, set **Resource** to **["examplebucket/*","examplebucket"]**.

The following example policy grants all operation permissions on **examplebucket** (including the bucket and its objects) to user1 whose user ID is **71f3901173514e6988115ea2c26d1999** under account **b4bf1b36d9ca43d984fbcb9491b6fce9** (account ID).

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

On OBS Console, resources can be a bucket or objects in the bucket.

Resources can be specified in either of the following ways:

-  **Include**: Specifies the OBS resources on which the bucket policy takes effect.
-  **Exclude**: Specifies that on all OBS resources except the specified ones the bucket policy takes effect.

**Specifying the bucket as the resource**

To specify the current bucket as the resource, keep the resource text box empty. When configuring actions for the policy, select bucket related actions.

**Specifying objects as the resources**

When objects in a bucket are specified as the resources, configure object-related actions in the bucket policy. The following are examples of how to specify objects as resources.

-  For an object, enter the object name (including its folder name if any). For example, if the specified resource is the **example.jpg** file in the **imgs-folder** folder in the bucket, enter the following content in the resource text box:

   **imgs-folder/example.jpg**

-  For an object set, the wildcard asterisk (*) should be used. The asterisk (*) indicates an empty string or any combination of multiple characters. The format rules are as follows:

   -  Use only one asterisk (*) to indicate all objects in a bucket.

   -  Use *Object name prefix*\ \* to indicate objects starting with this prefix in a bucket. Example:

      imgs\*

   -  Use \*\ *Object name suffix* to indicate objects ending with this suffix in a bucket. Example:

      \*.jpg

.. note::

   Use commas (,) to separate one object (or object set) from another.

Condition
---------

In addition to the effect, principal, resources, and actions, you can also specify the conditions under which a bucket policy takes effect. The bucket policy takes effect only when its condition expressions match values contained in the request. Conditions are optional. You can choose whether to configure them.

For example, if account A needs to have full control over an object uploaded by account B to bucket **example** of account A, the **x-obs-acl** key must be specified in the upload request and the policy effect must be set to **Allow** for account A. The complete condition expression is as follows:

==================== ========= =========================
Conditional Operator Key       Value
==================== ========= =========================
StringEquals         x-obs-acl bucket-owner-full-control
==================== ========= =========================

A condition consists of three parts: conditional operator, key, and value. If there are multiple identical keys in the same conditional operator, only the last key is retained. Conditional operators and keys are mutually restricted:

-  If you select a conditional operator of the string type, for example, **StringEquals**, the key can only be of the string type, for example, **UserAgent**.
-  Likewise, if a key of the date type is selected, for example, **CurrentTime**, the conditional operator can only be of the date type, for example, **DateEquals**.

:ref:`Table 4 <obs_40_0041__en-us_topic_0118394684_table18965458>` lists the general condition types that you can specify.

.. _obs_40_0041__en-us_topic_0118394684_table18965458:

.. table:: **Table 4** Conditional operators

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
   | Numeric               | NumericEquals             | Strict matching. Short version: numeq                                                                                                                                                        |
   |                       |                           |                                                                                                                                                                                              |
   |                       |                           | **Numeric** indicates a data type expressed in numbers.                                                                                                                                      |
   +-----------------------+---------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   |                       | NumericNotEquals          | Strict negated matching. Short version: numneq                                                                                                                                               |
   +-----------------------+---------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   |                       | NumericLessThan           | "Less than" matching. Short version: numlt                                                                                                                                                   |
   +-----------------------+---------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   |                       | NumericLessThanEquals     | "Less than or equals" matching. Short version: numlteq                                                                                                                                       |
   +-----------------------+---------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   |                       | NumericGreaterThan        | "Greater than" matching. Short version: numgt                                                                                                                                                |
   +-----------------------+---------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   |                       | NumericGreaterThanEquals  | "Greater than or equals" matching. Short version: numgteq                                                                                                                                    |
   +-----------------------+---------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Date                  | DateEquals                | Strict matching. Short version: dateeq                                                                                                                                                       |
   +-----------------------+---------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   |                       | DateNotEquals             | Strict negated matching. Short version: dateneq                                                                                                                                              |
   +-----------------------+---------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   |                       | DateLessThan              | Indicates that the date is earlier than a specific date. Short version: datelt                                                                                                               |
   +-----------------------+---------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   |                       | DateLessThanEquals        | Indicates that the date is earlier than or equal to a specific date. Short version: datelteq                                                                                                 |
   +-----------------------+---------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   |                       | DateGreaterThan           | Indicates that the date is later than a specific date. Short version: dategt                                                                                                                 |
   +-----------------------+---------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   |                       | DateGreaterThanEquals     | Indicates that the date is later than or equal to a specific date. Short version: dategteq                                                                                                   |
   +-----------------------+---------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Boolean               | Bool                      | Strict Boolean matching                                                                                                                                                                      |
   +-----------------------+---------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | IP address            | IpAddress                 | Specified IP address or IP address range                                                                                                                                                     |
   +-----------------------+---------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   |                       | NotIpAddress              | All IP addresses excluding the specified IP address or IP address range                                                                                                                      |
   +-----------------------+---------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

.. note::

   Elements in a condition are case sensitive. The date format complies with the ISO 8601 standard, for example, **2015-07-01T12:00:00Z**.

Each condition can contain multiple key-value pairs. The **Condition** combination in the following figure indicates that the request time ranges from **2015-07-01T12:00:00Z** to **2018-04-16T15:00:00Z** and the request IP address range is **192.168.176.0/24** or **192.168.143.0/24**.

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

Keys in a condition can be classified into three types: general keys, keys related to bucket actions, and keys related to object actions.

The following table lists the keys that are not related to actions.

.. table:: **Table 5** General keys

   +-----------------+------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Key             | Type       | Description                                                                                                                                                 |
   +=================+============+=============================================================================================================================================================+
   | CurrentTime     | Date       | Indicates the date when the request is received by the server. The date format must comply with ISO 8601.                                                   |
   +-----------------+------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | EpochTime       | Numeric    | Indicates the time when the request is received by the server, which is expressed as seconds since 1970.01.01 00:00:00 UTC, regardless of the leap seconds. |
   +-----------------+------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | SecureTransport | Bool       | Indicates whether requests are encrypted using SSL.                                                                                                         |
   +-----------------+------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | SourceIp        | IP address | Source IP address from which the request is sent                                                                                                            |
   +-----------------+------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | UserAgent       | String     | Requested client software agent                                                                                                                             |
   +-----------------+------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Referer         | String     | Indicates the link from which the request is sent.                                                                                                          |
   +-----------------+------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------+

Keys in a condition must be used in certain actions. The following table lists the mapping between actions and the keys in a condition.

.. table:: **Table 6** Keys related to bucket actions

   +--------------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Action             | Optional Key    | Description                                                                                                                                                                                                                                                           | Remarks                                                                                                                                                                                                                                                                                                                                                                                     |
   +====================+=================+=======================================================================================================================================================================================================================================================================+=============================================================================================================================================================================================================================================================================================================================================================================================+
   | ListBucket         | prefix          | Type: String. Lists objects that begin with the specified prefix.                                                                                                                                                                                                     | If **prefix**, **delimiter**, and **max-keys** are configured, the key-value pair meeting the conditions must be specified in the List operation for the bucket policy to take effect.                                                                                                                                                                                                      |
   |                    |                 |                                                                                                                                                                                                                                                                       |                                                                                                                                                                                                                                                                                                                                                                                             |
   |                    |                 |                                                                                                                                                                                                                                                                       | For example, if a bucket policy (with the conditional operator set to **NumericEquals**, the key to **max-keys**, and the value to **100**) that allows anonymous users to read data is configured for a bucket, the anonymous users must add **?max-keys=100** to the end of the bucket domain name for listing objects. The listed objects are the first 100 objects in alphabetic order. |
   +--------------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   |                    | delimiter       | Type: String. Groups objects in a bucket.                                                                                                                                                                                                                             |                                                                                                                                                                                                                                                                                                                                                                                             |
   +--------------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   |                    | max-keys        | Type: Numeric. Sets the maximum number of objects. Returned objects are listed in alphabetic order.                                                                                                                                                                   |                                                                                                                                                                                                                                                                                                                                                                                             |
   +--------------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | ListBucketVersions | prefix          | Type: String. Lists multi-version objects whose name starts with the specified prefix.                                                                                                                                                                                |                                                                                                                                                                                                                                                                                                                                                                                             |
   +--------------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   |                    | delimiter       | Type: String. Groups objects of different versions in a bucket.                                                                                                                                                                                                       |                                                                                                                                                                                                                                                                                                                                                                                             |
   +--------------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   |                    | max-keys        | Type: Numeric. Sets the maximum number of objects. Returned objects are listed in alphabetic order.                                                                                                                                                                   |                                                                                                                                                                                                                                                                                                                                                                                             |
   +--------------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | PutBucketAcl       | x-obs-acl       | Type: String. Configures the bucket ACL. When modifying a bucket ACL, you can use the request that contains a canned ACL setting in its header. Value options of a canned ACL setting: **private|public-read|public-read-write|bucketowner-read|log-delivery-write**. | None                                                                                                                                                                                                                                                                                                                                                                                        |
   +--------------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

.. table:: **Table 7** Keys related to object actions

   +---------------------+------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Action              | Optional Key                 | Description                                                                                                                                                                                                                                                                                                                       |
   +=====================+==============================+===================================================================================================================================================================================================================================================================================================================================+
   | PutObject           | x-obs-acl                    | Type: String. Configures the object ACL. When uploading an object, you can use the request that contains a canned ACL setting in its header. Value options of a canned ACL setting: **private|public-read|public-read-write|bucketowner-read|bucket-owner-full-control|log-delivery-write**.                                      |
   +---------------------+------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   |                     | x-obs-copy-source            | Type: String. Specifies names of the source bucket and the source object. Format: **/**\ *bucketname*\ **/**\ *keyname*                                                                                                                                                                                                           |
   +---------------------+------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   |                     | x-obs-metadata-directive     | Type: String. Specifies whether to copy the metadata from the source object or replace with the metadata in the request. The value can be **COPY** or **REPLACE**.                                                                                                                                                                |
   +---------------------+------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   |                     | x-obs-server-side-encryption | Type: String. Specifies that objects in a bucket are encrypted using SSE-KMS before they are stored. The value is **kms**.                                                                                                                                                                                                        |
   +---------------------+------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | PutObjectAcl        | x-obs-acl                    | Type: String. Configures the object ACL. When uploading an object, you can use the request that contains a canned ACL setting in its header. Value options of a canned ACL setting: **private|public-read|public-read-write|bucketowner-read|bucket-owner-full-control|log-delivery-write**.                                      |
   +---------------------+------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | GetObjectVersion    | versionId                    | Type: String. Obtains the object with the specified version ID.                                                                                                                                                                                                                                                                   |
   +---------------------+------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | GetObjectVersionAcl | versionId                    | Type: String. Obtains the ACL of the object with the specified version ID.                                                                                                                                                                                                                                                        |
   +---------------------+------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | PutObjectVersionAcl | versionId                    | Type: String. Specifies a version ID.                                                                                                                                                                                                                                                                                             |
   +---------------------+------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   |                     | x-obs-acl                    | Type: String. Configures the ACL of the object with the specified version ID. When uploading an object, you can use the request that contains a canned ACL setting in its header. Value options of a canned ACL setting: **private|public-read|public-read-write|bucketowner-read|bucket-owner-full-control|log-delivery-write**. |
   +---------------------+------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | DeleteObjectVersion | versionId                    | Type: String. Deletes the object with the specified version ID.                                                                                                                                                                                                                                                                   |
   +---------------------+------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Policy Permission Judgment Logic
--------------------------------

A policy may pose any of the three results for each statement: **Explicit Deny**, **Allow**, and **Default Deny**. If a bucket policy contains multiple statements, the policy determines which statement prevails according to the following rules:

1. If conditions in any statement of a policy are not met, the policy poses a default deny result.

2. An explicit deny overrides an allow.

3. An allow overrides a default deny.

4. Statements can be in any order in a policy.

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

If an ACL and a bucket policy are applied together to an account, an explicit deny in the bucket policy overrides the allow in the ACL.

If a bucket policy and an IAM policy are applied together to an account, an explicit deny overrides the allow, and an allow overrides the default deny.

SSE-KMS server-side encrypted object does not support Bucket ACL/Policy for cross-tenant authorization.
