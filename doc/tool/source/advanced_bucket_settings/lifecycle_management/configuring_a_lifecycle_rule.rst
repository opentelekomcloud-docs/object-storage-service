:original_name: obs_03_1052.html

.. _obs_03_1052:

Configuring a Lifecycle Rule
============================

Configure a lifecycle rule for a bucket to manage objects in the bucket.

Procedure
---------

#. Log in to OBS Browser+.

#. Select the bucket you want and choose **More** > **Lifecycle Rules**.

#. Click **Create**.

#. Configure related parameters.

   -  **Status**: Select **Enable** to enable this lifecycle rule after the configuration.
   -  **Rule Name**: Enter a rule name that is no longer than 255 characters.
   -  **Applies To**: By selecting **Object name prefix**, the lifecycle rule will apply to objects with the specified prefix contained in their name. You can also select **Bucket** for the lifecycle rule to apply to all objects in the bucket.

   .. note::

      -  If **Object name prefix** is selected and the specified prefix and the prefix in an existing lifecycle rule overlap, OBS regards the two rules as one and forbids you to configure the current rule. For example, if there is a rule with prefix **abc** in the system, another rule whose prefix contains **abc** cannot be configured.
      -  If there is already a lifecycle rule whose **Applies To** is set to **Object name prefix**, you are not allowed to configure a new rule whose **Applies To** is set to **Bucket**.
      -  If there is already a lifecycle rule whose **Applies To** is set to **Bucket**, you are not allowed to configure a new rule whose **Applies To** is set to **Object name prefix**.

   -  You can use a lifecycle rule to specify the number of days after which objects that have been last updated and meet specified conditions are automatically transitioned to the Warm or Cold storage class, or are automatically deleted upon expiration.

      -  **Transition to** **Warm**: This rule transitions the objects meeting the conditions to the Warm storage class after the specified number of days since the last object update.
      -  **Transition to** **Cold**: This rule transitions the objects meeting the conditions to the Cold storage class after the specified number of days since the last object update.
      -  **Expiration Time**: This determines when an object will expire and then be deleted, or the day after which objects matching the rule will be deleted.

   For example, on January 7, 2022, you saved the following files in OBS:

   -  log/test1.log
   -  log/test2.log
   -  doc/example.doc
   -  doc/good.txt

   On January 10, 2022, you saved the following files in OBS:

   -  log/clientlog.log

   -  log/serverlog.log

   -  doc/work.doc

   -  doc/travel.txt

      If you configure a rule on January 10, 2022 and the rule will make the objects with **log/** as their prefix expired and deleted one day later, objects **log/test1.log**, **log/test2.log**, **log/clientlog.log**, and **log/serverlog.log** will be deleted from the files above on January 12, 2022.

#. Click **OK** to save the lifecycle rule.

Related Operations
------------------

After the configuration is complete, you can edit, delete, enable, or disable the configured rule if necessary.
