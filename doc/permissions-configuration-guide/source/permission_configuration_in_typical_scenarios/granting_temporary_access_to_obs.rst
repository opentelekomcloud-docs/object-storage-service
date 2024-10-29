:original_name: obs_40_0037.html

.. _obs_40_0037:

Granting Temporary Access to OBS
================================

Scenario
--------

This case describes how to use temporary access keys (temporary AK/SK and security token) to access OBS.

Assume that you want to enable an IAM user (user name: APPServer) to access the APPClient folder in bucket **hi-company** and apply for two different temporary access keys to distribute to APP-1 and APP-2. APP-1 can only access files in APPClient/APP-1. APP-2 can access only the files in APPClient/APP-2.

Procedure
---------

#. Log in to the management console using a cloud service account.

#. On the top menu bar, choose **Service List** > **Management & Deployment** > **Identity and Access Management**.

#. Create an IAM user **APPServer**. For details, see `Creating an IAM User <https://docs.otc.t-systems.com/en-us/usermanual/iam/en-us_topic_0046611303.html>`__.

#. Create a user-defined policy that allows access to the AppClient folder in bucket hi-company.

   a. In the navigation pane, choose **Permissions**.

   b. Configure parameters for a custom policy.

      .. note::

         Before configuring an IAM policy, you need to understand what permissions are required. An IAM user only has the permissions defined by the policy. In this example, user **APPServer** only has full permissions on objects in the **APPClient** folder.


      .. figure:: /_static/images/en-us_image_0000001435988521.png
         :alt: **Figure 1** Configuring a custom policy

         **Figure 1** Configuring a custom policy

      .. table:: **Table 1** Parameters for configuring a custom policy

         +-----------------------------------+-------------------------------------------------------------+
         | Parameter                         | Description                                                 |
         +===================================+=============================================================+
         | Policy Name                       | Enter a policy name.                                        |
         +-----------------------------------+-------------------------------------------------------------+
         | Policy View                       | Select one based on your own habits. **JSON** is used here. |
         +-----------------------------------+-------------------------------------------------------------+
         | Policy Content                    | .. code-block::                                             |
         |                                   |                                                             |
         |                                   |    {                                                        |
         |                                   |        "Version": "1.1",                                    |
         |                                   |        "Statement": [                                       |
         |                                   |            {                                                |
         |                                   |                "Action": [                                  |
         |                                   |                    "obs:object:*"                           |
         |                                   |                ],                                           |
         |                                   |                "Resource": [                                |
         |                                   |                    "obs:*:*:object:hi-company/APPClient/*"  |
         |                                   |                ],                                           |
         |                                   |                "Effect": "Allow"                            |
         |                                   |            }                                                |
         |                                   |        ]                                                    |
         |                                   |    }                                                        |
         +-----------------------------------+-------------------------------------------------------------+
         | Scope                             | The default value is **Global services**.                   |
         +-----------------------------------+-------------------------------------------------------------+

   c. Click **OK**.

#. `Create a user group and assign permissions <https://docs.otc.t-systems.com/en-us/usermanual/iam/iam_01_0030.html>`__.

   Apply the created custom policy to the user group by following the instructions in the IAM document.

#. `Add the IAM user (APPServer) to the created user group <https://docs.otc.t-systems.com/en-us/usermanual/iam/iam_01_0031.html>`__.

   .. note::

      Due to data caching, it takes about 10 to 15 minutes for a custom policy to take effect.

#. The IAM user (APPServer) obtains temporary access keys (temporary access keys and security token) for **APP-1** and **APP-2**.

   To obtain temporary access keys with different permissions, you need to set a temporary policy by adding the policy parameter in the request body. For details, see `Obtaining a Temporary AK/SK <https://docs.otc.t-systems.com/en-us/api/iam/en-us_topic_0097949518.html>`__.

   The following is a sample request for obtaining a pair of temporary access keys. The temporary policy parameters are displayed in bold.

   **A sample request for obtaining a pair of temporary access keys for the device app** **APP-1:**

   .. code-block::

      {
          "auth": {
          "identity": {
              "policy": {
              "Version": "1.1",
              "Statement": [
               {
                 "Action": [
                     "obs:object:*"
                 ],
                  "Resource": [
                     "obs:*:*:object:hi-company/APPClient/APP-1/*"
                 ],
                 "Effect": "Allow"
                  }
              ]
              },
              "token": {
              "duration-seconds": 900

              },
              "methods": [
              "token"
              ]
          }
          }
      }

   **A sample request for obtaining a pair of temporary access keys for the device app** **APP-2:**

   .. code-block::

      {
          "auth": {
          "identity": {
              "policy": {
             "Version": "1.1",
           "Statement": [
                  {
                "Action": [
                     "obs:object:*"
                 ],
                  "Resource": [
                      "obs:*:*:object:hi-company/APPClient/APP-2/*"
                  ],
                 "Effect": "Allow"
                  }
             ]
           },
              "token": {
              "duration-seconds": 900

              },
              "methods": [
              "token"
              ]
          }
          }
      }

Verification
------------

After **APP-1** and **APP-2** have the temporary access keys, they can access OBS through OBS APIs. **APP-1** can access only files in the **APPClient/APP-1** folder, and **APP-2** can access only files in the **APPClient/APP-2** folder.
