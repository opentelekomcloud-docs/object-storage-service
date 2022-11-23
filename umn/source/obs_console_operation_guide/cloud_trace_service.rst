:original_name: obs_03_0020.html

.. _obs_03_0020:

Cloud Trace Service
===================

Cloud Trace Service (CTS) records operations on cloud resources in your account. You can use the records to perform security analysis, track resource changes, audit compliance, and locate faults.

After you enable CTS and configure a tracker, CTS can record management and data traces of OBS for auditing.


.. figure:: /_static/images/en-us_image_0136316120.png
   :alt: **Figure 1** CTS

   **Figure 1** CTS

Procedure
---------

#. Log in to the management console.
#. In the upper left corner of the top navigation menu, click |image1| to select a region and project.
#. Then choose **Service List** > **Management & Deployment** > **Cloud Trace Service**. The **Trace List** page is displayed.
#. For details about how to enable CTS, see `Enabling CTS <https://docs.otc.t-systems.com/en-us/usermanual/cts/en-us_topic_0030598498.html>`__ in the *CTS User Guide*.

Follow-up Procedure
-------------------

You can click **Disable** under the **Operation** column on the right of a tracker to disable the tracker. After the tracker is disabled, the system will stop recording operations, but you can still view existing operation records.

You can click **Delete** under the **Operation** column on the right of a tracker to delete the tracker. Deleting a tracker has no impact on existing operation records. When you enable CTS again, you can view operation records that have been generated.

.. |image1| image:: /_static/images/en-us_image_0148639306.png
