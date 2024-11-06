:original_name: obs_03_0049.html

.. _obs_03_0049:

Principals
==========

The principals indicate the users bucket policies apply to. These users can be accounts, federated users or federated user groups, and IAM users. Target users can be specified in either of the following ways:

-  **Include**: The policy applies to specified users.
-  **Exclude**: The policy applies to users except the specified ones.

Cloud Service User
------------------

-  IAM users in the current account

   With **Principal** set to **Current account**, you can select one or more IAM users under this account, so the bucket policy applies to the selected IAM users.

-  Other account

   When the **Principal** is set to **Other account**, you can enter the ID of other accounts. If you want to grant access only to the IAM users under that account, you also need to enter one or more IAM user IDs. Multiple IDs should be separated with commas (,).

   .. note::

      An authorized user can go to the **My Credentials** page to obtain the account ID and user ID after login as an IAM user.

      The account ID is the **Domain ID** that can be found on the **My Credentials** page.

-  Anyone (anonymous users)

   To grant the bucket access permission to anyone, set the **Principal** to **Other account** and enter an asterisk (``*``) as the account ID.

   .. caution::

      Exercise caution when granting the bucket access permissions to anonymous users. If you grant the bucket access permission to anonymous users, anyone can access your bucket, and the traffic and storage fees generated will be borne by the bucket owner (cloud service account). You are advised to set restrictions on access requests. For example, you can allow the access requests from only one IP address.

Federated User
--------------

The **Principal** of a bucket policy can also be a federated user or a federated user group.
