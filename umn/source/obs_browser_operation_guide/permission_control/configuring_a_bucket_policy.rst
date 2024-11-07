:original_name: en-us_topic_0045853707.html

.. _en-us_topic_0045853707:

Configuring a Bucket Policy
===========================

A bucket policy defines access control over resources (buckets and objects) in OBS.

Procedure
---------

#. Log in to OBS Browser.

#. Click the blank area in the row of the bucket for which you want to configure a bucket policy and choose **More** > **Configure Bucket Policy**.

#. In the **Configure Bucket Policy** dialog box, input required parameters.

   The size of a bucket policy cannot exceed 20 KB.

   :ref:`Table 1 <en-us_topic_0045853707__t90f413f7432b4558b68c408483fd2be9>` describes the parameters of bucket policies. All fields except the **Effect** field are optional.

   .. _en-us_topic_0045853707__t90f413f7432b4558b68c408483fd2be9:

   .. table:: **Table 1** Parameters in bucket policies

      +------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
      | Parameter              | Description                                                                                                                                                                                     | Mandatory or Not      |
      +========================+=================================================================================================================================================================================================+=======================+
      | Version                | The value can be **2008-10-17**.                                                                                                                                                                | Optional              |
      +------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
      | Id                     | The ID of the bucket policy. The value must be unique.                                                                                                                                          | Optional              |
      +------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
      | Statement              | The description of the bucket policy. The statement defines complete permission control. Each bucket policy can have multiple statements, and each statement contains the following parameters: | Mandatory             |
      |                        |                                                                                                                                                                                                 |                       |
      |                        | -  Sid                                                                                                                                                                                          |                       |
      |                        | -  Effect                                                                                                                                                                                       |                       |
      |                        | -  Principal                                                                                                                                                                                    |                       |
      |                        | -  NotPrincipal                                                                                                                                                                                 |                       |
      |                        | -  Action                                                                                                                                                                                       |                       |
      |                        | -  NotAction                                                                                                                                                                                    |                       |
      |                        | -  Resource                                                                                                                                                                                     |                       |
      |                        | -  NotResource                                                                                                                                                                                  |                       |
      |                        | -  Condition                                                                                                                                                                                    |                       |
      +------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
      | Effect                 | Effect of the bucket policy. The statement can be set to accept or reject requests. Possible values are **Allow** and **Deny**                                                                  | Mandatory             |
      +------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
      | Sid                    | The statement ID.                                                                                                                                                                               | Optional              |
      +------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
      | Principal/NotPrincipal | Users on whom the bucket policy statement takes effect                                                                                                                                          | Mandatory             |
      |                        |                                                                                                                                                                                                 |                       |
      |                        | Either **Principal** or **NotPrincipal** must be selected to specify the user on whom the bucket policy statement takes effect or does not take effect.                                         |                       |
      +------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
      | Action/NotAction       | OBS actions which the bucket policy is applied to.                                                                                                                                              | Mandatory             |
      |                        |                                                                                                                                                                                                 |                       |
      |                        | Either **Action** or **NotAction** must be selected to specify whether the bucket policy applies to the OBS actions.                                                                            |                       |
      +------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
      | Resource/NotResource   | Objects on which the bucket policy statement takes effect                                                                                                                                       | Mandatory             |
      |                        |                                                                                                                                                                                                 |                       |
      |                        | Either **Resource** or **NotResource** must be selected to specify whether the bucket policy applies to the OBS resources.                                                                      |                       |
      +------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
      | Condition              | The conditions under which the bucket policy takes effect                                                                                                                                       | Optional              |
      +------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+

   Example: Uploading objects to bucket **bucket-example** is not allowed.

   .. code-block::

      {
          "Version":"2008-10-17",
          "Id":"Policy1527928945090",
          "Statement":[
              {
                  "Sid":"Stmt1527929149040",
                  "Effect":"Deny",
                  "Principal":
                  {
                      "AWS":[
                          "*"
                      ]
                  },
                  "Action":[
                      "s3:Put*"
                  ],
                  "Resource":[
                      "arn:aws:s3:::bucket-example/*"
                  ]
              }
          ]
      }

#. Click **Save**.

#. In the displayed dialog box, click **Close** to close the dialog box.
