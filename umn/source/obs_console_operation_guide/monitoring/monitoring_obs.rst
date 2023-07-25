:original_name: obs_03_0009.html

.. _obs_03_0009:

Monitoring OBS
==============

Scenarios
---------

You may send PUT and GET requests continuously when using OBS, which generates upload and download traffic. You may also receive error responses from the server. Cloud Eye can perform automatic and real-time monitoring over your buckets. It triggers alarms and notifications upon operations to help you understand your bucket access requests, traffic, and error responses in a timely manner.

You do not need to separately subscribe to Cloud Eye. It starts automatically once you create a resource (a bucket, for example) in OBS. For more information about Cloud Eye, see `Cloud Eye User Guide <https://docs.otc.t-systems.com/cloud-eye/umn>`__.


.. figure:: /_static/images/en-us_image_0198863546.png
   :alt: **Figure 1** Cloud Eye monitoring

   **Figure 1** Cloud Eye monitoring

Setting Alarm Rules
-------------------

In addition to the automatic and real-time monitoring, you can configure alarm rules in Cloud Eye to send alarm notifications when specified situation occurs.

For details, see `Creating Alarm Rules <https://docs.otc.t-systems.com/cloud-eye/umn/using_the_alarm_function/creating_alarm_rules/index.html>`__ in *Cloud Eye User Guide*.

Viewing OBS Monitoring Metrics
------------------------------

Cloud Eye monitors :ref:`OBS monitoring metrics <obs_03_0010>` in real time. You can view detailed monitoring statistics of each metric on the console of Cloud Eye.

For details, see `Querying Metrics of a Cloud Service <https://docs.otc.t-systems.com/cloud-eye/umn/getting_started/querying_metrics_of_a_cloud_service.html>`__ in *Cloud Eye User Guide*.
