:original_name: obs_03_0106.html

.. _obs_03_0106:

Sharing a File
==============

Scenarios
---------

You can allow other users to access a file stored in OBS by sharing the temporary URL of the file.

Constraints
-----------

-  An object shared from OBS Browser can be valid for 1 minute to 1 year. If you want a shared object permanently to be valid, you can configure a :ref:`bucket policy or object policy <obs_03_0062>`.
-  Only version 3.0 buckets support file sharing. You can view the bucket version in the **Basic Information** area on the **Overview** page of a bucket.
-  Encrypted objects cannot be shared.

Procedure
---------

#. Log in to OBS Browser.

#. Click the bucket to be operated.

#. Select the file to be shared and click |image1|. The **Share File** dialog box is displayed.


   .. figure:: /_static/images/en-us_image_0000002541123746.png
      :alt: **Figure 1** Sharing File

      **Figure 1** Sharing File

#. URL related operations

   -  Click **Open URL** to preview the file on a new page or directly download it to your default download path.
   -  Click **Copy URL** to share the link to other users, so that they can enter the link to a web browser to access the file.
   -  Click **Copy Path** to share the file path to users who have access to the bucket. The users then can search for the file by pasting the shared path to the search box of the bucket.

   .. note::

      Within the URL validity period, anyone who has the URL can access the file.

#. Click **Close** to close the dialog box.

.. |image1| image:: /_static/images/en-us_image_0000002594230447.png
