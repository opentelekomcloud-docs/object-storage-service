:original_name: obs_03_0421.html

.. _obs_03_0421:

Uploading a File with Server-Side Encryption
============================================

OBS allows users to encrypt objects on the server side so that the objects can be securely stored in OBS.

Prerequisites
-------------

In the region where the OBS is deployed, add the **KMS Administrator** permission to the user group. For details about how to add permissions, see the *IAM User Guide*.

Procedure
---------

#. Log in to OBS Browser.

#. In the upper right corner on the page, click |image1|.

#. Choose **System Configuration** > **General**. For details, see :ref:`Figure 1 <obs_03_0421__fdd58a926a65c4dc39d5a7be42a9bb60c>`.

   .. _obs_03_0421__fdd58a926a65c4dc39d5a7be42a9bb60c:

   .. figure:: /_static/images/en-us_image_0129858302.png
      :alt: **Figure 1** Configuring KMS encryption

      **Figure 1** Configuring KMS encryption

#. Select **Enable HTTPS** and **Enable KMS encryption**.

#. Click **Save**.

#. Verify the encryption status.

   After HTTPS and KMS encryption are enabled, objects uploaded to OBS are encrypted with keys provided by KMS. By default, the key **obs/default** is selected for encryption.

   After objects are uploaded, click |image2| on the right of the object list. In the **Properties** dialog box that is displayed, you can view the object encryption status. **Yes** indicates that server-side encryption has been implemented for the object. **No** indicates that server-side encryption has not been implemented for the object. The object encryption status cannot be changed.

   .. note::

      HTTPS must be enabled when you enable KMS encryption to upload objects. Therefore, if you deselect **Enable HTTPS**, **Enable KMS encryption** is deselected automatically.


   .. figure:: /_static/images/en-us_image_0129858610.png
      :alt: **Figure 2** Encryption status

      **Figure 2** Encryption status

   .. note::

      -  Server-side encryption does not support HTTP. To use server-side encryption, enable HTTPS.
      -  A key in use cannot be deleted. Otherwise, the object encrypted with this key cannot be downloaded.

.. |image1| image:: /_static/images/en-us_image_0237530299.png
.. |image2| image:: /_static/images/en-us_image_0237534488.png
