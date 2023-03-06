:original_name: obs_03_0407.html

.. _obs_03_0407:

Adding a Bucket
===============

Buckets are containers that store objects in OBS. Before you store data in OBS, you need to create buckets.

.. note::

   An account can create a maximum of 100 buckets and parallel file systems.

Procedure
---------

#. Log in to OBS Browser.

#. Click **Add Bucket** on the upper left of the page. The **Add Bucket** dialog box is displayed.

#. Set the bucket parameters, as listed in :ref:`Table 1 <obs_03_0407__tcbb89d695149467789cfdd635af1df0c>`.


   .. figure:: /_static/images/en-us_image_0129772318.png
      :alt: **Figure 1** Adding a bucket

      **Figure 1** Adding a bucket

   .. _obs_03_0407__tcbb89d695149467789cfdd635af1df0c:

   .. table:: **Table 1** Creating a Bucket

      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter                         | Description                                                                                                                                                                      |
      +===================================+==================================================================================================================================================================================+
      | Method                            | Select **Create new bucket**.                                                                                                                                                    |
      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Region                            | Region where the bucket to be created is located.                                                                                                                                |
      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Storage Class                     | OBS offers three storage classes: standard, warm, and cold.                                                                                                                      |
      |                                   |                                                                                                                                                                                  |
      |                                   | -  Standard storage class: applies to storing frequently accessed (multiple times per month) hot or small files that require quick response.                                     |
      |                                   |                                                                                                                                                                                  |
      |                                   | -  Warm storage class: applies to storing semi-frequently accessed (less than 12 times a year) data requiring quick response.                                                    |
      |                                   | -  Cold storage class: applies to archiving rarely-accessed (once a year) data without high requirements on response speed.                                                      |
      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Bucket Name                       | Name the bucket according to the globally applied DNS naming regulation as follows:                                                                                              |
      |                                   |                                                                                                                                                                                  |
      |                                   | -  The name must be globally unique in OBS.                                                                                                                                      |
      |                                   | -  The name must contain 3 to 63 characters. Only lowercase letters, digits, hyphens (-), and periods (.) are allowed.                                                           |
      |                                   | -  The name cannot start or end with a period (.) or hyphen (-), and cannot contain two consecutive periods (.) or contain a period (.) and a hyphen (-) adjacent to each other. |
      |                                   | -  The name cannot be an IP address.                                                                                                                                             |
      |                                   | -  If the name contains a period (.), certificate verification will fail when you access OBS through HTTPS using a virtual host.                                                 |
      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

   .. note::

      -  When a URL is used to access a bucket, the bucket name will become a part of the URL. According to the DNS rule, URLs do not support uppercase letters and cannot be used to access a bucket whose name contains uppercase letters. Therefore, a bucket name can contain only lowercase letters, digits, hyphens (-), and periods (.) For example, if you attempt to access bucket **MyBucket** using the URL, bucket **mybucket** will be accessed instead, causing an access error.
      -  DNS naming can standardize the bucket naming globally, facilitating the resolution when accessing a bucket. Users can benefit from new functions and optimized features, and static website hosting is then applicable to buckets.
      -  Once you create a bucket, you cannot change the name of it. Make sure that the bucket name you set is appropriate.

#. Click **OK**.

#. In the displayed dialog box, click **Close** to close the dialog box.

Region Information Configuration
--------------------------------

The **Region** information can be configured on OBS Browser. The following details the configuration procedure:

#. Open file **region** in folder **OBS Browser** in the decompression path of OBS Browser.

#. Change the value of parameter **options** in file **region**.

   Enter the region information to be added to the end of parameter **options** in the following format:

   *{"key":"Region alias","value":"Region"}*

   The newly added information must be in the JSON format. The following describes the parameters.

   -  **key**: indicates a user-defined region alias. Its value is in the **Region** drop-down list in the **Add Bucket** dialog box. For a convenient view, you are advised to enter not more than 25 characters.

   -  **value** indicates region. Enter the value based on regions supported by OBS.

      Each time when a **Region** is added, a group of values will be added to **options**, that is, **{"key":"Region alias","value":"Region"}**. Groups of values are separated by commas (,). The following provides two configuration examples of newly added **region01** and **region02**. Keep the values of other parameters in file **region** unchanged.

      *"options":[{"key":"test_region01","value":"region01"},{"key":"test_region02","value":"region02"}]*

#. After file **region** is successfully modified, restart OBS Browser so that the configurations can take effect.

Related Operations
------------------

You can specify its storage class when creating a bucket or change its storage class after bucket creation. The procedure is as follows:

#. Log in to OBS Browser.
#. Select a bucket from the bucket list and click |image1| on the right. The **Change Storage Class** dialog box is displayed.
#. Select the desired storage class and click **OK**.

   .. note::

      -  Changing the storage class of a bucket does not change the storage class of existing objects in the bucket.
      -  An object inherits the bucket storage class by default, if no other storage class is specified for the object upon its upload. When the bucket storage class is changed, newly uploaded objects inherit the new bucket storage class by default.

#. In the displayed dialog box, click **Close** to close the dialog box.

.. |image1| image:: /_static/images/en-us_image_0237534341.png
