:original_name: en-us_topic_0045853662.html

.. _en-us_topic_0045853662:

Creating a Bucket
=================

This section describes how to create a bucket on OBS Console. A bucket is a container that stores objects in OBS. Before you store data in OBS, you need to create a bucket first.

.. note::

   An account can create a maximum of 100 buckets.

Procedure
---------

#. In the upper right corner of the OBS Console homepage, click **Create Bucket**. The **Create Bucket** page is displayed. For details, see :ref:`Figure 1 <en-us_topic_0045853662__obs_03_0306_fig30207295194414>`.

   .. _en-us_topic_0045853662__obs_03_0306_fig30207295194414:

   .. figure:: /_static/images/en-us_image_0129426050.png
      :alt: **Figure 1** Creating a bucket

      **Figure 1** Creating a bucket

#. Configure bucket parameters.

   .. table:: **Table 1** Bucket parameters

      +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter                         | Description                                                                                                                                                                                                                                                                                                 |
      +===================================+=============================================================================================================================================================================================================================================================================================================+
      | Region                            | Geographic area where a bucket resides. For low network latency and quick resource access, select the nearest region. Once a bucket is created, the region cannot be changed.                                                                                                                               |
      +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Bucket Name                       | Name of the bucket. A bucket name must be unique across all accounts and regions. Once a bucket is created, you cannot change its name.                                                                                                                                                                     |
      |                                   |                                                                                                                                                                                                                                                                                                             |
      |                                   | An OBS bucket must be named according to the globally applied DNS naming rules as follows:                                                                                                                                                                                                                  |
      |                                   |                                                                                                                                                                                                                                                                                                             |
      |                                   | -  A bucket name must be unique across all accounts and regions.                                                                                                                                                                                                                                            |
      |                                   | -  A bucket name must contain 3 to 63 characters. Only lowercase letters, digits, hyphens (-), and periods (.) are allowed.                                                                                                                                                                                 |
      |                                   | -  A bucket name cannot start or end with a period (.) or hyphen (-), and cannot contain two consecutive periods (..) or contain a period (.) and a hyphen (-) adjacent to each other.                                                                                                                      |
      |                                   | -  A bucket name cannot be an IP address.                                                                                                                                                                                                                                                                   |
      |                                   |                                                                                                                                                                                                                                                                                                             |
      |                                   |    .. note::                                                                                                                                                                                                                                                                                                |
      |                                   |                                                                                                                                                                                                                                                                                                             |
      |                                   |       When you access OBS through HTTPS using virtual hosted-style URLs, if the bucket name contains a period (.), the certificate verification will fail. To work around this issue, you are advised not to use periods (.) in bucket names.                                                               |
      +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Storage Class                     | Storage classes of a bucket. Different storage classes meet different requirements for storage performance and costs.                                                                                                                                                                                       |
      |                                   |                                                                                                                                                                                                                                                                                                             |
      |                                   | -  The Standard storage class features low access latency and high throughput. It is therefore suitable for storing a massive number of hot files (frequently accessed every month) or small files.                                                                                                         |
      |                                   | -  The Warm storage class is ideal for storing data that is semi-frequently accessed (less than 12 times a year), with requirements for quick response.                                                                                                                                                     |
      |                                   | -  The Archive storage class is suitable for archiving data that is rarely-accessed (averagely once a year), without requirements for quick response.                                                                                                                                                       |
      |                                   |                                                                                                                                                                                                                                                                                                             |
      |                                   | For details, see :ref:`Storage Classes Overview <en-us_topic_0050937852>`.                                                                                                                                                                                                                                  |
      +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Bucket Policy                     | Controls read and write permissions for buckets.                                                                                                                                                                                                                                                            |
      |                                   |                                                                                                                                                                                                                                                                                                             |
      |                                   | -  **Private**: Only users granted permissions by the ACL can access the bucket.                                                                                                                                                                                                                            |
      |                                   | -  **Public Read**: Anyone can read objects in the bucket.                                                                                                                                                                                                                                                  |
      |                                   | -  **Public Read and Write**: Anyone can read, write, or delete objects in the bucket.                                                                                                                                                                                                                      |
      +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Default Encryption                | After the default encryption is enabled for a bucket, all objects uploaded to the bucket are encrypted. The **obs/default** key is used for encryption by default. You can also click **Create KMS Key** to create a key on the KMS console. Then select the created key on OBS Console for KMS encryption. |
      |                                   |                                                                                                                                                                                                                                                                                                             |
      |                                   | If the default encryption is enabled for a bucket, uploaded objects are automatically encrypted.                                                                                                                                                                                                            |
      +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Tags                              | Optional. Tags are used to identify and classify buckets in OBS. Each tag is represented by a key-value pair.                                                                                                                                                                                               |
      |                                   |                                                                                                                                                                                                                                                                                                             |
      |                                   | For more information, see :ref:`Tag Overview <en-us_topic_0059888284>`.                                                                                                                                                                                                                                     |
      +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

#. Click **Create Now**.

Follow-up Procedure
-------------------

You can specify its storage class when creating a bucket or change its storage class after bucket creation.

#. In the bucket list on OBS Console, select the target bucket and click **Change Storage Class** on the right.
#. Select the desired storage class and click **OK**.

   .. note::

      -  Changing the storage class of a bucket does not change the storage class of existing objects in the bucket.
      -  An object inherits the bucket storage class by default, if no other storage class is specified for the object upon its upload. When the bucket storage class is changed, newly uploaded objects inherit the new bucket storage class by default.
