:original_name: obs_03_0075.html

.. _obs_03_0075:

Configuring an Object Policy
============================

Object policies are applied to the objects in a bucket. With an object policy, you can configure conditions and actions for objects in a bucket.

Procedure
---------

#. In the bucket list, click the bucket you want to operate. The **Overview** page of the bucket is displayed.

#. In the navigation pane, choose **Objects**.

#. On the right of the object to be operated, choose **More** > **Configure Object Policy**. The **Configure Object Policy** dialog box is displayed.

#. Select a proper policy mode as required. Valid options are as follows:

   -  Read-only mode: The authorized user has the read permission to the object. For follow-up procedure, see :ref:`5 <obs_03_0075__li3552175452220>`.
   -  Read and write mode: The authorized user has the read and write permissions to the object. For follow-up procedure, see :ref:`5 <obs_03_0075__li3552175452220>`.
   -  Customized: The authorized user will be granted with customized permissions to the object. For detailed configuration, see :ref:`6 <obs_03_0075__li588503161565>`.

   .. note::

      You can configure only one object policy at a time.

#. .. _obs_03_0075__li3552175452220:

   For read-only and read and write modes, enter information about the authorized user in the following format and click **OK**.


   .. figure:: /_static/images/en-us_image_0189257108.png
      :alt: **Figure 1** Parameter settings of an object policy in the read-only or read and write mode

      **Figure 1** Parameter settings of an object policy in the read-only or read and write mode

   .. table:: **Table 1** Object policy parameters in read-only or read and write mode

      +-----------------------+----------------------------------------------------------------------------------------------------------------------+-----------------------------------------------------------------------------------------+
      | Parameter             | Value                                                                                                                | Description                                                                             |
      +=======================+======================================================================================================================+=========================================================================================+
      | Principal             | -  **Include** or **Exclude**                                                                                        | Indicates the user that the object policy applies to.                                   |
      |                       | -  Cloud service user, Federated user                                                                                |                                                                                         |
      |                       |                                                                                                                      | -  **Include**: The policy takes effect on specified users.                             |
      |                       |    -  If you select **Federated user**, you can specify the user to be an **Identity provider** or a **User group**. | -  **Exclude**: The policy takes effect on all users except the specified ones.         |
      +-----------------------+----------------------------------------------------------------------------------------------------------------------+-----------------------------------------------------------------------------------------+
      | Resources             | **Include** or **Exclude**                                                                                           | Resources on which the object policy takes effect.                                      |
      |                       |                                                                                                                      |                                                                                         |
      |                       |                                                                                                                      | -  **Include**: The policy takes effect on specified OBS resources.                     |
      |                       |                                                                                                                      | -  **Exclude**: The policy takes effect on all OBS resources except the specified ones. |
      +-----------------------+----------------------------------------------------------------------------------------------------------------------+-----------------------------------------------------------------------------------------+

#. .. _obs_03_0075__li588503161565:

   For the customized mode, set parameters based on the site requirements and click **OK**.


   .. figure:: /_static/images/en-us_image_0168392585.png
      :alt: **Figure 2** Parameter settings of an object policy in the customized mode

      **Figure 2** Parameter settings of an object policy in the customized mode

   .. table:: **Table 2** Object policy parameters in the custom mode

      +-----------------------+--------------------------------------------------------------------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter             | Value                                                                                                                                | Description                                                                                                                                                                                                                                                                                                                      |
      +=======================+======================================================================================================================================+==================================================================================================================================================================================================================================================================================================================================+
      | Effect                | **Allow** or **Deny**                                                                                                                | Effect of the object policy.                                                                                                                                                                                                                                                                                                     |
      |                       |                                                                                                                                      |                                                                                                                                                                                                                                                                                                                                  |
      |                       |                                                                                                                                      | -  **Allow**: The policy allows the matched requests.                                                                                                                                                                                                                                                                            |
      |                       |                                                                                                                                      | -  **Deny**: The policy denies the matched requests.                                                                                                                                                                                                                                                                             |
      +-----------------------+--------------------------------------------------------------------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Principal             | -  **Include** or **Exclude**                                                                                                        | Specifies users on whom this object policy takes effect, including cloud service users and federated users. A cloud service user is the one who accesses the cloud services through registration with the cloud services. A federated user is the one who accesses the cloud services through federated identity authentication. |
      |                       | -  Cloud service user, Federated user                                                                                                |                                                                                                                                                                                                                                                                                                                                  |
      |                       |                                                                                                                                      | -  **Include**: The policy takes effect on specified users.                                                                                                                                                                                                                                                                      |
      |                       |    -  If you select **Federated user**, you can specify the user to be an **Identity provider** or a **User group**.                 | -  **Exclude**: The policy takes effect on all users except the specified ones.                                                                                                                                                                                                                                                  |
      +-----------------------+--------------------------------------------------------------------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Resources             | -  **Include** or **Exclude**                                                                                                        | Resources on which the object policy takes effect.                                                                                                                                                                                                                                                                               |
      |                       |                                                                                                                                      |                                                                                                                                                                                                                                                                                                                                  |
      |                       |                                                                                                                                      | -  **Include**: The policy takes effect on specified OBS resources.                                                                                                                                                                                                                                                              |
      |                       |                                                                                                                                      | -  **Exclude**: The policy takes effect on all OBS resources except the specified ones.                                                                                                                                                                                                                                          |
      +-----------------------+--------------------------------------------------------------------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Actions               | -  **Include** or **Exclude**                                                                                                        | Operation stated in the object policy.                                                                                                                                                                                                                                                                                           |
      |                       | -  For details about the actions, see :ref:`Actions Related to Objects <obs_03_0051__section387654045518>`.                          |                                                                                                                                                                                                                                                                                                                                  |
      |                       |                                                                                                                                      | -  **Include**: The policy takes effect on specified actions.                                                                                                                                                                                                                                                                    |
      |                       |                                                                                                                                      | -  **Exclude**: The policy takes effect on all actions except the specified ones.                                                                                                                                                                                                                                                |
      +-----------------------+--------------------------------------------------------------------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Conditions            | -  **Condition Operator**: For details, see :ref:`Table 1 <obs_03_0120__table16670126115713>`.                                       | Condition for an object policy to take effect.                                                                                                                                                                                                                                                                                   |
      |                       | -  **Key**: For details, see :ref:`Table 2 <obs_03_0120__table6707152645718>` and :ref:`Table 4 <obs_03_0120__table14742526145718>`. |                                                                                                                                                                                                                                                                                                                                  |
      |                       | -  **Value**: The entered value is associated with the key.                                                                          |                                                                                                                                                                                                                                                                                                                                  |
      +-----------------------+--------------------------------------------------------------------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

#. Click **OK**.

   After the object policy is configured successfully, it is displayed in the list under **Custom Bucket Policies**.
