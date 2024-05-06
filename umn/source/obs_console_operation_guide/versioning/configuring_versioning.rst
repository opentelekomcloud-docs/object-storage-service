:original_name: obs_03_0327.html

.. _obs_03_0327:

Configuring Versioning
======================

Procedure
---------

#. In the bucket list, click the bucket you want to operate. The **Overview** page is displayed.

#. In the **Basic Information** area, move the cursor over **Disabled**, **Suspended**, or **Enabled** next to **Versioning**. The **Edit** button is displayed next to the versioning status. Click **Edit**. The dialog box for editing the versioning status is displayed.

#. Select **Enable**. For details, see :ref:`Figure 1 <obs_03_0327__fig17030850192918>`.

   .. _obs_03_0327__fig17030850192918:

   .. figure:: /_static/images/en-us_image_0129536902.png
      :alt: **Figure 1** Configuring versioning

      **Figure 1** Configuring versioning

#. Click **OK** to enable versioning for the bucket.

#. Click an object to go to the object details page. On the **Versions** tab, view all versions of the object.

.. _obs_03_0327__section29772226:

Related Operations
------------------

After versioning is configured for a bucket, you can go to the object details page, click the **Versions** tab, and then delete and download object versions.

#. In the bucket list, click the bucket you want to operate. The **Overview** page is displayed.
#. In the navigation pane, choose **Objects**.
#. In the object list, click the object you want to go to the object details page.
#. On the **Versions** tab, view all versions of the object.
#. Perform the following operations on object versions:

   a. Download a desired version of the object by clicking **Download** in the **Operation** column.

      .. note::

         If the version you want to download is in the Cold storage class, restore it first.

   b. Delete a version of the object by clicking **Delete** in the **Operation** column. If you delete the latest version, the most recent version becomes the latest version.
