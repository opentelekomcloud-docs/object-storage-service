:original_name: obs_03_0121.html

.. _obs_03_0121:

Configuring Fine-Grained Policies
=================================

Custom policies can be created to supplement the system-defined policies of OBS.

For details, see `Creating a Custom Policy <https://docs.otc.t-systems.com/identity-access-management/umn/user_guide/fine-grained_policy_management/creating_a_custom_policy.html>`__. The following provides examples of common OBS custom policies.

Example Custom Policies
-----------------------

-  Example 1: Grant users all OBS permissions.

   This policy allows users to perform any operation on OBS.

   .. code-block::

      {
          "Version": "1.1",
          "Statement": [
              {
                  "Effect": "Allow",
                  "Action": [
                      "obs:*:*"
                  ]
              }
          ]
      }

-  Example 2: Grant users all OBS Console permissions.

   This policy allows users to perform all operations on OBS Console.

   When a user logs in to OBS Console, the user may access resources of other services such as audit information in CTS. Therefore, in addition to the OBS permissions in example 1, you also need to configure the access permissions to other services. You need to configure the **Tenant Guest** permission for the global project and regional projects based on the services and regions that you use.

   .. code-block::

      {
          "Version": "1.1",
          "Statement": [
              {
                  "Effect": "Allow",
                  "Action": [
                      "obs:*:*"
                  ]
              }
          ]
      }

-  Example 3: Grant users the read-only permission for all directories in a bucket.

   This policy allows users to list and download all objects in bucket **obs-example**.

   .. code-block::

      {
          "Version": "1.1",
          "Statement": [
              {
                  "Effect": "Allow",
                  "Action": [
                      "obs:object:GetObject",
                      "obs:bucket:ListBucket"
                  ],
                  "Resource": [
                      "obs:*:*:object:obs-example/*",
                      "obs:*:*:bucket:obs-example"
                  ]
              }
          ]
      }

-  Example 4: Grant users the read-only permission for a specified directory in a bucket.

   This policy allows users to download objects in only the **my-project/** directory of bucket **obs-example**. Objects in other directories can be listed but cannot be downloaded.

   .. code-block::

      {
          "Version": "1.1",
          "Statement": [
              {
                  "Effect": "Allow",
                  "Action": [
                      "obs:object:GetObject",
                      "obs:bucket:ListBucket"
                  ],
                  "Resource": [
                      "obs:*:*:object:obs-example/my-project/*",
                      "obs:*:*:bucket:obs-example"
                  ]
              }
          ]
      }

-  Example 5: Grant users the read/write permissions for a specified directory in a bucket.

   This policy allows users to list, download, upload, and delete objects in the **my-project** directory of bucket **obs-example**.

   .. code-block::

      {
          "Version": "1.1",
          "Statement": [
              {
                  "Effect": "Allow",
                  "Action": [
                      "obs:object:GetObject",
                      "obs:object:ListMultipartUploadParts",
                      "obs:bucket:ListBucket",
                      "obs:object:DeleteObject",
                      "obs:object:PutObject"
                  ],
                  "Resource": [
                      "obs:*:*:object:obs-example/my-project/*",
                      "obs:*:*:bucket:obs-example"
                  ]
              }
          ]
      }

-  Example 6: Grant users all permissions for a bucket.

   This policy allows users to perform any operation on bucket **obs-example**.

   .. code-block::

      {
          "Version": "1.1",
          "Statement": [
              {
                  "Effect": "Allow",
                  "Action": [
                      "obs:*:*"
                  ],
                  "Resource": [
                      "obs:*:*:bucket:obs-example",
                      "obs:*:*:object:obs-example/*"
                  ]
              }
          ]
      }

-  Example 7: Grant users the permission to deny object upload.

   A deny policy must be used together with other policies. If the permissions assigned to a user contain both "Allow" and "Deny", the "Deny" permissions take precedence over the "Allow" permissions.

   If you grant the system policy OBS OperateAccess to a user but do not want the user to have the object upload permission (which is also a permission allowed by OBS OperateAccess), you can create a custom policy besides the OBS OperateAccess policy, to deny the user's upload permission. According to the authorization principle, the policy with the deny statement takes precedence, so that the user can perform all operations allowed by OBS OperateAccess, except uploading objects. The following is an example of a deny policy:

   .. code-block::

      {
          "Version": "1.1",
          "Statement": [
              {
                  "Effect": "Deny",
                  "Action": [
                      "obs:object:PutObject"
                  ]
              }
          ]
      }
