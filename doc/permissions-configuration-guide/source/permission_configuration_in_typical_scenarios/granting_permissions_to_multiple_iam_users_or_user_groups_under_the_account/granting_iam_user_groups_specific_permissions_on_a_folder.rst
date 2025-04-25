:original_name: obs_40_0044.html

.. _obs_40_0044:

Granting IAM User Groups Specific Permissions on a Folder
=========================================================

Scenario
--------

This topic describes how to grant specified permissions for a folder in an OBS bucket to multiple IAM users or user groups.

Recommended Configuration
-------------------------

Use an IAM custom policy to configure the permissions.

Precautions
-----------

After configuration, IAM users can perform allowed operations using APIs. If they log in to OBS Console or OBS Browser+ to perform those operations, a message will be displayed indicating that they do not have required permissions.

This is because when they log in to OBS Console or OBS Browser+, APIs (such as **ListAllMyBuckets** and **ListBucket**) are called to load the bucket list and object list and some other APIs will also be called on other pages, but their permissions do not cover those APIs. In such case, the message is displayed.

To allow IAM users to operate buckets and objects on OBS Console or OBS Browser+, add at least the **obs:bucket:ListAllMyBuckets** and **obs:bucket:ListBucket** permissions to the custom policy. (In this case, these two permissions are configured in permissions 2 and 3.)

.. note::

   **obs:bucket:ListAllMyBuckets** applies to all resources. You need to select all resources.

   **obs:bucket:ListBucket** applies only to the authorized bucket. You can select all resources or a specified bucket as needed.

Procedure
---------

#. Log in to the management console using a cloud service account.

#. On the top menu bar, choose **Service List** > **Management & Deployment** > **Identity and Access Management**.

#. In the navigation pane, choose **Permissions**.

#. Click **Create Custom Policy** in the upper right corner.

#. Configure a custom policy.


   .. figure:: /_static/images/en-us_image_0000001386340170.png
      :alt: **Figure 1** Configuring a custom policy

      **Figure 1** Configuring a custom policy

   .. table:: **Table 1** Parameters for configuring a custom policy

      +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter                         | Description                                                                                                                                                                                                                                                                                                                                                           |
      +===================================+=======================================================================================================================================================================================================================================================================================================================================================================+
      | Policy Name                       | Enter a policy name.                                                                                                                                                                                                                                                                                                                                                  |
      +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Policy View                       | Select one based on your own habits. **Visual editor** is used here.                                                                                                                                                                                                                                                                                                  |
      +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Policy Content                    | [Permission 1]                                                                                                                                                                                                                                                                                                                                                        |
      |                                   |                                                                                                                                                                                                                                                                                                                                                                       |
      |                                   | -  Select **Allow**.                                                                                                                                                                                                                                                                                                                                                  |
      |                                   |                                                                                                                                                                                                                                                                                                                                                                       |
      |                                   | -  Select **Object Storage Service (OBS)**.                                                                                                                                                                                                                                                                                                                           |
      |                                   |                                                                                                                                                                                                                                                                                                                                                                       |
      |                                   | -  Select all the object-related permissions under **ReadOnly**, **ReadWrite**, and **Permissions**.                                                                                                                                                                                                                                                                  |
      |                                   |                                                                                                                                                                                                                                                                                                                                                                       |
      |                                   | -  On the **All** tab, choose **Specific** > **Specify resource path** to specify a folder.                                                                                                                                                                                                                                                                           |
      |                                   |                                                                                                                                                                                                                                                                                                                                                                       |
      |                                   |    [Path Format]                                                                                                                                                                                                                                                                                                                                                      |
      |                                   |                                                                                                                                                                                                                                                                                                                                                                       |
      |                                   |    **obs:*:*:object:**\ *Bucket name*\ **/**\ *Folder name*\ **/\***                                                                                                                                                                                                                                                                                                  |
      |                                   |                                                                                                                                                                                                                                                                                                                                                                       |
      |                                   |    [Notes]                                                                                                                                                                                                                                                                                                                                                            |
      |                                   |                                                                                                                                                                                                                                                                                                                                                                       |
      |                                   |    For bucket resources, IAM automatically generates the prefix of the resource path **obs:*:*:object:**.                                                                                                                                                                                                                                                             |
      |                                   |                                                                                                                                                                                                                                                                                                                                                                       |
      |                                   |    You can add *Bucket name/Object name* at the end of the generated path prefix to specify a resource path. Wildcards (``*``) are also supported. For example, **OBS:*:*:object:example-002/folder-001/\*** indicates any object in folder **folder-001** of bucket **example-002**.                                                                                 |
      |                                   |                                                                                                                                                                                                                                                                                                                                                                       |
      |                                   | [Permission 2] It is mandatory when an authorized user needs to perform operations on OBS Console or OBS Browser+.                                                                                                                                                                                                                                                    |
      |                                   |                                                                                                                                                                                                                                                                                                                                                                       |
      |                                   | -  Select **Allow**.                                                                                                                                                                                                                                                                                                                                                  |
      |                                   |                                                                                                                                                                                                                                                                                                                                                                       |
      |                                   | -  Select **Object Storage Service (OBS)**.                                                                                                                                                                                                                                                                                                                           |
      |                                   |                                                                                                                                                                                                                                                                                                                                                                       |
      |                                   | -  Select **obs:bucket:ListBucket** from the actions.                                                                                                                                                                                                                                                                                                                 |
      |                                   |                                                                                                                                                                                                                                                                                                                                                                       |
      |                                   | -  On the **All** tab, choose **Specific** > **Specify resource path** to specify a bucket.                                                                                                                                                                                                                                                                           |
      |                                   |                                                                                                                                                                                                                                                                                                                                                                       |
      |                                   |    [Path Format]                                                                                                                                                                                                                                                                                                                                                      |
      |                                   |                                                                                                                                                                                                                                                                                                                                                                       |
      |                                   |    **obs:*:*:bucket:**\ *Bucket name*                                                                                                                                                                                                                                                                                                                                 |
      |                                   |                                                                                                                                                                                                                                                                                                                                                                       |
      |                                   | -  On the **(Optional) Add request condition** tab, click **Add Request Condition**.                                                                                                                                                                                                                                                                                  |
      |                                   |                                                                                                                                                                                                                                                                                                                                                                       |
      |                                   |    -  **Condition key**: Select **obs:prefix** from the drop-down list.                                                                                                                                                                                                                                                                                               |
      |                                   |    -  **Operator**: Select **StringMatch** from the drop-down list.                                                                                                                                                                                                                                                                                                   |
      |                                   |    -  **Value**: *Folder name*\ **/**                                                                                                                                                                                                                                                                                                                                 |
      |                                   |                                                                                                                                                                                                                                                                                                                                                                       |
      |                                   |    [Notes]                                                                                                                                                                                                                                                                                                                                                            |
      |                                   |                                                                                                                                                                                                                                                                                                                                                                       |
      |                                   |    If you want a user to have only the permission to list a folder in the bucket, add a request condition for action **obs:bucket:ListBucket**. **prefix** is included in the request for listing objects in a bucket. In this way, when you specify **prefix** to list objects whose names start with *Folder name*\ **/**, the objects in the bucket can be listed. |
      |                                   |                                                                                                                                                                                                                                                                                                                                                                       |
      |                                   | [Permission 3] It is mandatory when an authorized user needs to perform operations on OBS Console or OBS Browser+.                                                                                                                                                                                                                                                    |
      |                                   |                                                                                                                                                                                                                                                                                                                                                                       |
      |                                   | -  Select **Allow**.                                                                                                                                                                                                                                                                                                                                                  |
      |                                   | -  Select **Object Storage Service (OBS)**.                                                                                                                                                                                                                                                                                                                           |
      |                                   | -  Select **obs:bucket:ListAllMyBuckets** under **ListOnly**.                                                                                                                                                                                                                                                                                                         |
      |                                   | -  Select **All** for **Resources**.                                                                                                                                                                                                                                                                                                                                  |
      +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Scope                             | The default value is **Global services**.                                                                                                                                                                                                                                                                                                                             |
      +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

#. Click **OK**.

#. `Create a user group and assign permissions <https://docs.otc.t-systems.com/en-us/usermanual/iam/iam_01_0030.html>`__.

   Apply the created custom policy to the user group by following the instructions in the IAM document.

#. `Add the IAM user you want to authorize to the created user group <https://docs.otc.t-systems.com/en-us/usermanual/iam/iam_01_0031.html>`__.

   .. note::

      Due to data caching, it takes about 10 to 15 minutes for a custom policy to take effect.

Verification
------------

#. Log in to OBS Console as an IAM user.
#. In the bucket list, click bucket **example-002** to go to the **Overview** page.

   .. note::

      After the configuration is complete, it is normal if the system still displays a message indicating that you do not have required permissions, because OBS Console also calls other APIs for advanced settings, but you can still perform the operations allowed on the folder.

#. In the navigation pane, select **Objects**. If a message indicating no sufficient is available and no object can be viewed, ignore the message and continue with the operations.

   .. note::

      The reason why there is no required permission is that listing objects on OBS Console is to list objects in the root folder. This is different from the configured custom policy (listing objects in folder **folder-001/**).

#. In the search box, enter **folder-001/** to view the list of objects in **folder-001**. Objects **222.txt** and **111.txt** are displayed.
#. Click **Create Folder** to create folder **folder-002**.
#. Click **Upload Object** to upload file **333.txt**.

   .. note::

      If some other permissions are required, hover over the username and choose **Identity and Access Management** > **Permissions**, and then repeat the operations above to configure custom policies as needed.
