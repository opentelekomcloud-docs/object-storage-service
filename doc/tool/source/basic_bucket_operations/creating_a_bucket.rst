:original_name: obs_03_1041.html

.. _obs_03_1041:

Creating a Bucket
=================

Buckets are containers that store objects in OBS. To store data in OBS, you must first create a bucket.

Procedure
---------

#. Log in to OBS Browser+.

#. In the upper part of the page, click **Create Bucket**.

#. In the displayed dialog box, configure bucket parameters, as shown in :ref:`Figure 1 <obs_03_1041__fig3347646295529>`.

   .. _obs_03_1041__fig3347646295529:

   **Figure 1** Creating a bucket

   |image1|

   .. table:: **Table 1** Bucket creation parameters

      +-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter                         | Description                                                                                                                                                                                      |
      +===================================+==================================================================================================================================================================================================+
      | Region                            | Enter the region where you want to create a bucket. Once the bucket is created, its region cannot be changed.                                                                                    |
      +-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Storage Class                     | Storage class of the bucket. Different storage classes meet customers' needs for storage performance and costs.                                                                                  |
      |                                   |                                                                                                                                                                                                  |
      |                                   | -  **Standard**: applicable to scenarios where a large number of hot files or small files need to be accessed frequently (multiple times per month on average) and require fast access response. |
      |                                   | -  **Warm**: ideal for storing data that is not frequently accessed (less than 12 times per year on average) but requires fast access response.                                                  |
      |                                   | -  **Cold**: suitable for archiving data that is rarely accessed (averagely once a year) and has no requirements for quick response.                                                             |
      +-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Bucket ACL                        | Controls read and write permissions on buckets.                                                                                                                                                  |
      |                                   |                                                                                                                                                                                                  |
      |                                   | -  **Private**: Only users granted permissions by the ACL can access the bucket.                                                                                                                 |
      |                                   | -  **Public Read**: Anyone can read objects in the bucket.                                                                                                                                       |
      |                                   | -  **Public Read and Write**: Anyone can read, write, or delete objects in the bucket.                                                                                                           |
      +-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Bucket Name                       | Name of the bucket you want to create, which must be globally unique. A bucket name:                                                                                                             |
      |                                   |                                                                                                                                                                                                  |
      |                                   | -  Must be 3 to 63 characters long and start with a digit or letter. Only lowercase letters, digits, hyphens (-), and periods (.) are allowed.                                                   |
      |                                   | -  Cannot be formatted as an IP address.                                                                                                                                                         |
      |                                   | -  Cannot start or end with a hyphen (-) or period (.).                                                                                                                                          |
      |                                   | -  Cannot contain two consecutive periods (..), for example, **my..bucket**.                                                                                                                     |
      |                                   | -  Cannot contain a period (.) and a hyphen (-) adjacent to each other, for example, **my-.bucket** or **my.-bucket**.                                                                           |
      +-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

   You can click |image2| next to the bucket name to learn about the bucket naming rules. A user can create a maximum of 100 buckets in OBS.

   .. note::

      -  When a URL is used to access a bucket, the bucket name will become part of the URL. According to the DNS rule, URLs do not support uppercase letters and cannot recognize buckets whose name contains uppercase letters. Therefore, a bucket name can contain only lowercase letters, digits, hyphens (-), and periods (.) For example, if you attempt to access bucket **MyBucket** using a URL, the URL will parse **MyBucket** as **mybucket**. This results in an access error.
      -  DNS naming rules can standardize bucket names globally, facilitating the resolution during bucket access. With the DNS naming rules used, you can benefit from new functions and optimized features, and configure static website hosting for buckets.
      -  Once a bucket is created, its name cannot be changed. Make sure that the bucket name you set is appropriate.

#. Click **OK**. If the bucket is successfully created, it is displayed in the bucket list. If the creation fails, an error message will be displayed.

.. |image1| image:: /_static/images/en-us_image_0000001267755821.png
.. |image2| image:: /_static/images/en-us_image_0000001195698772.png
