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
#. Enable CTS by referring to `Enabling CTS <https://docs.otc.t-systems.com/cloud-trace-service/umn/getting_started/enabling_cts.html>`__ in the *Cloud Trace Service User Guide*.

.. table:: **Table 1** OBS management operations logged by CTS

   +--------------+-----------------------------------------------------------------+----------+--------------------------+
   | Tracker Type | Operation                                                       | Resource | Trace Name               |
   +==============+=================================================================+==========+==========================+
   | Management   | Deleting a bucket                                               | Bucket   | deleteBucket             |
   +--------------+-----------------------------------------------------------------+----------+--------------------------+
   | Management   | Deleting the CORS configuration of a bucket                     | Bucket   | deleteBucketCors         |
   +--------------+-----------------------------------------------------------------+----------+--------------------------+
   | Management   | Deleting the custom domain name configuration                   | Bucket   | deleteBucketCustomdomain |
   +--------------+-----------------------------------------------------------------+----------+--------------------------+
   | Management   | Deleting the lifecycle configuration of a bucket                | Bucket   | deleteBucketLifecycle    |
   +--------------+-----------------------------------------------------------------+----------+--------------------------+
   | Management   | Deleting a bucket policy                                        | Bucket   | deleteBucketPolicy       |
   +--------------+-----------------------------------------------------------------+----------+--------------------------+
   | Management   | Deleting the cross-region replication configuration of a bucket | Bucket   | deleteBucketReplication  |
   +--------------+-----------------------------------------------------------------+----------+--------------------------+
   | Management   | Deleting the tag configuration of a bucket                      | Bucket   | deleteBucketTagging      |
   +--------------+-----------------------------------------------------------------+----------+--------------------------+
   | Management   | Deleting the static website hosting configuration of a bucket   | Bucket   | deleteBucketWebsite      |
   +--------------+-----------------------------------------------------------------+----------+--------------------------+
   | Management   | Creating a bucket                                               | Bucket   | createBucket             |
   +--------------+-----------------------------------------------------------------+----------+--------------------------+
   | Management   | Configuring the bucket ACL                                      | Bucket   | setBucketAcl             |
   +--------------+-----------------------------------------------------------------+----------+--------------------------+
   | Management   | Configuring the CORS rule for a bucket                          | Bucket   | setBucketCors            |
   +--------------+-----------------------------------------------------------------+----------+--------------------------+
   | Management   | Setting the custom domain name for a bucket                     | Bucket   | setBucketCustomdomain    |
   +--------------+-----------------------------------------------------------------+----------+--------------------------+
   | Management   | Configuring the bucket lifecycle rules                          | Bucket   | setBucketLifecycle       |
   +--------------+-----------------------------------------------------------------+----------+--------------------------+
   | Management   | Configuring the bucket logging function                         | Bucket   | setBucketLogging         |
   +--------------+-----------------------------------------------------------------+----------+--------------------------+
   | Management   | Configuring the event notification function for buckets         | Bucket   | setBucketNotification    |
   +--------------+-----------------------------------------------------------------+----------+--------------------------+
   | Management   | Configuring the bucket policy                                   | Bucket   | setBucketPolicy          |
   +--------------+-----------------------------------------------------------------+----------+--------------------------+
   | Management   | Configuring the bucket quota                                    | Bucket   | setBucketQuota           |
   +--------------+-----------------------------------------------------------------+----------+--------------------------+
   | Management   | Configuring the cross-region replication function for buckets   | Bucket   | setBucketReplication     |
   +--------------+-----------------------------------------------------------------+----------+--------------------------+
   | Management   | Configuring the bucket storage class                            | Bucket   | setBucketStorageclass    |
   +--------------+-----------------------------------------------------------------+----------+--------------------------+
   | Management   | Configuring the bucket tag                                      | Bucket   | setBucketTagging         |
   +--------------+-----------------------------------------------------------------+----------+--------------------------+
   | Management   | Configuring the versioning function for buckets                 | Bucket   | setBucketVersioning      |
   +--------------+-----------------------------------------------------------------+----------+--------------------------+
   | Management   | Configuring the static domain name for buckets                  | Bucket   | setBucketWebsite         |
   +--------------+-----------------------------------------------------------------+----------+--------------------------+

Follow-up Procedure
-------------------

You can click **Disable** under the **Operation** column on the right of a tracker to disable the tracker. After the tracker is disabled, the system will stop recording operations, but you can still view existing operation records.

You can click **Delete** under the **Operation** column on the right of a tracker to delete the tracker. Deleting a tracker has no impact on existing operation records. When you enable CTS again, you can view operation records that have been generated.

.. |image1| image:: /_static/images/en-us_image_0148639306.png
