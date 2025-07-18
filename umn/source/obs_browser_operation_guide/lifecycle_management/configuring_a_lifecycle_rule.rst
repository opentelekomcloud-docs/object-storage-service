:original_name: en-us_topic_0045853854.html

.. _en-us_topic_0045853854:

Configuring a Lifecycle Rule
============================

You can configure a lifecycle management rule for a bucket, and applicable objects in the bucket will be managed by the rule.

Procedure
---------

#. Log in to OBS Browser.

#. Click the blank area in the row of the bucket for which you want to configure a lifecycle rule and choose **More** > **Configure Lifecycle Rule**.

#. In the **Configure Lifecycle Rule** dialog box, click **Create**. The dialog box in :ref:`Figure 1 <en-us_topic_0045853854__fig49848587164214>` is displayed.

   .. _en-us_topic_0045853854__fig49848587164214:

   .. figure:: /_static/images/en-us_image_0129833825.png
      :alt: **Figure 1** Creating a lifecycle rule on OBS Browser

      **Figure 1** Creating a lifecycle rule on OBS Browser

#. Configure a lifecycle rule.

   **Basic Information**:

   -  **Status**:

      Select **Enable** to enable the lifecycle rule.

   -  **Rule Name**:

      It identifies a lifecycle rule. A rule name can contain a maximum of 255 characters.

   -  **Prefix**: It is optional.

      -  If this field is configured, objects with the specified prefix will be managed by the lifecycle rule. The prefix cannot start with a slash (/) or contain two consecutive slashes (//), and cannot contain the following special characters: \\ : \* ? " < > \|
      -  If this field is not configured, all objects in the bucket will be managed by the lifecycle rule.

   -  **Tag** (optional): You can apply a lifecycle rule to the objects with specific tags. A maximum of 10 tags can be added. Once tags are added, the deletion of expired fragments cannot be configured.

   .. note::

      -  If the specified prefix overlaps with the prefix of an existing lifecycle rule, OBS regards these two rules as one and forbids you to configure the one you are configuring. For example, if there is already a rule with prefix **abc** in OBS, you cannot configure another rule whose prefix starts with **abc**.
      -  If there is already a lifecycle rule based on an object prefix, you are not allowed to configure another rule that is applied to the entire bucket.
      -  If a lifecycle rule has been configured for the entire bucket, no more rules that apply to object name prefix can be added.

   **Current Version** or **Historical Version**:

   .. note::

      -  **Current Version** and **Historical Version** are two concepts for versioning. If versioning is enabled for a bucket, uploading objects with the same name to the bucket creates different object versions. The last uploaded object is called the current version, while those previously uploaded are called historical versions.
      -  You can configure either the **Current Version** or **Historical Version**, or both of them.

   -  **Transition to Warm**: After this number of days since the last update, objects meeting specified conditions will be transitioned to Warm.
   -  **Transition to Cold**: After this number of days since the last update, objects meeting specified conditions will be transitioned to Cold.
   -  **Delete Objects After (Days)**: After this number of days since the last update, objects meeting certain conditions will be expired and then deleted. This number must be an integer larger than that specified for any of the transition operations.
   -  **Delete Fragments After (Days)**: After this number of days since the fragment generation, OBS will automatically delete fragments in the bucket.

   For example, on January 7, 2015, you saved the following files in OBS:

   -  log/test1.log
   -  log/test2.log
   -  doc/example.doc
   -  doc/good.txt

   On January 10, 2015, you saved another four files:

   -  log/clientlog.log
   -  log/serverlog.log
   -  doc/work.doc
   -  doc/travel.txt

   On January 10, 2015, you set the objects prefixed with **log** to expire one day later. You might encounter the following situations:

   -  Objects **log/test1.log** and **log/test2.log** uploaded on January 7, 2015 might be deleted after the last system scan. The deletion could happen on January 10, 2015 or January 11, 2015, depending on the time of the last system scan.
   -  Objects **log/clientlog.log** and **log/serverlog.log** uploaded on January 10, 2015 might be deleted on January 11, 2015 or January 12, 2015, depending on whether they have been stored for over one day (since their last update) when the system scan happened.

   On the day of operation, you can set the objects with the name prefix **log** to be transitioned to **Warm** 30 days later, transitioned to **Cold** 60 days later, and deleted 100 days later, then OBS will transition **log/clientlog.log**, **log/serverlog.log**, **log/test1.log**, and **log/test2.log** to **Warm** when their storage duration exceeds 30 days, transition them to **Cold** when their storage duration exceeds 60 days, and delete them when their storage duration exceeds 100 days, respectively.

   .. note::

      In theory, it takes 24 hours at most to execute a lifecycle rule. After an object is updated, OBS calculates its lifecycle from the next 00:00 (UTC time), so there may be a delay of up to 48 hours in transitioning objects between storage classes or deleting expired objects. If you make changes to an existing lifecycle rule, the rule will take effect again.

#. Click **Save**.

#. In the **Create Lifecycle Rule** dialog box, click **Save**.

#. In the displayed dialog box, click **Close** to close the dialog box.
