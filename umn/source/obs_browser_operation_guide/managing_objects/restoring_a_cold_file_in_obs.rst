:original_name: obs_03_0418.html

.. _obs_03_0418:

Restoring a Cold File in OBS
============================

Background Information
----------------------

The Cold storage class is applicable to archiving rarely-accessed (such as once a year) data. The application scenarios include data archiving and long-term data retention for backup, allowing users to safely store data at a low price. However, it can take up to hours to restore data from the Cold storage class.

If an object in the Cold storage class is being restored, you cannot suspend or delete the restoration task.

You cannot restore an object that is in the **Restoring** state.

Procedure
---------

#. Log in to OBS Browser.

#. Click the bucket in which the file that you want to restore resides. The object list is displayed.

#. Click the restore icon next to the object that you want to restore. Alternatively, you can select an object and click the restore icon on the top of the object list.

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

   Click |image1| and the **Properties** dialog box is displayed. For details, see :ref:`Figure 1 <obs_03_0418__fe014653c9d364bf3999772d96d998638>`. You can view the restoration status.

   .. _obs_03_0418__fe014653c9d364bf3999772d96d998638:

   .. figure:: /_static/images/en-us_image_0129830942.png
      :alt: **Figure 1** Properties of the restored object

      **Figure 1** Properties of the restored object

   You can download the file only after its status changes to **Restored**. You can click the **Refresh** button in the upper right corner to refresh the restoration tasks and to view the restoration progress. The system also automatically refreshes the restoration tasks every 5 minutes.

   .. note::

      The system checks the file restoration status at UTC 00:00 everyday. The system starts counting down the expiration time from the time when the latest check is complete.

Follow-up Procedure
-------------------

Within the validity period of a restored object, you can restore the object again. Then the validity period is extended because it will start from the time when the latest restoration is complete.

.. note::

   If a restored object is restored again, its expiration time should be later than the time set for the previous restoration.

.. |image1| image:: /_static/images/en-us_image_0237534488.png
