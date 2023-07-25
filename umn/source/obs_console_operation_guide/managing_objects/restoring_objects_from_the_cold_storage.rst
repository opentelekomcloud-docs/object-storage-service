:original_name: obs_03_0320.html

.. _obs_03_0320:

Restoring Objects from the Cold Storage
=======================================

You must restore a Cold object before you can operate it, including download, access using a URL, as well as ACL and metadata settings.

Limitations and Constraints
---------------------------

-  You cannot suspend or delete the restore task if a Cold object is being restored.
-  You cannot re-restore an object in the **Restoring** state.
-  After an object is restored, an object copy in the Standard storage class will be generated. This way, there is the object in Cold storage class and also its copy in Standard storage class in the bucket. The copy will be automatically deleted once the restore expires.

Procedure
---------

#. In the bucket list, click the bucket you want to operate. The **Overview** page of the bucket is displayed.

#. In the navigation pane, choose **Objects**.

#. Select the file you want to restore, and click **Restore** on the right. The following dialog box shown in :ref:`Figure 1 <obs_03_0320__fig37793164192736>` is displayed.

   You can select multiple files and click **Restore** above the file list to batch restore the files.

   .. note::

      Objects that are being restored cannot be added for batch restore.

   .. _obs_03_0320__fig37793164192736:

   .. figure:: /_static/images/en-us_image_0129533894.png
      :alt: **Figure 1** Restoring an object

      **Figure 1** Restoring an object

#. Configure the validity period and speed of the restore. The following table describes the parameters.

   .. table:: **Table 1** Parameters for restoring objects

      +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter                         | Description                                                                                                                                                                                    |
      +===================================+================================================================================================================================================================================================+
      | Validity Period                   | How long the object will remain in the **Restored** state. It starts once the object is restored. The value is an integer ranging from 1 to 30 (days). The default value is **30**.            |
      |                                   |                                                                                                                                                                                                |
      |                                   | For example, if you set **Validity Period** to **20** when restoring an object, 20 days after the object is successfully restored, its status will change from **Restored** to **Unrestored**. |
      +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Speed                             | How fast an object will be restored.                                                                                                                                                           |
      |                                   |                                                                                                                                                                                                |
      |                                   | -  **Expedited**: Cold objects can be restored within 1 to 5 minutes.                                                                                                                          |
      |                                   | -  **Standard**: Cold objects can be restored within 3 to 5 hours.                                                                                                                             |
      |                                   | -  **Bulk**: Large amounts, even gigabytes, of data can be restored within 5 to 12 hours at a low cost.                                                                                        |
      +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

#. Click **OK**.

   The **Restoration Status** column in the object list displays the restore statuses of objects.

   You can click |image1| to manually refresh the restore status.

   .. note::

      The system checks the file restore status at UTC 00:00 every day. The system starts counting down the expiration time from the time when the latest check is complete.

Related Operations
------------------

Within the validity period of a restored object, you can restore the object again. The validity period is then extended because it will start again when the latest restore is complete.

.. note::

   If a restored object is restored again, its expiration time should be later than the time set for the previous restore. Assume that an object is restored on January 1 and will expire 30 days later (on January 30). If the object is restored again on January 10 and is made to be expired earlier than January 30 (less than 20 days later), this restore action is considered invalid.

.. |image1| image:: /_static/images/en-us_image_0148639825.png
