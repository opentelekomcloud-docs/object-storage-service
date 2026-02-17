:original_name: obs_11_0079.html

.. _obs_11_0079:

How Can I Locate and Rectify I/O Timeout and EOF Errors?
========================================================

I/O timeout and EOF errors usually occur when requests fail due to network fluctuations. Go through the following list to locate the cause.

#. Ping the bucket domain name (*bucketName.endpoint*) to check the network connection between your local PC and the bucket. If the network connection is abnormal, resolve the network issue first.
#. If these errors are prone to occur and the bucket domain name can be pinged, use HTTP for the endpoint and capture network packets. Based on the packets captured, check whether packet loss occurs on the actual network link and resolve the errors accordingly.

Solutions:

#. If the network connection is abnormal, resolve the local network problem first. If you need to configure a proxy, see :ref:`Configuring an HTTP Proxy for obsutil <obs_11_0068>`.
#. If these errors occur occasionally, retry the command of your operation. During upload, download, or replication operations, specify the **-u** parameter in the **cp** command to perform an incremental upload. In this way, you do not need to retry the tasks that have been successfully completed in a batch task.
#. If the network condition is poor, you can decrease the values of **defaultParallels (-p)** and **defaultJobs (-j)** to reduce the number of concurrent upload, download, or replication tasks, to make errors less likely occur.
