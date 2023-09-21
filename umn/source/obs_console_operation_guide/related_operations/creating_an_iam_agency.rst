:original_name: obs_03_0037.html

.. _obs_03_0037:

Creating an IAM Agency
======================

To use some OBS features, you need to use IAM agencies to grant required permissions to OBS for processing your data.

Creating an Agency for Cross-Region Replication
-----------------------------------------------

#. In the **Create Cross-Region Replication Rule** dialog box on OBS Console, click **Create IAM agencies** to jump to the **Agencies** page on the IAM console.
#. Click **Create Agency** to create an agency.
#. Enter an agency name.
#. Select **Cloud service** for the **Agency Type**.
#. Select **Object Storage Service (OBS)** for **Cloud Service**.
#. Set a validity period.
#. In the **Permissions** area, select **Project View**, locate **Global service [Global]**, and click **Modify Permissions** in the **Operation** column. The **Modify Permissions** window is displayed.
#. Click **Select Policy/Role** in the **Operation** column of the row where **Global service [Global]** is displayed. Search for **Tenant Administrator** and check the box next to it, and click **OK**.
#. (Optional) If **Replicate KMS encrypted objects** is selected when configuring the cross-region replication rule, the **KMS Administrator** policy set must be configured in the regions where the source bucket and destination bucket are located.

   a. Click **Modify Permissions** in the row of the region where the source/destination bucket resides. The **Modify Permissions** dialog box is displayed.
   b. Click **Select Policy/Role** in the row of the region where the source/destination bucket resides. The **Select Policy/Role** dialog box is displayed.
   c. Search for **KMS** and check the box next to the **KMS Administrator** policy set.
   d. Click **OK**.

#. Click **OK** to complete the agency creation.
