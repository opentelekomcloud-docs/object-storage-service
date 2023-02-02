:original_name: obs_03_0007.html

.. _obs_03_0007:

Locating a Resource
===================

In REST, specific information or data on a network is represented by a resource, which is referenced with a uniform resource identifier (URI). Clients on a network can locate resources using uniform resource locators (URLs). In OBS (compatible with OpenStack Swift), a resource can be an account, container, object, or specific resource related to an account, container, or object. Such a resource is identified by a URL and can be operated after requests are sent using the URL.

The common URL format is as follows (the content in brackets ([ ]) is optional):

protocol ://hostname[:port] /v1/account[/container] [/object] [?param]

:ref:`Table 1 <obs_03_0007__table6854763>` describes parameters in a URL.

.. _obs_03_0007__table6854763:

.. table:: **Table 1** URL parameters

   +-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
   | Parameter             | Description                                                                                                                                                                                                                                                                     | Required or Optional  |
   +=======================+=================================================================================================================================================================================================================================================================================+=======================+
   | protocol              | The protocol used for sending requests. Possible values include HTTP and HTTPS.                                                                                                                                                                                                 | Required              |
   |                       |                                                                                                                                                                                                                                                                                 |                       |
   |                       | You can specify HTTPS to ensure secure access to resources.                                                                                                                                                                                                                     |                       |
   +-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
   | hostname              | The host name, namely, the domain name or service IP address of OBS (compatible with OpenStack Swift).                                                                                                                                                                          | Required              |
   +-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
   | port                  | The port enabled for protocols used for sending requests. The value varies with software server deployment. In OBS (compatible with OpenStack Swift), the HTTP port is **80** and the HTTPS port is **443**. If this parameter is not specified, the default port will be used. | Optional              |
   +-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
   | v1                    | The version used in the request. **v1** indicates the object storage version.                                                                                                                                                                                                   | Required              |
   +-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
   | account               | A user path. Each path identifies a unique user in the system. An account consists of a management prefix and a project ID, for example, **AUTH\_**\ *ProjectID*.                                                                                                               | Required              |
   +-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
   | container             | A container path.                                                                                                                                                                                                                                                               | Optional              |
   +-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
   | object                | An object path.                                                                                                                                                                                                                                                                 | Optional              |
   +-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
   | param                 | The specific resource. By default, it is the requested container or object itself.                                                                                                                                                                                              | Optional              |
   +-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+

.. important::

   For security reasons, HTTP is not recommended. HTTPS should be used instead.

   In OBS (compatible with OpenStack Swift), HTTPS supports TLS 1.2 only.

.. note::

   If the version in a URL is set to V1 (the correct one is actually v1), OBS (compatible with OpenStack Swift) returns a 404 Not Found error code, whereas OpenStack Swift returns a 400 Bad Request error code.
