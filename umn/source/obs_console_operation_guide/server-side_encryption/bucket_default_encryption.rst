:original_name: obs_03_0088.html

.. _obs_03_0088:

Bucket Default Encryption
=========================

OBS allows you to configure default encryption for a bucket. After the configuration, objects uploaded to this bucket are automatically encrypted using the specified KMS key, making data storage more secure.

You can enable default encryption when creating a bucket (see :ref:`Creating a Bucket <en-us_topic_0045853662>`), or enable or disable default encryption after a bucket is created.

OBS encrypts only the objects uploaded after the default encryption is enabled, and does not encrypt those uploaded before. After default encryption is disabled, the encryption status of existing objects keeps unchanged, and you can still manually encrypt objects upon upload.

Enabling Default Encryption for a Bucket
----------------------------------------

#. In the bucket list, click the bucket you want to operate. The **Overview** page of the bucket is displayed.

#. In the right **Basic Configurations** area, click **Default Encryption**. The **Default Encryption** dialog box is displayed.

#. Select **Enable**.

   Key **obs/default** is selected by default for KMS encryption. You can also click **Create KMS Key** to switch to the management console of KMS and create customer master keys. Then back to OBS Console and select the key from the drop-down list box for KMS encryption.

#. Click **OK**.

Disabling Default Encryption for a Bucket
-----------------------------------------

#. In the bucket list, click the bucket you want to operate. The **Overview** page of the bucket is displayed.
#. In the right **Basic Configurations** area, click **Default Encryption**. The **Default Encryption** dialog box is displayed.
#. Select **Disable**.
#. Click **OK**.
