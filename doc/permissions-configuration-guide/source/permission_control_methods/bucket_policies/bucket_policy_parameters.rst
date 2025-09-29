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

   +-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+------------------------------------------------------------+
   | Element               | Description                                                                                                                                                                                                                                                                                                                                                                                      | Mandatory/Optional                                         |
   +=======================+==================================================================================================================================================================================================================================================================================================================================================================================================+============================================================+
   | Sid                   | ID of the statement. The value is a string that describes the statement.                                                                                                                                                                                                                                                                                                                         | Optional                                                   |
   +-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+------------------------------------------------------------+
   | Principal             | Domains and users that a statement applies to. The value can be a wildcard (``*``), indicating all users. To grant permissions to all users in a domain, set **Principal** to **domain/**\ *domainid*\ **:user/\***. To grant permissions to a specific user in a domain, set **Principal** to **domain/**\ *domainid*\ **:user/**\ *userId* or **domain/**\ *domainid*\ **:user/**\ *userName*. | Optional. Select either **Principal** or **NotPrincipal**. |
   +-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+------------------------------------------------------------+
   | NotPrincipal          | Users that the statement does not apply to. Its value has the same format as **Principal**.                                                                                                                                                                                                                                                                                                      | Optional. Select either **NotPrincipal** or **Principal**. |
   |                       |                                                                                                                                                                                                                                                                                                                                                                                                  |                                                            |
   |                       | The following gives an example that denies all operations performed by users except the specified IAM user.                                                                                                                                                                                                                                                                                      |                                                            |
   |                       |                                                                                                                                                                                                                                                                                                                                                                                                  |                                                            |
   |                       | *domain_id* indicates the account ID, and *user_id* indicates the IAM user ID.                                                                                                                                                                                                                                                                                                                   |                                                            |
   |                       |                                                                                                                                                                                                                                                                                                                                                                                                  |                                                            |
   |                       | ::                                                                                                                                                                                                                                                                                                                                                                                               |                                                            |
   |                       |                                                                                                                                                                                                                                                                                                                                                                                                  |                                                            |
   |                       |    {                                                                                                                                                                                                                                                                                                                                                                                             |                                                            |
   |                       |        "Statement": [                                                                                                                                                                                                                                                                                                                                                                            |                                                            |
   |                       |            {                                                                                                                                                                                                                                                                                                                                                                                     |                                                            |
   |                       |                "Effect": "Deny",                                                                                                                                                                                                                                                                                                                                                                 |                                                            |
   |                       |                "Action": ["*"],                                                                                                                                                                                                                                                                                                                                                                  |                                                            |
   |                       |                "Resource": [                                                                                                                                                                                                                                                                                                                                                                     |                                                            |
   |                       |                    "examplebucket/*",                                                                                                                                                                                                                                                                                                                                                            |                                                            |
   |                       |                    "examplebucket"                                                                                                                                                                                                                                                                                                                                                               |                                                            |
   |                       |                ],                                                                                                                                                                                                                                                                                                                                                                                |                                                            |
   |                       |                "NotPrincipal": {                                                                                                                                                                                                                                                                                                                                                                 |                                                            |
   |                       |                    "ID": [                                                                                                                                                                                                                                                                                                                                                                       |                                                            |
   |                       |                        "domain/domain_id:user/user_id",                                                                                                                                                                                                                                                                                                                                          |                                                            |
   |                       |                        "domain/domain_id:root"                                                                                                                                                                                                                                                                                                                                                   |                                                            |
   |                       |                    ]                                                                                                                                                                                                                                                                                                                                                                             |                                                            |
   |                       |                }                                                                                                                                                                                                                                                                                                                                                                                 |                                                            |
   |                       |            }                                                                                                                                                                                                                                                                                                                                                                                     |                                                            |
   |                       |         ]                                                                                                                                                                                                                                                                                                                                                                                        |                                                            |
   |                       |    }                                                                                                                                                                                                                                                                                                                                                                                             |                                                            |
   +-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+------------------------------------------------------------+
   | Action                | Actions that the statement applies to. This parameter specifies a set of all the operations supported by OBS. Its values are case insensitive. The value can be a wildcard character (``*``) that indicates all operations. For example: **"Action":["List*","Get*"]**.                                                                                                                          | Optional. Select either **Action** or **NotAction**.       |
   +-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+------------------------------------------------------------+
   | NotAction             | Actions that are not controlled by this statement. Its value has the same format as **Action**.                                                                                                                                                                                                                                                                                                  | Optional. Select either **Action** or **NotAction**.       |
   +-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+------------------------------------------------------------+
   | Effect                | Whether the permission in a statement is **Allow** or **Deny**.                                                                                                                                                                                                                                                                                                                                  | Mandatory                                                  |
   +-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+------------------------------------------------------------+
   | Resource              | Resources that the statement will apply to. You can use a wildcard (``*``) to indicate all resources.                                                                                                                                                                                                                                                                                            | Optional. Select either **Resource** or **NotResource**.   |
   +-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+------------------------------------------------------------+
   | NotResource           | Resources that the statement will not apply to. Its value has the same format as **Resource**.                                                                                                                                                                                                                                                                                                   | Optional. Select either **Resource** or **NotResource**.   |
   +-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+------------------------------------------------------------+
   | Condition             | Conditions for the statement to take effect.                                                                                                                                                                                                                                                                                                                                                     | Optional                                                   |
   +-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+------------------------------------------------------------+

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

For details, see `Bucket Actions <https://docs.otc.t-systems.com/object-storage-service/api-ref/iam_policies_and_supported_actions/bucket_actions.html>`__.

**Object Actions**

For details, see `Object Actions <https://docs.otc.t-systems.com/object-storage-service/api-ref/iam_policies_and_supported_actions/object_actions.html>`__.

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

**Condition Operators**

A condition operator, a condition key, and a condition value together constitute a complete condition statement. A policy can be applied only when its request conditions are met. :ref:`Table 2 <obs_40_0041__en-us_topic_0118394684_table18965458>` lists the condition operators available for statements. If a condition operator corresponds to multiple identical keys, only the last key is retained.

.. _obs_40_0041__en-us_topic_0118394684_table18965458:

.. table:: **Table 2** Condition operators

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

**Condition Keys**

Condition keys can be classified into general keys, keys related to actions on buckets, and keys related to actions on objects. :ref:`Table 3 <obs_40_0041__table6707152645718>` lists the general keys.

.. _obs_40_0041__table6707152645718:

.. table:: **Table 3** General keys

   +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------+
   | Key                   | Type                  | Description                                                                                                                                    |
   +=======================+=======================+================================================================================================================================================+
   | CurrentTime           | Date                  | Date when the request was received by the server. The date format must comply with ISO 8601.                                                   |
   +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------+
   | EpochTime             | Numeric               | Time when the request was received by the server, which was expressed as seconds since 1970.01.01 00:00:00 UTC, regardless of the leap seconds |
   +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------+
   | SecureTransport       | Boolean               | Whether the request was encrypted using SSL                                                                                                    |
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

Action-related condition keys can be used only when a specific action is selected. :ref:`Table 4 <obs_40_0041__table1972610267573>` and :ref:`Table 5 <obs_40_0041__table14742526145718>` list the mapping between actions and condition keys.

.. _obs_40_0041__table1972610267573:

.. table:: **Table 4** Keys related to bucket actions

   +--------------------+--------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+------------------------------------+---------------------------------------+
   | Action             | Optional Key | Description                                                                                                                                                                                                                                                           | Remarks                                                                                                                                                                                                                                                                                                                                                                                     | Supported by IAM Policies (Yes/No) | Supported by Bucket Policies (Yes/No) |
   +====================+==============+=======================================================================================================================================================================================================================================================================+=============================================================================================================================================================================================================================================================================================================================================================================================+====================================+=======================================+
   | ListBucket         | prefix       | Type: String. Lists objects with the specified prefix.                                                                                                                                                                                                                | If **prefix**, **delimiter**, and **max-keys** are configured for a bucket policy, the List requests must contain the matched key-value pair.                                                                                                                                                                                                                                               | Yes                                | Yes                                   |
   |                    |              |                                                                                                                                                                                                                                                                       |                                                                                                                                                                                                                                                                                                                                                                                             |                                    |                                       |
   |                    |              |                                                                                                                                                                                                                                                                       | For example, if a bucket policy (with the condition operator set to **NumericEquals**, the key to **max-keys**, and the value to **100**) is configured to allow anonymous users to read data from a bucket, the List requests from the anonymous users must have **?max-keys=100** at the end of the bucket domain name. The listed objects are the first 100 objects in alphabetic order. |                                    |                                       |
   +--------------------+--------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+------------------------------------+---------------------------------------+
   |                    | delimiter    | Type: String. Groups objects in a bucket.                                                                                                                                                                                                                             |                                                                                                                                                                                                                                                                                                                                                                                             | Yes                                | Yes                                   |
   +--------------------+--------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+------------------------------------+---------------------------------------+
   |                    | max-keys     | Type: Numeric. Sets the maximum number of objects. Returned objects are listed in alphabetic order.                                                                                                                                                                   |                                                                                                                                                                                                                                                                                                                                                                                             | Yes                                | Yes                                   |
   +--------------------+--------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+------------------------------------+---------------------------------------+
   | ListBucketVersions | prefix       | Type: String. Lists multi-version objects with the specified prefix.                                                                                                                                                                                                  |                                                                                                                                                                                                                                                                                                                                                                                             | Yes                                | Yes                                   |
   +--------------------+--------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+------------------------------------+---------------------------------------+
   |                    | delimiter    | Type: String. Groups objects of different versions in a bucket.                                                                                                                                                                                                       |                                                                                                                                                                                                                                                                                                                                                                                             | Yes                                | Yes                                   |
   +--------------------+--------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+------------------------------------+---------------------------------------+
   |                    | max-keys     | Type: Numeric. Sets the maximum number of objects. Returned objects are listed in alphabetic order.                                                                                                                                                                   |                                                                                                                                                                                                                                                                                                                                                                                             | Yes                                | Yes                                   |
   +--------------------+--------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+------------------------------------+---------------------------------------+
   | PutBucketAcl       | acl          | Type: String. Configures the bucket ACL. When modifying a bucket ACL, you can use the request that contains a canned ACL setting in its header. Value options of a canned ACL setting: **private|public-read|public-read-write|bucketowner-read|log-delivery-write**. | None                                                                                                                                                                                                                                                                                                                                                                                        | Yes                                | Yes                                   |
   +--------------------+--------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+------------------------------------+---------------------------------------+

.. _obs_40_0041__table14742526145718:

.. table:: **Table 5** Keys related to object actions

   +---------------------+------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+------------------------------------+---------------------------------------+
   | Action              | Optional Key           | Description                                                                                                                                                                                                                                                                                                                       | Supported by IAM Policies (Yes/No) | Supported by Bucket Policies (Yes/No) |
   +=====================+========================+===================================================================================================================================================================================================================================================================================================================================+====================================+=======================================+
   | PutObject           | acl                    | Type: String. Configures the object ACL. When uploading an object, you can use the request that contains a canned ACL setting in its header. Value options of a canned ACL setting: **private|public-read|public-read-write|bucketowner-read|bucket-owner-full-control|log-delivery-write**.                                      | Yes                                | Yes                                   |
   +---------------------+------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+------------------------------------+---------------------------------------+
   |                     | copy-source            | Type: String. Specifies names of the source bucket and the source object. Format: **/**\ *bucketname*\ **/**\ *keyname*                                                                                                                                                                                                           | Yes                                | Yes                                   |
   +---------------------+------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+------------------------------------+---------------------------------------+
   |                     | metadata-directive     | Type: String. Specifies whether to copy the metadata of the source object or replace with the metadata in the request. The value can be **COPY** or **REPLACE**.                                                                                                                                                                  | Yes                                | Yes                                   |
   +---------------------+------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+------------------------------------+---------------------------------------+
   |                     | server-side-encryption | Type: String. Specifies that objects in a bucket are encrypted using SSE-KMS before they are stored. The value is **kms**.                                                                                                                                                                                                        | Yes                                | Yes                                   |
   +---------------------+------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+------------------------------------+---------------------------------------+
   | PutObjectAcl        | acl                    | Type: String. Configures the object ACL. When uploading an object, you can use the request that contains a canned ACL setting in its header. Value options of a canned ACL setting: **private|public-read|public-read-write|bucketowner-read|bucket-owner-full-control|log-delivery-write**.                                      | Yes                                | Yes                                   |
   +---------------------+------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+------------------------------------+---------------------------------------+
   | GetObjectVersion    | versionId              | Type: String. Obtains the object with the specified version ID.                                                                                                                                                                                                                                                                   | Yes                                | Yes                                   |
   +---------------------+------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+------------------------------------+---------------------------------------+
   | GetObjectVersionAcl | versionId              | Type: String. Obtains the ACL of the object with the specified version ID.                                                                                                                                                                                                                                                        | Yes                                | Yes                                   |
   +---------------------+------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+------------------------------------+---------------------------------------+
   | PutObjectVersionAcl | versionId              | Type: String. Specifies a version ID.                                                                                                                                                                                                                                                                                             | Yes                                | Yes                                   |
   +---------------------+------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+------------------------------------+---------------------------------------+
   |                     | acl                    | Type: String. Configures the ACL of the object with the specified version ID. When uploading an object, you can use the request that contains a canned ACL setting in its header. Value options of a canned ACL setting: **private|public-read|public-read-write|bucketowner-read|bucket-owner-full-control|log-delivery-write**. | Yes                                | Yes                                   |
   +---------------------+------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+------------------------------------+---------------------------------------+
   | DeleteObjectVersion | versionId              | Type: String. Deletes the object with the specified version ID.                                                                                                                                                                                                                                                                   | Yes                                | Yes                                   |
   +---------------------+------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+------------------------------------+---------------------------------------+

Policy Permission Judgment Logic
--------------------------------

Each statement in a policy can have the action **Explicit Deny**, **Allow**, or **Default Deny**. If a bucket policy contains multiple statements with different actions, the final action is determined according to the following rules:

- If there are no **Explicit Deny** or **Allow**, **Default Deny** will apply.

- An explicit deny overrides an allow.

- An allow overrides a default deny.

- Statements can be in any order in a policy.

.. table:: **Table 6** Statement results

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
