:original_name: obs_13_0014.html

.. _obs_13_0014:

Permissions Configuration
=========================

The use cases and main functions of object access control also work on files in parallel file systems. For more information, see `Permissions Configuration Guide <https://docs.otc.t-systems.com/object-storage-service/permissions-configuration-guide/differences_between_obs_permissions_control_methods.html>`__.

Differences Between File and Object Permission Configurations
-------------------------------------------------------------

To exactly match a specific directory, the resource path in the policy must end with a slash (/). When checking permissions, parallel file systems consider objects as directories. If the object identifier does not end with a slash (/), the system will add a slash (/) to the end of the object identifier and then performs a policy matching.

IAM Permission Configuration Examples
-------------------------------------

Example 1: Grant a user the permissions required to download **dir_1**, excluding its subdirectories.

In the following configuration, the resource path ends with a slash (/). In such case, a success response can be returned when **dir_1** or **dir_1/** is contained in the URL of a head request.

Note that this configuration is not applied to subdirectories or files in **dir_1**. Therefore, a failure response will be returned if a head request is sent to **dir_1/file1**.

.. code-block::

   {
       "Version": "1.1",
       "Statement": [
           {
               "Effect": "Allow",
               "Action": [
                   "obs:object:GetObject",
               ],
               "Resource": [
                   "obs:*:*:object:examplebucket/dir_1/",
               ]
           }
       ]
   }

Example 2: Grant a user the permissions required to download **dir_1** and its subdirectories.

In the following configuration, the resource path uses prefix-based matching and ends with a wildcard (``*``). In such case, a success response can be returned when a head request is sent to **dir_1/file1**.

.. code-block::

   {
       "Version": "1.1",
       "Statement": [
           {
               "Effect": "Allow",
               "Action": [
                   "obs:object:GetObject",
               ],
               "Resource": [
                   "obs:*:*:object:examplebucket/dir_1/*",
               ]
           }
       ]
   }

Bucket Policy Configuration Examples
------------------------------------

Example: Grant a user the permissions required to download **dir_1**, excluding its subdirectories.

In the following configuration, the resource path ends with a slash (/). In such case, a success response can be returned when **dir_1** or **dir_1/** is contained in the URL of a head request.

.. code-block::

   {
       "Statement":[
       {
         "Sid":"test",
         "Effect":"Allow",
         "Principal": {"ID": ["domain/b4bf1b36d9ca43d984fbcb9491b6fce9:user/71f3901173514e6988115ea2c26d1999"]},
         "Action":["*"],
         "Resource":[
           "examplebucket/dir_1/",
         ]
       }
     ]
   }
