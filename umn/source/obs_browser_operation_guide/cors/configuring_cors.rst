:original_name: en-us_topic_0045853860.html

.. _en-us_topic_0045853860:

Configuring CORS
================

This section describes how to use CORS in HTML5 to implement cross-origin access.

Procedure
---------

#. Log in to OBS Browser.

#. Select the bucket to be configured and click **More** > **Configure CORS Rule**.

#. Click **Add**.

   .. note::

      You can set a maximum of 100 CORS rules for one bucket.

#. In the **Add CORS Rule** dialog box that is displayed, enter CORS rules.


   .. figure:: /_static/images/en-us_image_0129834236.png
      :alt: **Figure 1** Adding a CORS rule

      **Figure 1** Adding a CORS rule

   :ref:`Table 1 <en-us_topic_0045853860__t810c07199d9d4fb4949e45cc402582a0>` describes parameters in CORS rules.

   .. _en-us_topic_0045853860__t810c07199d9d4fb4949e45cc402582a0:

   .. table:: **Table 1** Parameters in CORS rules

      +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter                         | Description                                                                                                                                                                                           |
      +===================================+=======================================================================================================================================================================================================+
      | Allowed Origin                    | Specifies the origin of cross-origin requests. That is, requests from the origin can access the bucket. This parameter is mandatory.                                                                  |
      |                                   |                                                                                                                                                                                                       |
      |                                   | Multiple matching rules are allowed. One rule occupies one line, and allows one wildcard character (**\***) at most. Example:                                                                         |
      |                                   |                                                                                                                                                                                                       |
      |                                   | .. code-block::                                                                                                                                                                                       |
      |                                   |                                                                                                                                                                                                       |
      |                                   |    http://rds.example.com                                                                                                                                                                             |
      |                                   |    https://*.vbs.example.com                                                                                                                                                                          |
      +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Allowed Method                    | Specifies the method of cross-origin requests, that is, the operation type of buckets and objects. This parameter is mandatory. The following methods are included: Get, Post, Put, Delete, and Head. |
      +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Allowed Header                    | Specifies the allowed header of cross-origin requests. This parameter is optional. Only CORS requests matching the allowed header are valid.                                                          |
      |                                   |                                                                                                                                                                                                       |
      |                                   | You can enter multiple allowed headers (one per line) and each line can contain one wildcard character (``*``) at most. Spaces and special characters including **&:<** are not allowed.              |
      +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Exposed Header                    | Specifies the supplemented header in CORS responses, providing additional information for clients. This parameter is optional.                                                                        |
      |                                   |                                                                                                                                                                                                       |
      |                                   | You can enter multiple exposed headers (one per line). Spaces and special characters including **\*&:<** are not allowed.                                                                             |
      +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Cache Duration (s)                | Mandatory. Specifies the duration that your browser can cache CORS responses, expressed in seconds. The default value is 100.                                                                         |
      +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

#. Click **OK**.

#. Click **OK** to save the rules.

   After CORS is successfully configured, only the addresses specified in **Allowed Origin** can access a bucket in OBS using the method specified in **Allowed Method**. For example, you configure CORS parameters for bucket **testbucket** as follows: **Allowed Origin: www.example.com**; **Allowed Method: GET**; **Allowed Header**: left blank; **Exposed Header**: left blank; **Cache Duration (s): 100**. Then OBS only allows GET requests from **www.example.com** to access bucket **testbucket**, without restrictions on request headers. The client can cache the CORS response for 100 seconds.

#. In the displayed dialog box, click **Close** to close the dialog box.
