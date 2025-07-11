:original_name: obs_03_0327.html

.. _obs_03_0327:

Configuring Versioning
======================

Procedure
---------

#. In the bucket list, click the bucket you want to operate to go to the **Objects** page.
#. In the navigation pane, choose **Overview**.
#. In the **Basic Configurations** area, click **Versioning**.
#. Select **Enable**.
#. Click **OK** to enable versioning for the bucket.
#. Click an object to go to the object details page. On the **Versions** tab page, view all versions of the object.

.. _obs_03_0327__section29772226:

Related Operations
------------------

After versioning is configured for a bucket, you can go to the object details page, click the **Versions** tab, and then delete, share, and download object versions.

#. In the bucket list, click the bucket you want to operate to go to the **Objects** page.
#. In the object list, click the object you want to go to the object details page.
#. On the **Versions** tab page, view all versions of the object.
#. Perform the following operations on object versions:

   a. Download a desired version of the object by clicking **Download** in the **Operation** column.

      .. note::

         If the version you want to download is in the Cold storage class, restore it first.

   b. Share a version of the object by clicking **Share** in the **Operation** column.
   c. Permanently delete a version of the object by choosing **More** > **Delete** in the **Operation** column. The deleted object version cannot be recovered. If you delete the latest version, the most recent version will become the latest version.
