:original_name: obs_03_0075.html

.. _obs_03_0075:

Configuring an Object Policy
============================

Object policies apply to objects in a bucket. You can configure a policy for a specific object. The conditions and actions you can use in an object policy are those available for objects in a bucket policy.

Procedure
---------

#. In the bucket list of OBS Console, click the required bucket to go to the **Objects** page.

#. In the row containing the object for which you want to configure a policy, choose **More** > **Configure Object Policy** in the **Operation** column. The **Configure Object Policy** page is displayed.

   You can customize a policy or create a policy by using a preset template.

   -  **Using a preset template**: The system presets object policy templates for multiple typical scenarios. You can use the templates to quickly configure object policies.
   -  **Customizing a policy**: You can also customize an object policy based on your needs. Similar to a bucket policy, a custom object policy consists of five basic elements: effect, principals, resources, actions, and conditions. For details, see :ref:`Bucket Policy Parameters <obs_03_0074>`. The resource is the selected object and is automatically configured by the system. For details about how to customize an object policy, see :ref:`Configuring a Custom Bucket Policy (Common Mode) <obs_03_0123>`. Different from customizing a bucket policy, to customize an object policy, you:

      a. Do not need to specify the resource.
      b. Can configure only object-related actions.
