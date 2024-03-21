:original_name: obs_03_0088.html

.. _obs_03_0088:

Bucket Default Encryption
=========================

OBS allows you to configure default encryption for a bucket. After the default encryption is enabled for the bucket, objects uploaded to this bucket are automatically encrypted using the specified KMS key, making data storage more secure.

You can enable default encryption when creating a bucket (see :ref:`Creating a Bucket <en-us_topic_0045853662>`), or enable or disable default encryption after the bucket is created.

OBS only encrypts the objects uploaded after the default encryption is enabled for the bucket, and does not encrypt those uploaded before. After you disable a bucket's default encryption, the encryption status of existing objects keeps unchanged, and you can separately encrypt objects when uploading them to the bucket.

Enabling Default Encryption for a Bucket
----------------------------------------

#. In the bucket list, click the bucket you want to operate. The **Overview** page is displayed.

#. In the **Basic Configurations** area, click **Default Encryption**. The **Default Encryption** dialog box is displayed.

#. Select **Enable**.

   Key **obs/default** is selected by default for KMS encryption. You can also click **Create KMS Key** to switch to the KMS management console and create a customer master key. Then go back to OBS Console and select the key from the drop-down list.

#. Click **OK**.

Disabling Default Encryption for a Bucket
-----------------------------------------

#. In the bucket list, click the bucket you want to operate. The **Overview** page is displayed.
#. In the **Basic Configurations** area, click **Default Encryption**. The **Default Encryption** dialog box is displayed.
#. Select **Disable**.
#. Click **OK**.
