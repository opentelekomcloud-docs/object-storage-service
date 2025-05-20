:original_name: obs_03_0141.html

.. _obs_03_0141:

Configuring a Custom Bucket Policy (Coding Mode)
================================================

You can configure a custom bucket policy by coding. The size of a custom bucket policy cannot exceed 20 KB.

Procedure
---------

#. In the bucket list, click the bucket you want to operate to go to the **Objects** page.

#. In the navigation pane, choose **Permissions** > **Bucket Policies**.

#. Click **Create** and click the **JSON** tab.

#. Edit the bucket policy. Below gives a bucket policy example in JSON:

   .. code-block::

      {
         "Statement":[
             {
                 "Action":[
                     "CreateBucket",
                     "DeleteBucket"
                 ],
                 "Effect":"Allow",
                 "Principal":{
                     "ID":[
                         "domain/account ID",
                         "domain/account ID:user/User ID"
                     ]
                 },
                 "Condition":{
                     "NumericNotEquals":{
                         "Referer":"sdf"
                     },
                     "StringNotLike":{
                         "Delimiter":"ouio"
                     }
                 },
                 "Resource":"000-02/key01"
             }
         ]
       }

   .. table:: **Table 1** Parameters for creating a bucket policy in JSON

      +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter                         | Description                                                                                                                                                                                             |
      +===================================+=========================================================================================================================================================================================================+
      | Action                            | Actions the bucket policy applies to. For details, see :ref:`Actions <obs_03_0051>`.                                                                                                                    |
      +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Effect                            | Effect of the bucket policy. For details, see :ref:`Effect <obs_03_0115>`.                                                                                                                              |
      +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Principal                         | Users the bucket policy is applied to. You can obtain the user ID on the **My Credentials** page by logging in to the console as the user to be authorized. Principals should be configured as follows: |
      |                                   |                                                                                                                                                                                                         |
      |                                   | -  **domain/**\ *Domain ID* (indicating that the principal is an account)                                                                                                                               |
      |                                   | -  **domain/**\ *Domain ID*\ **:user/**\ *User ID* (indicating that the principal is a user under an account)                                                                                           |
      |                                   |                                                                                                                                                                                                         |
      |                                   | .. note::                                                                                                                                                                                               |
      |                                   |                                                                                                                                                                                                         |
      |                                   |    *Domain ID* is the **Account ID** that you can find on the **My Credentials** page.                                                                                                                  |
      +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Condition                         | Conditions under which the bucket policy takes effect. For details, see :ref:`Conditions <obs_03_0120>`.                                                                                                |
      +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Resource                          | Resources the bucket policy is applied to. For details, see :ref:`Resources <obs_03_0118>`.                                                                                                             |
      +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

#. Click **Create**.
