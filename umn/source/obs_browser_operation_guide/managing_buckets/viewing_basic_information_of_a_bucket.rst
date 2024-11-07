:original_name: obs_03_0409.html

.. _obs_03_0409:

Viewing Basic Information of a Bucket
=====================================

This section describes how to view basic information about a bucket, including the owner, capacity, location, and object quantity using OBS Browser.

Procedure
---------

#. Log in to OBS Browser.

#. Click the blank area in the row of the bucket about which you want to query the basic information and click **Basic Information**.

#. The **Basic Information** window is popped up displaying related information. For details, :ref:`Figure 1 <obs_03_0409__fig35840242155659>`.

   .. _obs_03_0409__fig35840242155659:

   .. figure:: /_static/images/en-us_image_0129807617.png
      :alt: **Figure 1** Basic information about the bucket

      **Figure 1** Basic information about the bucket

   .. table:: **Table 1** Parameter description

      +--------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter          | Description                                                                                                                                                        |
      +====================+====================================================================================================================================================================+
      | Bucket Name        | Name of the bucket.                                                                                                                                                |
      +--------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Region             | Region where the bucket is stored.                                                                                                                                 |
      +--------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Storage Class      | Indicates the storage class of the bucket, which can be **Standard**, **Warm**, or **Cold**.                                                                       |
      +--------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Bucket Version     | Version number of the bucket.                                                                                                                                      |
      +--------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Used Capacity      | Total capacity used by objects in the bucket.                                                                                                                      |
      +--------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Objects            | The number of objects is the sum of folders and files (including the latest versions and historical versions).                                                     |
      +--------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Access Domain Name | Indicates the access domain name of the bucket, which is in the format of *Bucket name*.\ *Domain name*.                                                           |
      +--------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Endpoint           | Indicates the domain name of the region where the bucket resides. OBS provides an endpoint for each region, facilitating users to access resources in each region. |
      +--------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Owner              | Bucket owner is the account that creates the bucket                                                                                                                |
      +--------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Account ID         | Unique identity of the bucket owner. It is the same as **Domain ID** on the **My Credentials** page.                                                               |
      +--------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Created            | Time when the creation of a bucket is completed.                                                                                                                   |
      +--------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------+

   .. note::

      The statistics of **Used Capacity** and **Objects** are not real-time data, which are usually updated 15 minutes in delay.
