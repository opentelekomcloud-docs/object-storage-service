:original_name: obs_03_1044.html

.. _obs_03_1044:

Managing Fragments
==================

Clear fragments that are generated due to data upload failures.

Context
-------

Data is uploaded to OBS using multipart upload. In the event of some situations, data uploads usually fail and generate fragments. You need to clear these fragments to free up storage space. The situations include but are not limited to the following:

-  The network is in poor condition, and connection to the OBS server is frequently interrupted.
-  The upload task is manually suspended.
-  The device is faulty.
-  The device is powered off suddenly.

Procedure
---------

#. Log in to OBS Browser+.

#. Select the bucket you want and click **Fragments**.

#. In the **Fragments** window, select the unwanted fragments and click **Delete** above the list.

   You can also click **Delete All** above the list to delete all fragments. Click |image1| in the upper right corner to refresh the fragment list.

   |image2|

#. In the displayed **Warning** dialog box, confirm the delete information and click **OK**.

#. Click **OK**.

   The **Fragments** window is displayed. You can close this window to go back to the OBS Browser+ homepage.

.. caution::

   Deleted fragments cannot be recovered. Before deleting fragments, ensure that all multipart uploads are complete, or deleting fragments may cause uploads to fail.

.. |image1| image:: /_static/images/en-us_image_0000001240541671.png
.. |image2| image:: /_static/images/en-us_image_0000001223075866.png
