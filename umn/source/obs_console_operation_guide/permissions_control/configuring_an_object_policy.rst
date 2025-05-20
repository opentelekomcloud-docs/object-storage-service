:original_name: obs_03_0075.html

.. _obs_03_0075:

Configuring an Object Policy
============================

Object policies are applied to the objects in a bucket. With an object policy, you can configure conditions and actions for objects in a bucket.

Procedure
---------

#. In the bucket list, click the bucket you want to operate to go to the **Objects** page.

#. In the row containing the object for which you want to configure a policy, choose **More** > **Configure Object Policy** in the **Operation** column. The **Configure Object Policy** page is displayed.

   You can customize a policy or use a preset template to configure one as needed.

   -  **Using a preset template**: The system presets object policy templates for multiple typical scenarios. You can use the templates to quickly configure object policies.
   -  **Customizing a policy**: You can also customize an object policy based on your needs. A custom object policy consists of five basic elements: effect, principals, resources, actions, and conditions, similar to a bucket policy. For details, see :ref:`Bucket Policy Parameters <obs_03_0074>`. The resource is the selected object and is automatically configured by the system. For details about how to customize an object policy, see :ref:`Configuring a Custom Bucket Policy (Common Mode) <obs_03_0123>`. Different from customizing a bucket policy, to customize an object policy, you:

      a. Do not need to specify the resource.
      b. Can configure only object-related actions.
