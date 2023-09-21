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
#. In the upper left corner of the top navigation menu, click |image1| to select a region and then project.
#. Then choose **Service List** > **Management & Deployment** > **Cloud Trace Service**. The **Trace List** page is displayed.
#. For details about how to enable CTS, see `Enabling CTS <https://docs.otc.t-systems.com/en-us/usermanual/cts/en-us_topic_0030598498.html>`__ in the *CTS User Guide*.

.. table:: **Table 1** OBS management operations logged by CTS

   +--------------+-----------------------------------------------------------------+----------+--------------------------+
   | Tracker Type | Operation                                                       | Resource | Trace Name               |
   +==============+=================================================================+==========+==========================+
   | Management   | Deleting a bucket                                               | bucket   | deleteBucket             |
   +--------------+-----------------------------------------------------------------+----------+--------------------------+
   | Management   | Deleting the CORS configuration a Bucket                        | bucket   | deleteBucketCors         |
   +--------------+-----------------------------------------------------------------+----------+--------------------------+
   | Management   | Deleting the custom domain name configuration                   | bucket   | deleteBucketCustomdomain |
   +--------------+-----------------------------------------------------------------+----------+--------------------------+
   | Management   | Deleting the lifecycle configuration of a bucket                | bucket   | deleteBucketLifecycle    |
   +--------------+-----------------------------------------------------------------+----------+--------------------------+
   | Management   | Deleting a bucket policy                                        | bucket   | deleteBucketPolicy       |
   +--------------+-----------------------------------------------------------------+----------+--------------------------+
   | Management   | Deleting the cross-region replication configuration of a bucket | bucket   | deleteBucketReplication  |
   +--------------+-----------------------------------------------------------------+----------+--------------------------+
   | Management   | Deleting the tag configuration of a bucket                      | bucket   | deleteBucketTagging      |
   +--------------+-----------------------------------------------------------------+----------+--------------------------+
   | Management   | Deleting the static website hosting configuration of a bucket   | bucket   | deleteBucketWebsite      |
   +--------------+-----------------------------------------------------------------+----------+--------------------------+
   | Management   | Deleting bucket data                                            | bucket   | deleteBucketdata         |
   +--------------+-----------------------------------------------------------------+----------+--------------------------+
   | Management   | Creating a bucket                                               | bucket   | createBucket             |
   +--------------+-----------------------------------------------------------------+----------+--------------------------+
   | Management   | Configuring the bucket ACL                                      | bucket   | setBucketAcl             |
   +--------------+-----------------------------------------------------------------+----------+--------------------------+
   | Management   | Configuring the CORS rule for a bucket                          | bucket   | setBucketCors            |
   +--------------+-----------------------------------------------------------------+----------+--------------------------+
   | Management   | Setting the custom domain name for a bucket                     | bucket   | setBucketCustomdomain    |
   +--------------+-----------------------------------------------------------------+----------+--------------------------+
   | Management   | Configuring the bucket lifecycle rules                          | bucket   | setBucketLifecycle       |
   +--------------+-----------------------------------------------------------------+----------+--------------------------+
   | Management   | Configuring the bucket logging function                         | bucket   | setBucketLogging         |
   +--------------+-----------------------------------------------------------------+----------+--------------------------+
   | Management   | Configuring the event notification function for buckets         | bucket   | setBucketNotification    |
   +--------------+-----------------------------------------------------------------+----------+--------------------------+
   | Management   | Configuring the bucket policy                                   | bucket   | setBucketPolicy          |
   +--------------+-----------------------------------------------------------------+----------+--------------------------+
   | Management   | Configuring the bucket quota                                    | bucket   | setBucketQuota           |
   +--------------+-----------------------------------------------------------------+----------+--------------------------+
   | Management   | Configuring the cross-region replication function for buckets   | bucket   | setBucketReplication     |
   +--------------+-----------------------------------------------------------------+----------+--------------------------+
   | Management   | Configuring the bucket storage class                            | bucket   | setBucketStorageclass    |
   +--------------+-----------------------------------------------------------------+----------+--------------------------+
   | Management   | Configuring the bucket tag                                      | bucket   | setBucketTagging         |
   +--------------+-----------------------------------------------------------------+----------+--------------------------+
   | Management   | Configuring the versioning function for buckets                 | bucket   | setBucketVersioning      |
   +--------------+-----------------------------------------------------------------+----------+--------------------------+
   | Management   | Configuring the static domain name for buckets                  | bucket   | setBucketWebsite         |
   +--------------+-----------------------------------------------------------------+----------+--------------------------+

Follow-up Procedure
-------------------

You can click **Disable** under the **Operation** column on the right of a tracker to disable the tracker. After the tracker is disabled, the system will stop recording operations, but you can still view existing operation records.

You can click **Delete** under the **Operation** column on the right of a tracker to delete the tracker. Deleting a tracker has no impact on existing operation records. When you enable CTS again, you can view operation records that have been generated.

.. |image1| image:: /_static/images/en-us_image_0148639306.png
