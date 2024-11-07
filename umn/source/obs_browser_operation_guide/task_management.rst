:original_name: obs_03_0435.html

.. _obs_03_0435:

Task Management
===============

OBS Browser supports the management of upload, download, deletion, and restoration tasks. You can suspend, cancel, or delete tasks using the task management function.

.. note::

   If the number of displayed items exceeds 200,000, the system will save the first 100,000 items of tasks that are created earlier to the **history** directory in the decompression path of OBS Browser. These items are saved in the **historyDBData**\ [*time stamp*]\ **.csv** files, for example, **historyDBData20170426T063744.csv**.

Procedure
---------

#. Log in to OBS Browser.
#. In the upper right corner on the page, click |image1|.
#. You can select a task type from the drop-down list box in the upper right corner to query the running tasks.
#. **Optional**: Select a running task and click |image2| to suspend the task. For a paused task, you can click |image3| to continue the task.
#. **Optional**: Select a running task and click |image4| to delete the task.
#. **Optional**: If the task fails, select the failed task, move the cursor over |image5| to view the failure cause, or click |image6| to run the task again.
#. **Optional**: You can select multiple tasks and click **Run All**, **Suspend All**, or **Cancel All** above the list.

   .. note::

      -  For tasks in the **Restoring** status, the **Run All** and **Suspend All** buttons do not take effect.
      -  The **Cancel All** button does not take effect on tasks that are in the **Restoring** status, but will delete tasks that fail to be restored.

#. **Optional**: Click the **Completed** button on the top of the page to view completed tasks. Click |image7| next to a finished task to delete the task record.

.. |image1| image:: /_static/images/en-us_image_0237531615.png
.. |image2| image:: /_static/images/en-us_image_0237531617.png
.. |image3| image:: /_static/images/en-us_image_0237531618.png
.. |image4| image:: /_static/images/en-us_image_0237534487.png
.. |image5| image:: /_static/images/en-us_image_0237531619.png
.. |image6| image:: /_static/images/en-us_image_0237531618.png
.. |image7| image:: /_static/images/en-us_image_0237534487.png
