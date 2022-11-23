:original_name: obs_03_0088.html

.. _obs_03_0088:

Bucket Default Encryption
=========================

OBS enables you to configure default encryption for a bucket. After the configuration, objects uploaded to the bucket are automatically encrypted using the specified KMS key, improving data storage security.

You can enable the default encryption when creating a bucket. For details, see :ref:`Creating a Bucket <en-us_topic_0045853662>`. You can also enable or disable the default encryption for an existing bucket.

OBS encrypts only the objects uploaded after the default encryption function is enabled. The encryption status of existing objects in the bucket remains unchanged. Disabling default encryption does not change the encryption status of existing objects in a bucket. After this function is disabled, you can still manually encrypt objects upon upload.

Enabling Default Encryption for a Bucket
----------------------------------------

#. In the bucket list, click the bucket to be operated. The **Overview** page of the bucket is displayed.

#. In the right **Basic Configurations** area, click **Default Encryption**. The **Default Encryption** dialog box is displayed.

#. Select **Enable**.

   Key **obs/default** is selected by default for KMS encryption. You can also click **Create KMS Key** to switch to the management console of KMS and create customer master keys. Then back to OBS Console and select the key from the drop-down list box for KMS encryption.

#. Click **OK**.

Disabling Default Encryption for a Bucket
-----------------------------------------

#. In the bucket list, click the bucket to be operated. The **Overview** page of the bucket is displayed.
#. In the right **Basic Configurations** area, click **Default Encryption**. The **Default Encryption** dialog box is displayed.
#. Select **Disable**.
#. Click **OK**.
