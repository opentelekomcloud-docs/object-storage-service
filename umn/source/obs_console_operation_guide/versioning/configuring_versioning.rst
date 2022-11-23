:original_name: obs_03_0327.html

.. _obs_03_0327:

Configuring Versioning
======================

Procedure
---------

#. In the bucket list, click the bucket to be operated. The **Overview** page of the bucket is displayed.

#. In the **Basic Information** area, move the cursor over **Disabled**, **Suspended**, or **Enabled** next to **Versioning**. The **Edit** button is displayed next to the versioning status. Click **Edit**. The dialog box for editing the versioning status is displayed.

#. Select **Enable**. For details, see :ref:`Figure 1 <obs_03_0327__fig17030850192918>`.

   .. _obs_03_0327__fig17030850192918:

   .. figure:: /_static/images/en-us_image_0129536902.png
      :alt: **Figure 1** Configuring versioning

      **Figure 1** Configuring versioning

#. Click **OK** to enable versioning for objects in the bucket.

#. Click an object to go to the object details page. On the **Versions** tab, view all versions of the object.

.. _obs_03_0327__section29772226:

Follow-up Procedure
-------------------

After versioning is enabled, on the object details page that is displayed, click **Versions**, and then you can delete and download versions of the object.

#. In the bucket list, click the bucket to be operated. The **Overview** page of the bucket is displayed.
#. In the navigation pane, click **Objects**.
#. In the object list, click the target object. The system displays the object information.
#. On the **Versions** tab, view all versions of the object.
#. You can perform the following operations on object versions:

   a. You can download a desired version of the object by clicking **Download** on the right of the version.

      .. note::

         If the desired version is in the Cold storage class, it has to be restored before downloading.

   b. You can delete a version of the object by clicking **Delete** on the right of the version. If you delete the latest version, the most recent version becomes the latest version.
