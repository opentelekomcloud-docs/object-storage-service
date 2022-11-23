:original_name: obs_03_0322.html

.. _obs_03_0322:

Uploading a File with Server-Side Encryption
============================================

OBS allows users to encrypt objects using server-side encryption so that the objects can be securely stored in OBS.

Limitations and Constraints
---------------------------

-  The object encryption status cannot be changed.
-  A key in use cannot be deleted. Otherwise, the object encrypted with this key cannot be downloaded.

Prerequisites
-------------

In the region where OBS is deployed, the **KMS Administrator** permission has been added to the user group. For details about how to add permissions, see the *IAM User Guide*.

Procedure
---------

#. In the bucket list, click the bucket to be operated. The **Overview** page of the bucket is displayed.

#. In the navigation pane, click **Objects**.

#. Click **Upload Object**. The **Upload Object** dialog box is displayed.

#. Add the files to be uploaded.

#. Select **KMS encryption** and select a key that you have created on KMS.

   .. note::

      If the default encryption is enabled for a bucket, uploaded objects are automatically encrypted.

   After **KMS encryption** is selected, **obs/default** is selected by default as the key for the encryption. You can also click **Create KMS Key** to switch to the management console of KMS and create customer master keys. Then back to OBS Console and select the key from the drop-down list box for KMS encryption.


   .. figure:: /_static/images/en-us_image_0130187638.png
      :alt: **Figure 1** Encrypting an object to be uploaded

      **Figure 1** Encrypting an object to be uploaded

#. Click **Upload**.

   After the object is uploaded successfully, you can view its encryption status in the object list.
