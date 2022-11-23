:original_name: en-us_topic_0066088957.html

.. _en-us_topic_0066088957:

Configuring Redirection
=======================

You can configure static website hosting by redirecting all requests for a bucket to another bucket or URL.

Prerequisites
-------------

Web page files of the static website have been uploaded to a bucket.

The static website files hosted in the bucket are accessible to anonymous users.

If the web page files are in the Cold storage class, restore them first. For more information, see :ref:`Restoring a Cold File Stored in OBS <obs_03_0320>`.

Procedure
---------

#. In the bucket list, click the bucket to be operated. The **Overview** page of the bucket is displayed.

#. In the right **Basic Configurations** area, click **Static Website Hosting**. The **Static Website Hosting** page is displayed.

   Alternatively, you can choose **Basic Configurations** > **Static Website Hosting** from the navigation pane on the left.

#. Click **Configure Static Website Hosting**. The **Configure Static Website Hosting** dialog box is displayed.

#. Enable it by turning on the status switch.

#. Set **Hosting By** to **Redirection**. See :ref:`Figure 1 <en-us_topic_0066088957__fig1131112528711>` for details. Enter a bucket access domain name or URL in the text box of **Redirect To**.

   .. _en-us_topic_0066088957__fig1131112528711:

   .. figure:: /_static/images/en-us_image_0145846362.png
      :alt: **Figure 1** Configuring redirection

      **Figure 1** Configuring redirection

#. Click **OK**.

#. In the bucket list, click the bucket to which requests for the static website are redirected.

#. (**Optional**) If the static website files in the bucket are not accessible to anonymous users, perform this step to configure them to be accessible to anonymous users. If the static website files are already accessible to anonymous users, skip this step.

   Authorize anonymous users the permission to read files on the static website. For details, see :ref:`Authorizing Access Permissions to Anonymous Users <obs_03_0132>`.

   If the bucket contains only static website files, configure the **Public Read** policy for the bucket so that all files in it can be accessed publicly.

   a. Choose **Permissions** > **Bucket Policies**.

   b. In the **Standard Bucket Policies** area, select the **Public Read** policy for the bucket.

   c. Click **Public Read**. For details, see :ref:`Figure 2 <en-us_topic_0066088957__en-us_topic_0045853755_fig15186794193556>`. In the confirmation dialog box that is displayed, click **Yes**.

      .. _en-us_topic_0066088957__en-us_topic_0045853755_fig15186794193556:

      .. figure:: /_static/images/en-us_image_0129612765.png
         :alt: **Figure 2** Configuring the public read permission

         **Figure 2** Configuring the public read permission

#. **Verification**: Input the access domain name of the bucket in the web browser and press **Enter**. The bucket or URL to which requests are redirected will be displayed.

   .. note::

      In some conditions, you may need to clear the browser cache before the expected results are displayed.
