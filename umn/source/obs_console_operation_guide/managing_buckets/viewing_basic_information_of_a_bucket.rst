:original_name: obs_03_0312.html

.. _obs_03_0312:

Viewing Basic Information of a Bucket
=====================================

On OBS Console, you can view details about a bucket, including basic bucket information and configurations. You can also export all buckets of the current account and view their basic information in the exported Excel file.

Viewing Bucket Details
----------------------

#. In the bucket list of OBS Console, click the required bucket to go to the **Objects** page.

#. In the navigation pane, choose **Overview**.

#. On the top of the page, view the bucket information, including the bucket name, storage class, region, and creation time.


   .. figure:: /_static/images/en-us_image_0000002540964504.png
      :alt: **Figure 1** Bucket information

      **Figure 1** Bucket information

   .. table:: **Table 1** Bucket information

      +---------------+--------------------------------------------------------------------------------+
      | Item          | Description                                                                    |
      +===============+================================================================================+
      | Bucket name   | Name of the bucket                                                             |
      +---------------+--------------------------------------------------------------------------------+
      | Storage class | Storage class of the bucket, which can be **Standard**, **Warm**, or **Cold**. |
      +---------------+--------------------------------------------------------------------------------+
      | Region        | Region where the bucket is located                                             |
      +---------------+--------------------------------------------------------------------------------+
      | Created       | Creation time of the bucket                                                    |
      +---------------+--------------------------------------------------------------------------------+

#. In the **Basic Information** area, view the number of objects, used capacity, bucket version, and account ID.


   .. figure:: /_static/images/en-us_image_0000002571724439.png
      :alt: **Figure 2** Bucket's basic information

      **Figure 2** Bucket's basic information

   .. table:: **Table 2** Parameters in the Basic Information area

      +----------------+----------------------------------------------------------------------------------------------------------------------------+
      | Parameter      | Description                                                                                                                |
      +================+============================================================================================================================+
      | Objects        | The total number of objects (including folders and all object versions) stored in a bucket                                 |
      +----------------+----------------------------------------------------------------------------------------------------------------------------+
      | Used Capacity  | Total storage space occupied by objects of all versions in the bucket                                                      |
      +----------------+----------------------------------------------------------------------------------------------------------------------------+
      | Bucket Version | Version number of the bucket. **3.0** indicates the latest bucket version, and **--** indicates versions earlier than 3.0. |
      +----------------+----------------------------------------------------------------------------------------------------------------------------+
      | Account ID     | Unique identity of the bucket owner. It is the same as **Domain ID** on the **My Credentials** page.                       |
      +----------------+----------------------------------------------------------------------------------------------------------------------------+

#. In the **Domain Name Details** area, view information about the endpoint, access domain name, and static website hosting domain name. You can also perform related operations by clicking buttons in the **Operation** column.


   .. figure:: /_static/images/en-us_image_0000002571724423.png
      :alt: **Figure 3** Domain name details of the bucket

      **Figure 3** Domain name details of the bucket

#. In the **Basic Configurations** area, view the basic configurations of the bucket, including logging, server-side encryption, requester pays, WORM retention, and versioning. You can click a card to make required configurations.


   .. figure:: /_static/images/en-us_image_0000002540964510.png
      :alt: **Figure 4** Basic configurations of the bucket

      **Figure 4** Basic configurations of the bucket

Exporting a Bucket List
-----------------------

#. Go to the bucket list.

#. To export all buckets, click **Export** in the upper left corner of the bucket list.


   .. figure:: /_static/images/en-us_image_0000002540964522.png
      :alt: **Figure 5** Exporting all buckets

      **Figure 5** Exporting all buckets

#. To export some of the buckets, select the required buckets and click **Export** in the upper left corner of the bucket list.


   .. figure:: /_static/images/en-us_image_0000002541124168.png
      :alt: **Figure 6** Exporting the selected buckets

      **Figure 6** Exporting the selected buckets

#. Obtain the bucket list in Excel, which is automatically downloaded to your local computer.

   The file lists the following bucket information: bucket name, storage class, region, used capacity, object quantity, bucket version, and bucket creation time.
