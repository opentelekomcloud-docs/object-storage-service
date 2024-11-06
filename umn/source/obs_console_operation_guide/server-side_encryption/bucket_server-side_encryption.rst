:original_name: obs_03_0088.html

.. _obs_03_0088:

Bucket Server-Side Encryption
=============================

You can configure server-side encryption for an OBS bucket. Once configured, any objects you upload to the bucket will be encrypted with the specified KMS key by default.

You can enable server-side encryption when creating a bucket (see :ref:`Creating a Bucket <en-us_topic_0045853662>`). You can also enable or disable server-side encryption for an existing bucket.

OBS only encrypts the objects uploaded after server-side encryption is enabled for the bucket, and does not encrypt those uploaded before. After server-side encryption is disabled, encryption status of existing objects in the bucket remains unchanged, and you can still encrypt objects when you upload them.

Enabling Server-Side Encryption for a Bucket
--------------------------------------------

#. In the bucket list, click the bucket you want to operate. The **Overview** page is displayed.

#. In the **Basic Configurations** area, click **Server-Side Encryption**. The **Server-Side Encryption** dialog box is displayed.

#. Select **Enable**.

   Key **obs/default** is selected by default for KMS encryption. You can also click **Create KMS Key** to switch to the KMS management console and create a customer master key. Then go back to OBS Console and select the key from the drop-down list.

#. Click **OK**.

Disabling Server-Side Encryption for a Bucket
---------------------------------------------

#. In the bucket list, click the bucket you want to operate. The **Overview** page is displayed.
#. In the **Basic Configurations** area, click **Server-Side Encryption**. The **Server-Side Encryption** dialog box is displayed.
#. Select **Disable**.
#. Click **OK**.
