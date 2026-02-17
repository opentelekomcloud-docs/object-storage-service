:original_name: obs_11_0068.html

.. _obs_11_0068:

Configuring an HTTP Proxy for obsutil
=====================================

You can configure an HTTP proxy in either of the following ways:

Method 1: Set the **proxyUrl** parameter in the **.obsutilconfig** file, for example, **proxyUrl=http://username:password@your-proxy:8080**.

Method 2: Use the system environment variable **HTTPS_PROXY** or **HTTP_PROXY**, for example, **HTTPS_PROXY=http://username:password@your-proxy:8080**.

.. note::

   -  HTTP proxy format: **http://[Username:Password\ @]\ Proxy server address:Port number**. The *Username* and *Password* are optional.
   -  The **proxyUrl** parameter and system environment variables are in the following priority order: **proxyUrl** > **HTTPS_PROXY** > **HTTP_PROXY**.
   -  The user name and password cannot contain colons (:) and at signs (@), which will result in parsing errors.
