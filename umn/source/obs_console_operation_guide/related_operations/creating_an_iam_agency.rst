:original_name: obs_03_0037.html

.. _obs_03_0037:

Creating an IAM Agency
======================

To use some OBS features, you need to use IAM agencies to grant required permissions to OBS for processing your data.

Creating an Agency for Cross-Region Replication
-----------------------------------------------

#. In the **Create Cross-Region Replication Rule** dialog box on OBS Console, click **View IAM Agencies** to jump to the **Agencies** page on the IAM console.

#. Click **Create Agency**.

#. Enter an agency name.

#. Select **Cloud service** for the **Agency Type**.

#. Select **OBS** for **Cloud Service**.

#. Select a validity period.

#. Click **Next**.

#. On the **Select Policy/Role** page, click **Create Policy** in the upper right corner to create a custom policy.

#. .. _obs_03_0037__li1632423102016:

   Enter a policy name and configure the policy content as follows:

   -  **Select service**: Select **Object Storage Service (OBS)**.
   -  **Actions**: Select the actions listed in the table below.

      +----------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------+
      | Action                                 | Description                                                                                                                                      |
      +========================================+==================================================================================================================================================+
      | obs:object:GetObject                   | Obtains object content and metadata.                                                                                                             |
      +----------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------+
      | obs:object:DeleteObjectVersion         | Deletes one or more object versions.                                                                                                             |
      +----------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------+
      | obs:object:PutObjectVersionAcl         | Configures the object version ACL.                                                                                                               |
      +----------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------+
      | obs:object:AbortMultipartUpload        | Aborts a multipart upload.                                                                                                                       |
      +----------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------+
      | obs:object:PutObjectAcl                | Configures the object ACL.                                                                                                                       |
      +----------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------+
      | obs:object:DeleteObject                | Deletes one or more objects.                                                                                                                     |
      +----------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------+
      | obs:bucket:HeadBucket                  | Obtains bucket metadata.                                                                                                                         |
      +----------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------+
      | obs:object:PutObject                   | Uploads objects with PUT or POST, copies objects, appends data to objects, initiates a multipart upload, as well as uploads and assembles parts. |
      +----------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------+
      | obs:object:GetObjectVersionAcl         | Obtains the object version ACL.                                                                                                                  |
      +----------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------+
      | obs:bucket:GetBucketVersioning         | Obtains the versioning status of a bucket.                                                                                                       |
      +----------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------+
      | obs:bucket:ListBucketMultipartUploads  | Lists multipart uploads.                                                                                                                         |
      +----------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------+
      | obs:object:ListMultipartUploadParts    | Lists uploaded parts.                                                                                                                            |
      +----------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------+
      | obs:object:ModifyObjectMetaData        | Modifies object metadata.                                                                                                                        |
      +----------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------+
      | obs:bucket:ListBucketVersions          | Lists object versions in a bucket.                                                                                                               |
      +----------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------+
      | obs:bucket:ListBucket                  | Lists objects in a bucket.                                                                                                                       |
      +----------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------+
      | obs:object:GetObjectVersion            | Obtains the content and metadata of an object version.                                                                                           |
      +----------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------+
      | obs:object:GetObjectAcl                | Obtains the object ACL.                                                                                                                          |
      +----------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------+
      | obs:bucket:GetReplicationConfiguration | Obtains the cross-region replication configuration of a bucket.                                                                                  |
      +----------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------+

   -  **Resources**: Select **Specific**.

      -  **object**: Select **Specify resource path**. The resource path format is **OBS:*:*:object:**\ *Bucket name*\ **/**\ *Object name*.

         Add all objects in the source and destination buckets. For example, set the resource path to **OBS:*:*:object:piccomp/\*** and **OBS:*:*:object:piccomp-output/\***, indicating all objects in source bucket **piccomp** and destination bucket **piccomp-output**, respectively.

      -  **bucket**: Select **Specify resource path**. The resource path format is **OBS:*:*:bucket:**\ *Bucket name*.

         Add the source and destination buckets. For example, set the resource path to **OBS:*:*:bucket:piccomp** and **OBS:*:*:bucket:piccomp-output**, indicating the source bucket **piccomp** and destination bucket **piccomp-output**, respectively.


   .. figure:: /_static/images/en-us_image_0000002269635345.png
      :alt: **Figure 1** Configuring a custom policy

      **Figure 1** Configuring a custom policy

#. Click **Next** in the lower right corner of the page.

#. Select the custom policy created in :ref:`9 <obs_03_0037__li1632423102016>` and click **Next** in the lower right corner of the page.

#. On the **Select Scope** page, select **Global services** for **Scope** and click **OK**.

#. (Optional) If **Replicate KMS encrypted objects** is selected, the IAM agency also needs the **KMS CMKFullAccess** permission in the regions where the source and destination buckets are located.

   a. Go to the **Agencies** page of the IAM console and click the name of the agency created in the previous step.
   b. Choose the **Permissions** tab and click **Authorize**.
   c. On the **Select Policy/Role** page, search for and select **KMS CMKFullAccess**. Then, click **Next**.
   d. On the **Select Scope** page, select **Region-specific projects** for **Scope**. Then, select the projects in the regions where the source and destination buckets are located.
