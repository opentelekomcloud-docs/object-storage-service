:original_name: obs_03_0322.html

.. _obs_03_0322:

Enabling Server-Side Encryption When Uploading an Object
========================================================

OBS allows you to encrypt objects with server-side encryption so that the objects can be securely stored in OBS.

When you upload an object to a bucket with server-side encryption disabled, you can separately configure server-side encryption for the object. If the bucket has server-side encryption enabled, the object you upload inherits encryption from the bucket by default. You can also configure new encryption for the object.

Constraints
-----------

-  The object encryption status cannot be changed.
-  A key in use cannot be deleted. Otherwise, the object encrypted with this key cannot be downloaded.
-  Objects encrypted on the server side cannot be shared.

Prerequisites
-------------

In the region where OBS is deployed, the **KMS Administrator** permission has been added to the user group. For details about how to add permissions, see the *IAM User Guide*.

.. note::

   A custom KMS Policy with a minimum required set of allowed actions for users to be able to upload and download objects with Server-Side Encryption is:

   .. code-block::

      {
          "Version": "1.1",
          "Statement": [
              {
                  "Effect": "Allow",
                  "Action": [
                      "kms:dek:crypto",
                      "kms:dek:create",
                      "kms:cmk:get",
                      "kms:cmk:list",
                      "kms:cmk:generate",
                      "kms:cmk:crypto"
                  ]
              }
          ]
      }

Procedure
---------

#. In the bucket list, click the bucket you want to operate. The **Overview** page is displayed.

#. In the navigation pane, choose **Objects**.

#. Click **Upload Object**. The **Upload Object** dialog box is displayed.

#. Add the files to be uploaded.

#. Enable **KMS encryption** and select a key that you have created on KMS.

   .. note::

      If the bucket has server-side encryption enabled, any object you upload will inherit the KMS encryption from the bucket by default.

   After **KMS encryption** is selected, **obs/default** is selected by default as the key for the encryption. You can also click **Create KMS Key** to switch to the KMS management console and create a customer master key. Then go back to OBS Console and select the key from the drop-down list.


   .. figure:: /_static/images/en-us_image_0130187638.png
      :alt: **Figure 1** Encrypting an object to be uploaded

      **Figure 1** Encrypting an object to be uploaded

#. Click **Upload**.

   After the object is uploaded, you can view its encryption status on its details page.
