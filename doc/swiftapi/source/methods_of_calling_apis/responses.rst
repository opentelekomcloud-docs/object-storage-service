:original_name: obs_03_0011.html

.. _obs_03_0011:

Responses
=========

OBS (compatible with OpenStack Swift) returns an HTTP response after receiving and processing a request.

Syntax
------

.. code-block::

   Status Line: HTTP-Version Status-Code Reason-Phrase
   Response Headers
   <Conditional Response Body>

Status Line
-----------

The first line of a response is the Status-Line, consisting of the protocol version, numeric status code, and textual phrases. The previous elements are separated by spaces. See :ref:`Table 1 <obs_03_0011__table47156901>`.

.. _obs_03_0011__table47156901:

.. table:: **Table 1** Status line elements

   +---------------+--------------------------------------------------------------------+
   | Element       | Description                                                        |
   +===============+====================================================================+
   | HTTP-Version  | HTTP version. OBS (compatible with OpenStack Swift) uses HTTP 1.1. |
   +---------------+--------------------------------------------------------------------+
   | Status-Code   | Status code, which describes the response type.                    |
   +---------------+--------------------------------------------------------------------+
   | Reason-Phrase | Reason phrase, which describes the status code in a short text.    |
   +---------------+--------------------------------------------------------------------+

The first digit of the status code defines the response type. The last two digits do not have this function. There are five types of status codes, categorized based on the first digit. The categories are described in :ref:`Table 2 <obs_03_0011__table46218860>`.

.. _obs_03_0011__table46218860:

.. table:: **Table 2** Status codes in OBS (compatible with OpenStack Swift)

   +-------------+------------------------------------------------------------------------------------------------+
   | Status Code | Description                                                                                    |
   +=============+================================================================================================+
   | 1xx         | The server has received but is still processing the request.                                   |
   +-------------+------------------------------------------------------------------------------------------------+
   | 2xx         | The request has been received, understood, and accepted.                                       |
   +-------------+------------------------------------------------------------------------------------------------+
   | 3xx         | The client must take further actions to complete the request.                                  |
   +-------------+------------------------------------------------------------------------------------------------+
   | 4xx         | There was an error on the client side. The request contains bad syntax or cannot be fulfilled. |
   +-------------+------------------------------------------------------------------------------------------------+
   | 5xx         | There was an error on the server side. The server failed to fulfill a valid request.           |
   +-------------+------------------------------------------------------------------------------------------------+

-  A 1xx status code is a provisional response. :ref:`Table 3 <obs_03_0011__table52995244111757>` describes the 1xx status code in OBS (compatible with OpenStack Swift).

.. _obs_03_0011__table52995244111757:

.. table:: **Table 3** 1xx status code

   +-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
   | Status Code           | Description                                                                                                                                    | Returned After        |
   +=======================+================================================================================================================================================+=======================+
   | 100 Continue          | The initial part of the request has been received and has not yet been rejected by the server and the client should continue with its request. | -  PUT Object         |
   |                       |                                                                                                                                                | -  POST Object        |
   +-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+

-  A 2xx status code indicates that a request has been successfully processed by the server. :ref:`Table 4 <obs_03_0011__table33573506>` describes all 2xx status codes in OBS (compatible with OpenStack Swift).

.. _obs_03_0011__table33573506:

.. table:: **Table 4** 2xx status codes

   +-----------------------+------------------------------------------------------------------------------------+---------------------------------------------------+
   | Status Code           | Description                                                                        | Returned After                                    |
   +=======================+====================================================================================+===================================================+
   | 200 OK                | The server has received and accepted the client's request.                         | -  List Objects                                   |
   |                       |                                                                                    | -  GET Object                                     |
   |                       |                                                                                    | -  GET Object Metadata                            |
   +-----------------------+------------------------------------------------------------------------------------+---------------------------------------------------+
   | 201 Created           | The response may contain an XML file. The XML file describes the response content. | -  PUT Container                                  |
   |                       |                                                                                    | -  PUT Object                                     |
   +-----------------------+------------------------------------------------------------------------------------+---------------------------------------------------+
   | 202 Accepted          | The server has received the request.                                               | -  POST operations (Update object metadata)       |
   +-----------------------+------------------------------------------------------------------------------------+---------------------------------------------------+
   | 204 No Content        | The server has processed a request successfully, but no content was returned.      | -  HEAD Container                                 |
   |                       |                                                                                    | -  POST operations on access control lists (ACLs) |
   |                       |                                                                                    | -  DELETE Object                                  |
   |                       |                                                                                    | -  DELETE Container                               |
   +-----------------------+------------------------------------------------------------------------------------+---------------------------------------------------+

-  A 3xx status code indicates that a request can be successfully processed only after being redirected. :ref:`Table 5 <obs_03_0011__table49785318>` describes all 3xx status codes in OBS (compatible with OpenStack Swift).

.. _obs_03_0011__table49785318:

.. table:: **Table 5** 3xx status codes

   +-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------+-------------------------------------------------------------------------------+
   | Status Code           | Description                                                                                                                                             | Returned After                                                                |
   +=======================+=========================================================================================================================================================+===============================================================================+
   | 303 See Other         | The client can use another URL to get a specific object.                                                                                                | POST operations (provided that redirection parameters in requests are valid.) |
   +-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------+-------------------------------------------------------------------------------+
   | 304 Not Modified      | After the client sent a GET request with the required modification time, access was allowed but the resource was not modified after the specified time. | The resource is obtained but the modification time condition is not met.      |
   +-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------+-------------------------------------------------------------------------------+
   | 307 Moved Temporarily | A request has been redirected.                                                                                                                          | A request is redirected after it fails to be processed by the server.         |
   +-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------+-------------------------------------------------------------------------------+

-  A 4xx status code indicates that a request failed to be processed due to a client error. A 4xx status code is returned together with a response body containing error details. 4xx status codes apply to all request methods except HEAD. For more details, see the definition of 4xx status codes.

.. table:: **Table 6** 4xx status codes

   +------------------------------+----------------------------------------------------------------------------------------------------+------------------------------------------------------------------------------------------------------------+
   | Status Code                  | Description                                                                                        | Returned After                                                                                             |
   +==============================+====================================================================================================+============================================================================================================+
   | 400 Bad Request              | The syntax of a request was incorrect.                                                             | A request in incorrect syntax or containing incorrect parameters is sent.                                  |
   +------------------------------+----------------------------------------------------------------------------------------------------+------------------------------------------------------------------------------------------------------------+
   | 401 Unauthorized             | The request could not be authenticated.                                                            | The user does not exist or the authentication information in a sent request is incorrect.                  |
   +------------------------------+----------------------------------------------------------------------------------------------------+------------------------------------------------------------------------------------------------------------+
   | 403 Forbidden                | The server refused the request.                                                                    | The user does not have sufficient permissions.                                                             |
   +------------------------------+----------------------------------------------------------------------------------------------------+------------------------------------------------------------------------------------------------------------+
   | 404 Not Found                | The requested resource does not exist.                                                             | The requested resource (such as a container or object) does not exist.                                     |
   +------------------------------+----------------------------------------------------------------------------------------------------+------------------------------------------------------------------------------------------------------------+
   | 411 Length Required          | The request header did not contain the required **Content-Length** or **Transfer-Encoding** field. | A request containing no **Content-Length** header is sent.                                                 |
   +------------------------------+----------------------------------------------------------------------------------------------------+------------------------------------------------------------------------------------------------------------+
   | 412 Precondition Failed      | Conditions are not met.                                                                            | Conditions are not met, if the object query request contains the **If-Match** or **If-None-Match** header. |
   +------------------------------+----------------------------------------------------------------------------------------------------+------------------------------------------------------------------------------------------------------------+
   | 413 Request Entity Too Large | Insufficient user quota.                                                                           | User storage capacity exceeds user quota when uploading or replicating objects.                            |
   +------------------------------+----------------------------------------------------------------------------------------------------+------------------------------------------------------------------------------------------------------------+

-  A 5xx status code means that the server encountered an error when processing the request or failed to process the request. Except for HEAD requests, a 5xx status code is returned together with a response body containing error details. :ref:`Table 7 <obs_03_0011__table16341824>` describes all 5xx status codes in OBS (compatible with OpenStack Swift).

.. _obs_03_0011__table16341824:

.. table:: **Table 7** 5xx status codes

   +-------------------------+-------------------------------------------+---------------------------------------------+
   | Status Code             | Description                               | Returned After                              |
   +=========================+===========================================+=============================================+
   | 500 Internal Error      | An internal error occurred on the server. | An internal error occurred on the server.   |
   +-------------------------+-------------------------------------------+---------------------------------------------+
   | 503 Service Unavailable | The server was overloaded.                | The server is processing too many requests. |
   +-------------------------+-------------------------------------------+---------------------------------------------+

Response Headers
----------------

A response header is the information appended to a response, as described in :ref:`Table 8 <obs_03_0011__table53316885>`. Response headers describe the server and contain further information about accessing the requested resource.

.. _obs_03_0011__table53316885:

.. table:: **Table 8** Response headers

   +----------------+--------------------------------------------------------------------------------------+---------------------------------------------------------------------------+
   | Header         | Description                                                                          | Applicable To                                                             |
   +================+======================================================================================+===========================================================================+
   | Content-Length | Length of a response body                                                            | All responses (except those responses whose transfer-encoding is chunked) |
   +----------------+--------------------------------------------------------------------------------------+---------------------------------------------------------------------------+
   | Date           | The date and time when a response was generated                                      | All responses                                                             |
   +----------------+--------------------------------------------------------------------------------------+---------------------------------------------------------------------------+
   | X-Trans-Id     | A unique identifier generated by OBS (compatible with OpenStack Swift) for a request | All responses                                                             |
   +----------------+--------------------------------------------------------------------------------------+---------------------------------------------------------------------------+
   | Content-Type   | The object type returned                                                             | All responses                                                             |
   +----------------+--------------------------------------------------------------------------------------+---------------------------------------------------------------------------+

.. note::

   OBS (compatible with OpenStack Swift) normalizes the content of the **Content-Type**. The content returned is different from that returned by OpenStack Swift in the following way:

   -  **Content-Type** content uses only **charset=UTF-8** (UTF in uppercase).

Response Body
-------------

In OBS (compatible with OpenStack Swift), a response body is included in a request response under the following conditions:

-  GET Object

   If the object is not blank, the response body is the object body.

-  GET Account or Container

   The response body is account or container information.

-  Client error

   The response body describes the client error in detail in XML format so that the user can perform further operations. For details, see client error response codes.

-  Server error

   The response body describes the server error in detail in XML format so that the user can perform further operations.

Error Responses
---------------

OBS (compatible with OpenStack Swift) returns an error response if a request is incorrect, the permission is incorrect, or the requested container or object is not found. An error response describes the error. When you upload an object, if permissions cannot be authenticated, the following information (in HTML format) is displayed:

.. code-block::

   <html><h1>Unauthorized</h1><p>This server could not verify that you are authorized to access the document you requested.</p></html>
