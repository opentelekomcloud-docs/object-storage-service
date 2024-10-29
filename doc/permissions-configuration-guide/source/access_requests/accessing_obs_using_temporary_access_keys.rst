:original_name: obs_40_0008.html

.. _obs_40_0008:

Accessing OBS Using Temporary Access Keys
=========================================

Temporary Access Keys
---------------------

You can assign temporary security credentials (including an AK, an SK, and a security token) to a third-party application or an IAM user, so that they can access OBS only for a specified period of time.

You can obtain temporary security credentials by calling an IAM API. For details, see `Obtaining a Temporary AK/SK <https://docs.otc.t-systems.com/en-us/api/iam/en-us_topic_0097949518.html>`__.

The least privilege principle is granted for temporary security credentials to ensure security. Both a temporary AK/SK pair and a security token are required to call an API for authentication, which means that the request header needs to include **x-obs-security-token** field.

Temporary access keys have the following advantages over permanent access keys of IAM users:

-  Temporary access keys are valid for 15 minutes to 24 hours. Permanent access keys of IAM users are not exposed, reducing the risk of identity theft or fraud.
-  When obtaining temporary access keys, you can send the policy parameter to request for the least temporary permissions that can be granted to IAM users.

For details, see `Authenticating a Request <https://docs.otc.t-systems.com/api_obs/obs/en-us_topic_0125560435.html>`__.

Permissions of Temporary Access Keys
------------------------------------

When an IAM user calls the IAM API for `Obtaining a Temporary AK/SK <https://docs.otc.t-systems.com/en-us/api/iam/en-us_topic_0097949518.html>`__, the user can send the **policy** parameter to add a temporary policy to further restrict the permissions that can be granted to other users. The format and content of a temporary policy should be consistent with those specified in :ref:`IAM Permissions <obs_40_0003>`.

-  If the **policy** parameter is not specified, the temporary access keys have the IAM user's permissions.
-  If the **policy** parameter is specified, the temporary access keys' permissions are the overlaps between the temporary policy's permissions and the IAM user's permissions.

As shown in the following figure, circle 1 indicates an IAM user's permissions, and circle 2 indicates the temporary policy's permissions. The overlapping part 3 is the permissions of the temporary access keys.


.. figure:: /_static/images/en-us_image_0269157281.png
   :alt: **Figure 1** Intersection of IAM user permissions and temporary policy permissions

   **Figure 1** Intersection of IAM user permissions and temporary policy permissions

Temporary access keys have the least privilege. You are advised to restrict a temporary policy's permissions within an IAM user's permissions. If a temporary policy's permissions are not all within the IAM user's permissions, the temporary access keys' permissions are definitely not the temporary policy's permissions. As illustrated by the following figure, the finally granted permissions are the temporary policy's permissions.


.. figure:: /_static/images/en-us_image_0269160697.png
   :alt: **Figure 2** Restricting temporary permissions within IAM user permissions

   **Figure 2** Restricting temporary permissions within IAM user permissions

For a temporary policy's permissions, Deny always overrides Allow. Unspecified permissions are all Deny permissions by default.

.. note::

   Therefore, you are advised to specify only Allow permissions.

Application Scenarios
---------------------

Temporary access keys are authorized to third parties to allow them to temporarily access OBS. For example, some companies have user management systems that manage app users and local users. These users do not have IAM user permissions, so IAM can grant temporary access keys to allow these users to temporarily access OBS.

**Typical application scenario:**

A company has a large number of apps that need to access OBS. Different apps require different access permissions. In this case, temporary access keys can be granted to app users to allow them to temporarily access OBS.


.. figure:: /_static/images/en-us_image_0268971273.jpg
   :alt: **Figure 3** Application scenarios of temporary access keys

   **Figure 3** Application scenarios of temporary access keys

#. The customer server has permanent access keys, so it can request IAM to generate different temporary access keys for different apps.

   IAM users can call the IAM API for `Obtaining a Temporary AK/SK <https://docs.otc.t-systems.com/en-us/api/iam/en-us_topic_0097949518.html>`__. IAM users can also send the **policy** parameter to request for temporary policy's permissions. An example is provided as follows:

   .. code-block::

      {
          "auth": {
              "identity": {
                  "methods": [
                      ... ...
                  ],
                  "policy": {
                      ... ...
                  }
              }
          }
      }

   The policy's syntax and format are the same as those specified in :ref:`IAM Permissions <obs_40_0003>`.

#. IAM generates temporary access keys with different permissions and validity periods based on the **policy** parameter and returns the access keys to the customer server.

#. The customer server distributes the temporary access keys to apps.

#. Apps can use the temporary access keys to access OBS through OBS SDKs or APIs. Temporary access keys are valid for the specified period of time. If the apps need to prolong the access to OBS, they should request to the customer server to update temporary access keys before they expire.

Configuration Example
---------------------

For details, see :ref:`Granting Temporary Access to OBS <obs_40_0037>`.
