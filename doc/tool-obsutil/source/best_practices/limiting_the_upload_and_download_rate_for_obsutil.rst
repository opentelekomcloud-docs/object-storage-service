:original_name: obs_11_0073.html

.. _obs_11_0073:

Limiting the Upload and Download Rate for obsutil
=================================================

obsutil allows you to configure the **rateLimitThreshold** parameter in the **.obsutilconfig** file to limit the upload and download rate.

For detailed parameter description, see :ref:`Configuration Parameters <obs_11_0035>`. If you do not configure this parameter, the upload and download rate will not be limited, but depend on the user's network bandwidth and the number of concurrent tasks. For details about the optimization, see :ref:`Fine-Tuning obsutil Performance <obs_11_0052>`.

Parameter **rateLimitThreshold** limits the global rate of obsutil tasks. This means that if you upload and download files in batches using the **cp** and **sync** commands, the actual upper rate is the one specified by **rateLimitThreshold**, not by the value obtained as follows: Number of concurrent tasks x Value of **rateLimitThreshold**.
