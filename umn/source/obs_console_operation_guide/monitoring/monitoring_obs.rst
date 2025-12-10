:original_name: obs_03_0009.html

.. _obs_03_0009:

Monitoring OBS
==============

Scenarios
---------

In the use of OBS, you may send PUT and GET requests that generate upload and download traffic, or receive error responses from the server. To learn the requests, traffic, and error responses in a timely manner, you can use Cloud Eye to perform automatic and real-time monitoring over your buckets.

You do not need to separately subscribe to Cloud Eye. It starts automatically once you create a resource (a bucket, for example) in OBS. For more information about Cloud Eye, see `Cloud Eye User Guide <https://docs.otc.t-systems.com/cloud-eye/umn>`__.


.. figure:: /_static/images/en-us_image_0198863546.png
   :alt: **Figure 1** Cloud Eye monitoring

   **Figure 1** Cloud Eye monitoring

Setting Alarm Rules
-------------------

In addition to automatic and real-time monitoring, you can configure alarm rules in Cloud Eye to receive alarm notifications when there are exceptions.

For details about how to configure alarm rules for monitoring over OBS, see `Creating Alarm Rules <https://docs.otc.t-systems.com/cloud-eye/umn/using_the_alarm_function/creating_alarm_rules/index.html>`__ in *Cloud Eye User Guide*.

On Cloud Eye, you can configure alarm rules for events. When specified events happen, you will receive alarm notifications. For details, see section "Creating an Alarm Rule to Monitor an Event" in *Cloud Eye User Guide*.

Viewing OBS Monitoring Metrics
------------------------------

Cloud Eye monitors :ref:`OBS monitoring metrics <obs_03_0010>` in real time. You can view detailed monitoring statistics of each metric on the console of Cloud Eye.

For details about how to view OBS monitoring metrics, see `Querying Metrics of a Cloud Service <https://docs.otc.t-systems.com/cloud-eye/umn/getting_started/querying_metrics_of_a_cloud_service.html>`__ in *Cloud Eye User Guide*.

Cloud Eye monitors :ref:`OBS events <obs_03_063603__table13653193214714>` in real time. You can view the monitoring data on the Cloud Eye console. For details, see section "Viewing Event Monitoring Data" in *Cloud Eye User Guide*.
