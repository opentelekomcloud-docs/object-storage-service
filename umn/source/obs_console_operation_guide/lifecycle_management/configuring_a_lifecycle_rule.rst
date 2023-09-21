:original_name: obs_03_0335.html

.. _obs_03_0335:

Configuring a Lifecycle Rule
============================

You can configure a lifecycle rule for a bucket or for certain objects. With a lifecycle rule, you can transition objects from Standard to Warm or Cold, or from Warm to Cold. However, Cold objects cannot be transitioned to other storage classes using a lifecycle rule. You can also make the objects to be automatically deleted once they expire.

Procedure
---------

#. In the bucket list, click the bucket you want to operate. The **Overview** page is displayed.

#. In the right **Basic Configurations** area, click **Lifecycle Rules**. The **Lifecycle Rules** page is displayed.

   Alternatively, you can choose **Basic Configurations** > **Lifecycle Rules** in the navigation pane.

#. Click **Create**. A dialog box shown in :ref:`Figure 1 <obs_03_0335__fig1529154319415>` is displayed.

   .. _obs_03_0335__fig1529154319415:

   .. figure:: /_static/images/en-us_image_0000001631360616.png
      :alt: **Figure 1** Creating a lifecycle rule

      **Figure 1** Creating a lifecycle rule

#. Configure a lifecycle rule.

   **Basic Information**:

   -  **Status**:

      Select **Enable** to enable the lifecycle rule.

   -  **Rule Name**:

      Identify lifecycle rules. The **Rule Name** contains a maximum of 255 characters.

   -  **Applies To**: Can be set to **Object name prefix** or **Bucket**.

      -  **Object name prefix**: Objects that have the specified prefix will be managed by the lifecycle rule. The prefix cannot start with a slash (/), cannot have consecutive slashes (/), and cannot contain the following special characters: **\\:*?"<>\|**
      -  **Bucket**: All objects in the bucket will be managed by the lifecycle rule.

   .. note::

      -  When **Object name prefix** is selected and the specified prefix and the prefix of an existing lifecycle rule overlap, OBS regards the two rules as one and disables the one to be configured. For example, if a rule with prefix **abc** exists in the system, another rule whose prefix starts with **abc** cannot be configured.
      -  If a lifecycle rule whose **Applies To** is set to **Object name prefix** has been configured, you cannot configure a lifecycle rule whose **Applies To** is set to **Bucket**.
      -  If a lifecycle rule has been configured for the entire bucket, no more rules that apply to object name prefix can be added.

   **Current Version** or **Historical Version**:

   .. note::

      -  **Current Version** and **Historical Version** are two concepts for **Versioning**. If **Versioning** is enabled, uploading objects with the same name to the same path generates different versions. The object uploaded lastly is called **Current Version**, and the object uploaded previously is called **Historical Version**.
      -  You can configure either the **Current Version** or **Historical Version**, or both of them.

   -  **Transition to Warm**: You can specify the number of days after which objects that have been last updated and meet specified conditions are automatically transitioned to **Warm**. This number must be at least 30.
   -  **Transition to Cold**: You can specify the number of days after which objects that have been last updated and meet specified conditions are automatically transitioned to **Cold**. If you configure to transition objects first to Warm and then Cold, the objects must stay Warm at least 30 days before they can be transitioned to Cold. If only transition to Cold is used, but transition to Warm is not, there is no limit on the number of days for transition.
   -  Object deletion upon expiration: You can specify the number of days after which objects that have been last updated and meet the specified conditions are automatically deleted. The expiration time must be greater than the two transition times.

   For example, on January 7, 2015, you saved the following files in OBS:

   -  log/test1.log
   -  log/test2.log
   -  doc/example.doc
   -  doc/good.txt

   On January 10, 2015, you saved the following files:

   -  log/clientlog.log
   -  log/serverlog.log
   -  doc/work.doc
   -  doc/travel.txt

   On January 10, 2015, you set the expiration time of objects prefixed with **log** to one day later, you may encounter the following situations:

   -  Objects **log/test1.log** and **log/test2.log** uploaded on January 7, 2015 may be deleted after the last system scan. The deletion may happen on January 10, 2015 or January 11, 2015, depending on the time of the last system scan.
   -  Objects **log/clientlog.log** and **log/serverlog.log** uploaded on January 10, 2015 are usually deleted on January 11, 2015 or January 12, 2015, depending on the time of the last system scan. If the objects have been stored for more than one day at the time of the last system scan, the objects are deleted upon the scan. Or, they are deleted at the next system scan or later whenever their storage duration meets the specified expiration time requirement.

   On the day of operation, you can set the objects with the name prefix **log** to be transitioned to **Warm** 30 days later, transitioned to **Cold** 60 days later, and deleted 100 days later, then OBS will transition **log/clientlog.log**, **log/serverlog.log**, **log/test1.log**, and **log/test2.log** to **Warm** when their storage duration exceeds 30 days, transition them to **Cold** when their storage duration exceeds 60 days, and delete them when their storage duration exceeds 100 days, respectively.

   .. note::

      In theory, it takes 24 hours at most to execute a lifecycle rule. Because OBS calculates the lifecycle of an object from the next 00:00 (UTC time) after the object is uploaded, there may be a delay in transitioning objects between storage classes and deleting expired objects. Generally, the delay does not exceed 48 hours. If you make changes to an existing lifecycle rule, the rule will take effect again.

#. Click **OK** to complete the lifecycle rule configuration.

Follow-up Procedure
-------------------

You can click **Edit** under the **Operation** column of a lifecycle rule, to edit the rule. Also you can click **Disable** or **Enable** to disable or enable it.

If you want to delete more than one lifecycle rule at a time, select them and click **Delete** above the list.
