:original_name: obs_03_0046.html

.. _obs_03_0046:

Sharing a File
==============

Scenarios
---------

You can allow anyone to access your file stored in OBS by sharing the temporary URL of the file.

Background Information
----------------------

File sharing is temporary. All shared URLs are temporary with a validity period.

A temporary URL consists of the access domain name and the temporary authentication information of a file.

The temporary authentication information contains the **AccessKeyId**, **Expires**, **x-obs-security-token**, and **Signature** parameters. **AccessKeyId**, **x-obs-security-token**, and **Signature** are used for authentication. The **Expires** parameter specifies the validity period of the authentication.

After an object is shared on OBS Console, the system will generate a URL that contains the temporary authentication information, valid for five minutes since its generation by default. Each time you change the validity period of a URL, OBS obtains the authentication information again to generate a new URL for sharing, which takes effect since the time when the validity period is changed.

Limitations and Constraints
---------------------------

-  An object shared from OBS Console can be valid for one minute to 18 hours. If you need a longer validity period for a shared object, use the client tool OBS Browser+ that supports a validity period from one minute to 30 days. Or, you can configure a :ref:`bucket policy or object policy <en-us_topic_0045853745>` to grant the access permissions of an object to other users permanently.
-  Only buckets of version 3.0 support file sharing. You can view the bucket version in the **Basic Information** area on the **Overview** page of a bucket.
-  Encrypted objects cannot be shared.
-  To share a cold object, restore it first.

Procedure
---------

#. In the bucket list, click the bucket you want to operate. The **Overview** page of the bucket is displayed.

#. In the navigation pane, click **Objects**.

#. Locate the file to be shared and click **Share** under the **Operation** column. The dialog box as given in :ref:`Figure 1 <obs_03_0046__fig125731684458>` is displayed.

   Once the **Share File** dialog box is opened, the URL is effective and valid for five minutes by default. If you change the validity period, the authentication information in the URL changes accordingly, and the URL's new validity period starts upon the change.

   .. _obs_03_0046__fig125731684458:

   .. figure:: /_static/images/en-us_image_0000001523534634.png
      :alt: **Figure 1** Sharing a file

      **Figure 1** Sharing a file

#. Operate the URL as follows:

   -  Click **Open URL** to preview the file on a new page or directly download it to your default download path.
   -  Click **Copy Link** to share the link to others for them to access this file using a browser.
   -  Click **Copy Path** to share the file path to users who have access permissions to the bucket. The users then can search for the file by pasting the shared path to the search box of the bucket.

   .. note::

      Within the validity period of a URL, any user who has the URL can access the file.
