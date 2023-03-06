:original_name: obs_03_0331.html

.. _obs_03_0331:

Configuring Tags for a Bucket
=============================

You can add tags to a bucket when creating the bucket. For details, see :ref:`Creating a Bucket <obs_03_0306>`. Also you can add tags to a bucket after it has been created. This topic describes how to add tags to a bucket after it has been created.

Procedure
---------

#. In the bucket list, click the bucket you want to operate. The **Overview** page of the bucket is displayed.

#. In the right **Basic Configurations** area, click **Tags**. The **Tags** page is displayed.

   Alternatively, you can choose **Basic Configurations** > **Tagging** in the navigation pane.

#. Click **Add Tag**. The **Add Tag** dialog box is displayed. See :ref:`Figure 1 <obs_03_0331__fig8687910182820>` for details.

   .. _obs_03_0331__fig8687910182820:

   .. figure:: /_static/images/en-us_image_0129545688.png
      :alt: **Figure 1** Add Tag

      **Figure 1** Add Tag

#. Set the key and value based on :ref:`Table 1 <obs_03_0331__table13674114016216>`.

   .. _obs_03_0331__table13674114016216:

   .. table:: **Table 1** Parameter description

      +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter                         | Description                                                                                                                         |
      +===================================+=====================================================================================================================================+
      | Key                               | Specifies the key of the tag. Each tag of a bucket has a unique key. The value of the key can be self-defined or predefined by TMS. |
      |                                   |                                                                                                                                     |
      |                                   | A tag key must comply with the following naming rules:                                                                              |
      |                                   |                                                                                                                                     |
      |                                   | -  Must contain 1 to 36 characters.                                                                                                 |
      |                                   | -  Only digits, letters, underscores (_), hyphens (-) are allowed.                                                                  |
      +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------+
      | Value                             | Specifies the value of the tag. Tags of a bucket can have repetitive or blank values.                                               |
      |                                   |                                                                                                                                     |
      |                                   | The tag value must comply with the following naming rules:                                                                          |
      |                                   |                                                                                                                                     |
      |                                   | -  Must contain 0 to 43 characters.                                                                                                 |
      |                                   | -  Only digits, letters, underscores (_), hyphens (-) are allowed.                                                                  |
      +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------+

#. Click **OK**.

   It takes approximately 3 minutes for the tag to take effect.

Related Operations
------------------

In the tag list, click **Edit** to change the tag value or click **Delete** to remove the tag.

Searching for buckets by tag is not supported by OBS. However, you can use Tag Management Service (TMS) to search for buckets by tag. For details, see `Searching for Cloud Resources <https://docs.otc.t-systems.com/usermanual/tms/en-us_topic_0056266264.html>`__. **Resource Type** should be set to **OBS-Bucket**.
