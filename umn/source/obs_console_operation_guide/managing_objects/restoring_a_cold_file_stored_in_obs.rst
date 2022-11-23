:original_name: obs_03_0320.html

.. _obs_03_0320:

Restoring a Cold File Stored in OBS
===================================

You need to restore a **Cold** object before downloading it, accessing it using its URL, or setting ACL permissions or object metadata for it.

Limitations and Constraints
---------------------------

-  If a **Cold** object is in the **Restoring** state, you cannot suspend or delete the restoration task.
-  You cannot re-restore an object that is in the **Restoring** state.
-  After an object is restored, a copy of the object is generated and saved in the Standard storage class. In this way, the object in the Cold storage class and its copy in the Standard storage class co-exist in the bucket. The copy will be automatically deleted upon expiration of its validity period.

Procedure
---------

#. In the bucket list, click the bucket to be operated. The **Overview** page of the bucket is displayed.

#. In the navigation pane, click **Objects**.

#. Select the file you want to restore, and click **Restore** on the right. The following dialog box shown in :ref:`Figure 1 <obs_03_0320__fig37793164192736>` is displayed.

   You can select multiple files and click **Restore** above the file list to batch restore the files.

   .. note::

      Objects that are being restored cannot be added for batch restoration.

   .. _obs_03_0320__fig37793164192736:

   .. figure:: /_static/images/en-us_image_0129533894.png
      :alt: **Figure 1** Restoring an object

      **Figure 1** Restoring an object

#. Before restoring objects, configure the validity period and restoration speed of the objects. The following table describes the parameters.

   .. table:: **Table 1** Parameters for restoring objects

      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter                         | Description                                                                                                                                                                                                                      |
      +===================================+==================================================================================================================================================================================================================================+
      | Validity Period                   | Time duration when an object remains in the **Restored** state. It starts once the object is restored. The value is an integer ranging from 1 to 30 (days). The default value is **30**.                                         |
      |                                   |                                                                                                                                                                                                                                  |
      |                                   | For example, you set **Validity Period** to **20** when restoring an object. After 20 days starting from the time when the object is successfully restored, the object's status will change from **Restored** to **Unrestored**. |
      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Speed                             | Restoration speed of an object.                                                                                                                                                                                                  |
      |                                   |                                                                                                                                                                                                                                  |
      |                                   | -  **Expedited**: Allows you to restore Cold objects within 1 to 5 minutes.                                                                                                                                                      |
      |                                   | -  **Standard**: Allows you to restore Cold objects within 3 to 5 hours.                                                                                                                                                         |
      |                                   | -  **Bulk**: Bulk retrievals are the lowest-cost retrieval option of OBS, enabling you to retrieve large amounts, even petabytes, of data in a day at a low cost. Bulk retrievals typically complete within 5 to 12 hours.       |
      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

#. Click **OK**.

   The **Restoration Status** column in the objects list displays the restoration statuses of objects.

   You can click |image1| to manually refresh the restoration status.

   .. note::

      The system checks the file restoration status at UTC 00:00 everyday. The system starts counting down the expiration time from the time when the latest check is complete.

Follow-up Procedure
-------------------

Within the validity period of a restored object, you can restore the object again. Then the validity period is extended because it will start from the time when the latest restoration is complete.

.. note::

   If a restored object is restored again, its expiration time should be later than the time set for the previous restoration.

.. |image1| image:: /_static/images/en-us_image_0148639825.png
