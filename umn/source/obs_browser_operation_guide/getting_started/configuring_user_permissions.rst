:original_name: obs_03_0035.html

.. _obs_03_0035:

Configuring User Permissions
============================

If your cloud service account does not need individual IAM users, then you may skip this section. Your permissions to use OBS functions are not affected.

If IAM users are required, you need to grant OBS access permissions to the users, because OBS is separately deployed from other cloud resources.

Process
-------


.. figure:: /_static/images/en-us_image_0170301902.png
   :alt: **Figure 1** Process of granting an IAM user the OBS permissions

   **Figure 1** Process of granting an IAM user the OBS permissions

Procedure
---------

#. Log in to the management console using a cloud service account.

#. On the top navigation menu, choose **Service List** > **Management & Deployment** > **Identity and Access Management**. The IAM console page is displayed.

#. Create a user group and grant the OBS permissions to the user group.

   User groups facilitate centralized user management and streamlined permissions management. Users in the same user group have the same permissions. Users created in IAM inherit permissions from the groups to which they belong.

   a. In the navigation pane on the left, click **User Groups**. The **User Groups** page is displayed.

   b. Click **Create User Group**.

   c. On the **Create User Group** page, enter a name for the user group and click **OK**.

      The user group is displayed in the user group list once the creation completes.

   d. Click **Modify** in the **Operation** column of the row where the created user group resides.

   e. In the **Group Permissions** area, locate **OBS (S3)**, click **Attach Policy** in the **Operation** column, select the policy name, and click **OK**.

      .. note::

         In the **Policy Information** area, you can view the details about the policy.

#. Create a user.

   a. In the navigation pane on the left, click **Users**. The **Users** page is displayed.
   b. Click **Create User**.
   c. Set user information and click **Next**.

      .. table:: **Table 1** User parameters

         +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
         | Parameter                         | Description                                                                                                                                                                                                                                                |
         +===================================+============================================================================================================================================================================================================================================================+
         | Username                          | The user name for logging in to the cloud service.                                                                                                                                                                                                         |
         +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
         | Credential Type                   | A credential refers to the identity credential used for user system authentication. In this example, password is selected.                                                                                                                                 |
         |                                   |                                                                                                                                                                                                                                                            |
         |                                   | -  **Password**: Used for accessing cloud services using the console or development tools.                                                                                                                                                                 |
         |                                   | -  **Access key**: Used for logging to the cloud service using development tools. This credential type is more secure, and is recommended if the user does not need to use the console.                                                                    |
         +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
         | User Groups                       | You can add a user to one or more user groups. Then the user will inherit the permissions granted to these user groups. The default user group **admin** has the administrator permissions and all of the permissions required to use all cloud resources. |
         +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
         | Description                       | (Optional) Brief description about the user.                                                                                                                                                                                                               |
         +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

   d. Select a type for password generation, set the email address and mobile number, and click **OK**.

#. Use the created IAM user to log in to OBS Console and verify the user permissions.
