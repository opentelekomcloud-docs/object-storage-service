:original_name: obs_40_0004.html

.. _obs_40_0004:

Bucket Policy Overview
======================

Bucket Policies
---------------

A bucket policy applies to an OBS bucket and the objects in the bucket. Bucket policies let a bucket owner grant IAM users or other accounts permissions on the bucket and its objects.

.. note::

   -  Creating a bucket and obtaining a bucket list are service-level operations. To obtain such operation permissions, you need to configure :ref:`IAM permissions <obs_40_0014>`.
   -  Due to data caching, it takes 5 minutes at most for a bucket policy to take effect.


Bucket Policy Overview
----------------------

A bucket policy is attached to a bucket and objects in the bucket. An OBS bucket owner can use bucket policies to grant IAM users, other accounts, or anonymous users the permissions to operate buckets and objects in the buckets. OBS provides standard and advanced bucket policies.

**Standard Bucket Policies**:

There are three options for standard bucket policies.

-  **Private**: No access beyond the bucket ACL settings is granted.
-  **Public Read**: Any user can read objects in the bucket.
-  **Public Read and Write**: Any user can read, write, and delete objects in the bucket.

After a bucket is created, the default bucket policy is **Private**. Only the bucket owner has the full control permissions over the bucket. To ensure data security, it is recommended that you do not use the **Public Read** or **Public Read and Write** policies.

.. table:: **Table 1** Standard bucket policies

   +-----------------+-----------------+------------------------------+------------------------------+
   | Parameter       | Private         | Public Read                  | Public Read and Write        |
   +=================+=================+==============================+==============================+
   | Effect          | N/A             | Allow                        | Allow                        |
   +-----------------+-----------------+------------------------------+------------------------------+
   | Principal       | N/A             | \* (Any user)                | \* (Any user)                |
   +-----------------+-----------------+------------------------------+------------------------------+
   | Resources       | N/A             | \* (All objects in a bucket) | \* (All objects in a bucket) |
   +-----------------+-----------------+------------------------------+------------------------------+
   | Actions         | N/A             | -  GetObject                 | -  GetObject                 |
   |                 |                 | -  GetObjectVersion          | -  GetObjectVersion          |
   |                 |                 | -  HeadBucket                | -  PutObject                 |
   |                 |                 | -  ListBucket                | -  DeleteObject              |
   |                 |                 |                              | -  DeleteObjectVersion       |
   |                 |                 |                              | -  HeadBucket                |
   |                 |                 |                              | -  ListBucket                |
   +-----------------+-----------------+------------------------------+------------------------------+
   | Conditions      | N/A             | N/A                          | N/A                          |
   +-----------------+-----------------+------------------------------+------------------------------+

**Custom Bucket Policy**:

The following three modes are provided to facilitate quick configuration of a custom bucket policy:

-  **Read-only**: With the **Read-only** mode, you only need to specify the **Principal** (authorized users). Then the authorized users have the read permission for the bucket and objects in the bucket, and can perform all GET operations on these resources.
-  **Read and write**: With the **Read and write** mode, you only need to specify the **Principal** (authorized users). Then the authorized users have the full control permissions for the bucket and objects in the bucket, and can perform any operation on these resources.
-  **Customized**: With the **Customized** mode, you can define the specific operation permissions that you want to authorize to users and accounts by configuring the parameters of **Effect**, **Principal**, **Resources**, **Actions**, and **Conditions**. For details, see `Bucket Policy Parameters <https://docs.otc.t-systems.com/en-us/usermanual/obs/obs_03_0074.html>`__.

.. note::

   On OBS Console, when you use the custom bucket policy to authorize other users with resource operation permissions, you also need to authorize the users with the bucket read permission **ListBucket** (leave the resource name blank to indicate that the policy takes effect on the entire bucket). Otherwise, the users have no permission to access the bucket.

Application Scenarios of a Bucket Policy
----------------------------------------

-  Grant other accounts the permissions to access OBS resources.
-  Grant IAM users the permissions to access buckets.

Policy Structure and Syntax
---------------------------

A bucket policy is in JSON format. The format is as follows:

.. code-block::

   {
   "Statement" : [
       {
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
      "Statement":[
          {
              "Sid": "ExampleStatementID1",
              "Principal":{
                  "ID":[
                      "domain/account ID",
                      "domain/account ID:user/User ID"
                  ]
              },
              "Effect":"Allow",
              "Action":[
                  "CreateBucket",
                  "DeleteBucket"
              ],
              "Resource":"000-02/key01",
              "Condition":{
                  "NumericNotEquals":{
                      "Referer":"sdf"
                  },
                  "StringNotLike":{
                      "Delimiter":"ouio"
                  }
              }
          }
      ]
    }

A bucket policy comprises one or more statements. Each statement contains the following elements:

.. table:: **Table 2** Statement elements

   +-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+------------------------------------------------------------+
   | Element               | Description                                                                                                                                                                                                                                                  | Mandatory or Optional                                      |
   +=======================+==============================================================================================================================================================================================================================================================+============================================================+
   | Sid                   | ID of a statement. The value is a string that describes the statement.                                                                                                                                                                                       | Optional                                                   |
   +-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+------------------------------------------------------------+
   | Principal             | Domains (accounts) and users (IAM users) to which the statement applies. The wildcard (``*``) is supported, indicating all users.                                                                                                                            | Optional. Select either **Principal** or **NotPrincipal**. |
   |                       |                                                                                                                                                                                                                                                              |                                                            |
   |                       | -  When permissions are granted to all IAM users in a domain (account), the principal format is ``domain/domainid:user/*``.                                                                                                                                  |                                                            |
   |                       | -  When a user is authorized, the principal format is *domain/domainid:user/userId* or *domain/domainid:user/userName*.                                                                                                                                      |                                                            |
   +-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+------------------------------------------------------------+
   | NotPrincipal          | An exception to a list of principals in the statement. You can deny access to all principals except the ones named in the **NotPrincipal** element. This parameter has the same value format as **Principal**.                                               | Optional. Select either **Principal** or **NotPrincipal**. |
   +-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+------------------------------------------------------------+
   | Effect                | Whether the permission in a statement is allowed or denied. The value is **Allow** or **Deny**.                                                                                                                                                              | Mandatory                                                  |
   +-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+------------------------------------------------------------+
   | Action                | Actions which a statement applies to. This parameter specifies a set of all the operations supported by OBS. Its values are case insensitive. You can use a wildcard character (``*``) to indicate all actions, for example, **"Action":["List*", "Get*"]**. | Optional. Select either **Action** or **NotAction**.       |
   +-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+------------------------------------------------------------+
   | NotAction             | An exception to a list of actions in the statement. All actions are performed except the ones specified in **NotAction**. The value of this element is similar to **Action**.                                                                                | Optional. Select either **Action** or **NotAction**.       |
   +-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+------------------------------------------------------------+
   | Resource              | Resources on which the statement takes effect. The wildcard (``*``) is supported, indicating all resources.                                                                                                                                                  | Optional. Select either **Resource** or **NotResource**.   |
   +-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+------------------------------------------------------------+
   | NotResource           | An exception to a list of resources in a statement. A policy is not applied to the resources specified in **NotResource**. The value of this parameter is similar to that of **Resource**.                                                                   | Optional. Select either **Resource** or **NotResource**.   |
   +-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+------------------------------------------------------------+
   | Condition             | Conditions for a statement to take effect.                                                                                                                                                                                                                   | Optional                                                   |
   +-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+------------------------------------------------------------+

For details about each element, see `Bucket Policy Parameters <https://docs.otc.t-systems.com/en-us/usermanual/obs/obs_03_0074.html>`__.

Configuring a Bucket Policy
---------------------------

-  `Configuring a Standard Bucket Policy <https://docs.otc.t-systems.com/en-us/usermanual/obs/obs_03_0142.html>`__
-  `Configuring a Custom Bucket Policy (Common Mode) <https://docs.otc.t-systems.com/en-us/usermanual/obs/obs_03_0123.html>`__
-  `Configuring a Custom Bucket Policy (Coding Mode) <https://docs.otc.t-systems.com/en-us/usermanual/obs/obs_03_0141.html>`__

Bucket Policy Example
---------------------

-  **Example 1: Grant an IAM user the specified operation permission on all objects in a specified bucket.**

   The following policy grants the PutObject and PutObjectAcl permissions to the IAM user **71f3901173514e6988115ea2c26d1999** under account **b4bf1b36d9ca43d984fbcb9491b6fce9**.

   .. code-block::

      {
          "Statement":[
          {
            "Sid":"AddCannedAcl",
            "Effect":"Allow",
            "Principal": {"ID": ["domain/b4bf1b36d9ca43d984fbcb9491b6fce9:user/71f3901173514e6988115ea2c26d1999"]},
            "Action":["PutObject","PutObjectAcl"],
            "Resource":["examplebucket/*"]
          }
        ]
      }

-  **Example 2: Grant all permissions for a specified bucket to an IAM user.**

   The following policy grants all permissions for bucket **examplebucket** and its objects to the user **71f3901173514e6988115ea2c26d1999** in account **b4bf1b36d9ca43d984fbcb9491b6fce9**.

   .. code-block::

      {
          "Statement":[
          {
            "Sid":"test",
            "Effect":"Allow",
            "Principal": {"ID": ["domain/b4bf1b36d9ca43d984fbcb9491b6fce9:user/71f3901173514e6988115ea2c26d1999"]},
            "Action":["*"],
            "Resource":[
              "examplebucket/*",
              "examplebucket"
            ]
          }
        ]
      }

-  **Example 3: Grant all permissions except the object deletion permission to an OBS user.**

   The following policy grants the user **71f3901173514e6988115ea2c26d1999** under the account **b4bf1b36d9ca43d984fbcb9491b6fce9** all permissions for the **examplebucket** bucket, excluding the permission to delete objects.

   .. code-block::

      {
          "Statement":[
          {
            "Sid":"test1",
            "Effect":"Allow",
            "Principal": {"ID": ["domain/b4bf1b36d9ca43d984fbcb9491b6fce9:user/71f3901173514e6988115ea2c26d1999"]},
            "Action":["*"],
            "Resource":["examplebucket/*"]
          },
          {
            "Sid":"test2",
            "Effect":"Deny",
            "Principal": {"ID": ["domain/b4bf1b36d9ca43d984fbcb9491b6fce9:user/71f3901173514e6988115ea2c26d1999"]},
            "Action":["DeleteObject"],
            "Resource":["examplebucket/*"]
          }
        ]
      }

-  **Example 4: Grant the read-only permission on a specified object to anonymous users.**

   The following policy grants anonymous users the **GetObject** permissions to download object **exampleobject** from bucket **examplebucket**, allowing everyone to read data of the **exampleobject** object.

   .. code-block::

      {
          "Statement":[
          {
            "Sid":"AddPerm",
            "Effect":"Allow",
            "Principal": "*",
            "Action":["GetObject"],
            "Resource":["examplebucket/exampleobject"]
          }
        ]
      }

-  **Example 5: Allow access only from a specific IP address.**

   The following policy grants the permission to allow users to access from the specific IP address range to perform any operations on OBS. The range is 192.168.0.*, excluding 192.168.0.1.

   You can use **IpAddress** and **NotIpAddress** conditions, and the **SourceIp** (in OBS range) condition key. The value of **SourceIp** is a CIDR notation described in RFC 4632.

   .. code-block::

      {
        "Statement": [
          {
            "Sid": "IPAllow",
            "Effect": "Allow",
            "Principal": "*",
            "Action": "*",
            "Resource": "examplebucket/*",
            "Condition": {
               "IpAddress": {"SourceIp": "192.168.0.0/24"},
               "NotIpAddress": {"SourceIp": "192.168.0.1/32"}
            }
          }
        ]
      }
