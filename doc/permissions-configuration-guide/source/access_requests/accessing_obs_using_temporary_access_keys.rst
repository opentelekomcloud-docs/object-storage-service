:original_name: obs_40_0008.html

.. _obs_40_0008:

Accessing OBS Using Temporary Access Keys
=========================================

Temporary Access Keys
---------------------

OBS can be accessed through temporary access keys and the security token, which can be obtained on IAM. You can assign the temporary access keys (including the security token) to a third-party application and an IAM user, so they can access OBS within a specified period of time.

You can obtain the temporary access keys and security token by calling the IAM API in `Obtaining a Temporary AK/SK <https://docs.otc.t-systems.com/en-us/api/iam/en-us_topic_0097949518.html>`__.

Temporary AK/SK and security token comply with the least privilege principle and can be used to temporarily access OBS. When you use a temporary AK/SK pair to call an API for authentication, you must use the temporary AK/SK and security token at the same time and add the **x-obs-security-token** field to the request header.

Temporary access keys have the following advantages over permanent access keys of IAM users:

-  Temporary access keys are valid for 15 minutes to 24 hours. You do not need to expose the permanent access keys of IAM users, reducing security risks.
-  When obtaining temporary access keys, you can pass policy parameters to further restrict the temporary permissions granted to users. This ensures that IAM users can effectively control permissions granted to other users.

For details, see `Authenticating a Request <https://docs.otc.t-systems.com/api_obs/obs/en-us_topic_0125560435.html>`__.

Permissions of the Temporary Access Keys
----------------------------------------

When an IAM user calls the IAM API in `Obtaining a Temporary AK/SK <https://docs.otc.t-systems.com/en-us/api/iam/en-us_topic_0097949518.html>`__, the user can specify parameter **policy** to add a temporary policy for the temporary access keys to further restrict the permissions granted to other users. The format and content of a temporary policy are consistent with those specified in :ref:`IAM Permissions <obs_40_0003>`.

-  If policy parameters are not specified, no temporary policies are used. The temporary access keys inherit the IAM user's permissions.
-  If policy parameters are specified, a temporary policy is enabled. Then the temporary access keys confine the granted permissions according to the temporary policy and the IAM user permissions.

As shown in the following figure, circle 1 indicates the original permissions of an IAM user, and circle 2 indicates the temporary permissions specified by a temporary policy. The overlapped part 3 is the scope of permissions enabled by the temporary access keys.


.. figure:: /_static/images/en-us_image_0269157281.png
   :alt: **Figure 1** Intersection of IAM user permissions and temporary policy permissions

   **Figure 1** Intersection of IAM user permissions and temporary policy permissions

Temporary access keys comply with the least privilege principle. Configure a temporary policy within the original permission scope of an IAM user. Otherwise you may be confused about why permissions enabled by a temporary policy are not effective. As illustrated by the following figure, the finally effective permissions are the authorized temporary permissions.


.. figure:: /_static/images/en-us_image_0269160697.png
   :alt: **Figure 2** Restricting temporary permissions within the scope of IAM user permissions

   **Figure 2** Restricting temporary permissions within the scope of IAM user permissions

A temporary policy authentication starts from the Deny statements. Unspecified permissions are denied by default.

.. note::

   Therefore, you are advised to specify only the allowed permission.

Application Scenarios
---------------------

Temporary access keys are used to authorize third parties to temporarily access OBS. For example, some companies have their user management systems, which manage device app users and local enterprise users. These users do not have IAM user permissions, so IAM users can grant temporary access keys to these users when they need to access OBS.

**Typical application scenario:**

A company has a large number of device apps that need to access OBS. Different apps represent different end users who require different access permissions. In this case, temporary access keys can be used to access OBS.


.. figure:: /_static/images/en-us_image_0268971273.jpg
   :alt: **Figure 3** Application scenarios of temporary access keys

   **Figure 3** Application scenarios of temporary access keys

#. If the customer's server can obtain permanent access keys for IAM users, the server can send requests to IAM to generate different temporary access keys for different apps.

   IAM users can obtain the temporary access keys and security token by calling the IAM API in `Obtaining a Temporary AK/SK <https://docs.otc.t-systems.com/en-us/api/iam/en-us_topic_0097949518.html>`__. When calling this API, pass the **policy** parameter to set a temporary policy. An example is provided as follows:

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

#. IAM generates temporary access keys with different permissions and validity periods based on the passed policy parameters and returns the access keys to the customer server.

#. Then the customer server distributes the temporary access keys to device apps that require such permissions.

#. A device app can use the temporary access keys to access OBS through OBS SDKs or APIs. Temporary access keys are valid for a short period of time. If the device app needs to prolong its use of OBS, it should send a request to the customer server for updating temporary access keys before they expire.

Configuration Example
---------------------

For details, see :ref:`Granting Temporary Access to OBS <obs_40_0037>`.
