:original_name: obs_03_0418.html

.. _obs_03_0418:

Restoring a Cold File in OBS
============================

Background Information
----------------------

The Cold storage class is applicable to archiving rarely-accessed (such as once a year) data. The application scenarios include data archiving and long-term data retention for backup, allowing users to safely store data at a low price. However, it can take up to hours to restore data from the Cold storage class.

If a Cold object is being restored, its restore task cannot be suspended or deleted.

You cannot restore an object that is in the **Restoring** state.

Procedure
---------

#. Log in to OBS Browser.

#. Click the bucket in which the file that you want to restore resides. The object list is displayed.

#. Click the restore icon next to the object that you want to restore. Alternatively, you can select an object and click the restore icon on the top of the object list.

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

   Click |image1| and the **Properties** dialog box is displayed. For details, see :ref:`Figure 1 <obs_03_0418__fe014653c9d364bf3999772d96d998638>`. You can view the restoration status.

   .. _obs_03_0418__fe014653c9d364bf3999772d96d998638:

   .. figure:: /_static/images/en-us_image_0129830942.png
      :alt: **Figure 1** Properties of the restored object

      **Figure 1** Properties of the restored object

   You can download the file only after its status changes to **Restored**. You can click the **Refresh** button in the upper right corner to refresh the restoration tasks and to view the restoration progress. The system also automatically refreshes the restoration tasks every 5 minutes.

   .. note::

      The system checks the file restore status at UTC 00:00 every day. The system starts counting down the expiration time from the time when the latest check is complete.

Related Operations
------------------

Within the validity period of a restored object, you can restore the object again. The validity period is then extended because it will start again when the latest restore is complete.

.. note::

   If a restored object is restored again, its expiration time should be later than the time set for the previous restore. Assume that an object is restored on January 1 and will expire 30 days later (on January 30). If the object is restored again on January 10 and is made to be expired earlier than January 30 (less than 20 days later), this restore action is considered invalid.

.. |image1| image:: /_static/images/en-us_image_0237534488.png
