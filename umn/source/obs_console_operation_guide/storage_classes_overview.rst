:original_name: en-us_topic_0050937852.html

.. _en-us_topic_0050937852:

Storage Classes Overview
========================

OBS supports tiered storage classes at the bucket level and object level.

OBS provides the following storage classes: Standard, Warm, and Cold.

Different storage classes meet different requirements for storage performance and costs.

-  The Standard storage class features low access latency and high throughput. It is therefore suitable for storing a massive number of hot files (frequently accessed every month) or small files (less than 1 MB). The application scenarios include big data analytics, mobile apps, hot videos, and social apps.
-  The Warm storage class is ideal for storing data that is semi-frequently accessed (less than 12 times a year), with requirements for quick response. The application scenarios include file synchronization, file sharing, and enterprise backup.
-  The Cold storage class is suitable for archiving data that is rarely-accessed (averagely once a year). The application scenarios include data archiving and long-term data backups. The Cold storage class is secure, durable, and inexpensive, and can be used to replace tape libraries. However, it may take hours to restore data from the Archive storage class.

Bucket Storage Classes vs. Object Storage Classes
-------------------------------------------------

When an object is uploaded, it inherits the storage class of the bucket by default, but you can change the default storage class when you upload the object.

Changing the storage class of a bucket does not change the storage classes of existing objects in the bucket, but newly uploaded objects will inherit the new storage class.

Comparison of Storage Classes
-----------------------------

+--------------------------+------------------------------------------------------------------------+---------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------+
| Compared Item            | Standard                                                               | Warm                                                                            | Cold                                                                                      |
+==========================+========================================================================+=================================================================================+===========================================================================================+
| Feature                  | Top-notch performance, highly reliable and available                   | Reliable, inexpensive, and real-time storage access                             | Long-term storage for archived data at a very low cost                                    |
+--------------------------+------------------------------------------------------------------------+---------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------+
| Application scenarios    | Cloud application, data sharing, content sharing, and hot data storage | Web disk applications, enterprise backup, active archiving, and data monitoring | Archive, medical image storage, video material storage, and replacement of tape libraries |
+--------------------------+------------------------------------------------------------------------+---------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------+
| Minimum storage duration | Not required                                                           | 30 days                                                                         | 90 days                                                                                   |
+--------------------------+------------------------------------------------------------------------+---------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------+
