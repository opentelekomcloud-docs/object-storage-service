:original_name: en-us_topic_0045853630.html

.. _en-us_topic_0045853630:

Configuring the System
======================

This section describes how to modify system configurations.

Procedure
---------

#. Log in to OBS Browser.

#. In the upper right corner of OBS Browser, click |image1| and choose **System Configuration**. The **System Configuration** dialog box is displayed, see :ref:`Figure 1 <en-us_topic_0045853630__fig42068739173655>`.

   .. _en-us_topic_0045853630__fig42068739173655:

   .. figure:: /_static/images/en-us_image_0129866628.png
      :alt: **Figure 1** Configuring the system

      **Figure 1** Configuring the system

#. Click **General** and modify basic parameters as required.

   :ref:`Table 1 <en-us_topic_0045853630__t5b000a761ce742d3a008e78296aa7e23>` describes the parameters that can be modified.

   .. _en-us_topic_0045853630__t5b000a761ce742d3a008e78296aa7e23:

   .. table:: **Table 1** General configuration parameters

      +-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter                         | Description                                                                                                                                                                                                                                                                                                                                                                                      |
      +===================================+==================================================================================================================================================================================================================================================================================================================================================================================================+
      | Enable HTTPS                      | If this option is selected, all communications information will be encrypted and then transferred to OBS over HTTPS.                                                                                                                                                                                                                                                                             |
      +-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Enable certificate verification   | When this option is selected, the client will verify the server certificate.                                                                                                                                                                                                                                                                                                                     |
      +-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Enable KMS encryption             | When **Enable HTTPS** and **Enable KMS encryption** are selected, KMS encryption will be implemented for all objects uploaded to OBS.                                                                                                                                                                                                                                                            |
      +-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Multipart Upload, Part Size (MB)  | OBS uses multipart uploads by default. Objects larger than the specified part size (5 MB by default) will be uploaded using multipart upload in the background. You can adjust the size of each part as needed. The value of **Part Size (MB)** can range from 5 MB to 5 GB.                                                                                                                     |
      |                                   |                                                                                                                                                                                                                                                                                                                                                                                                  |
      |                                   | .. note::                                                                                                                                                                                                                                                                                                                                                                                        |
      |                                   |                                                                                                                                                                                                                                                                                                                                                                                                  |
      |                                   |    Multipart upload is used by default. Recommended settings of **Part Size (MB)** are as follows:                                                                                                                                                                                                                                                                                               |
      |                                   |                                                                                                                                                                                                                                                                                                                                                                                                  |
      |                                   |    To maximize client performance, set **Part Size (MB)** based on the upload speed. You are advised to set the **Part Size (MB)** value larger than the maximum upload speed. For example, if the maximum upload speed is 10 MB/s, set **Part Size (MB)** to an integer greater than 10 MB. It is recommended that the part size be set to a value two to three times the maximum upload speed. |
      +-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Max Number of Upload Tasks        | Specifies the maximum number of upload tasks. Enter an integer ranging from 2 to 20.                                                                                                                                                                                                                                                                                                             |
      +-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Max Number of Download Tasks      | Specifies the maximum number of download tasks. Enter an integer ranging from 5 to 50.                                                                                                                                                                                                                                                                                                           |
      +-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

#. Click **Network** and set proxy server information as required. See :ref:`Figure 2 <en-us_topic_0045853630__fig543149173827>`.

   .. _en-us_topic_0045853630__fig543149173827:

   .. figure:: /_static/images/en-us_image_0129866667.png
      :alt: **Figure 2** Network configurations

      **Figure 2** Network configurations

   .. table:: **Table 2** Network configuration parameters

      +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter                         | Description                                                                                                                                             |
      +===================================+=========================================================================================================================================================+
      | Enable proxy                      | Selecting this option will display the **Authentication** option. By configuring the following parameters, you can access OBS through the proxy server: |
      |                                   |                                                                                                                                                         |
      |                                   | -  Address: domain name or IP address of the proxy server                                                                                               |
      |                                   | -  Port: port of the proxy server (default port is **8080**)                                                                                            |
      +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------+

#. Click **Other** and set the parameters as required. For details, see :ref:`Figure 3 <en-us_topic_0045853630__fig2876079495946>`.

   .. _en-us_topic_0045853630__fig2876079495946:

   .. figure:: /_static/images/en-us_image_0129867351.png
      :alt: **Figure 3** Other configurations

      **Figure 3** Other configurations

   .. table:: **Table 3** Other parameters

      +------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter                                | Description                                                                                                                                                                                                                                      |
      +==========================================+==================================================================================================================================================================================================================================================+
      | Enable automatic update check            | If this option is selected, each time when you log in to OBS Browser, a check will be automatically performed to determine whether the current software version is the latest.                                                                   |
      +------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Number of Objects Displayed on Each Page | Set the number of objects that are displayed on each page. The default value is 100. The value ranges from 50 to 300. After setting the value, click the |image3| button in the upper right corner of the page so that the setting takes effect. |
      +------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

#. Click **Save** to save the system configuration.

.. |image1| image:: /_static/images/en-us_image_0237530299.png
.. |image2| image:: /_static/images/en-us_image_0148639825.png
.. |image3| image:: /_static/images/en-us_image_0148639825.png
