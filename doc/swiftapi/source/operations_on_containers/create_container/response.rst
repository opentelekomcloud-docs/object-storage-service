:original_name: obs_03_0035.html

.. _obs_03_0035:

Response
========

Response Headers
----------------

+-----------------------+-----------------------+----------------------------------+
| Header                | Type                  | Description                      |
+=======================+=======================+==================================+
| Content-Length        | String                | Length of a response body.       |
|                       |                       |                                  |
|                       | (Required)            |                                  |
+-----------------------+-----------------------+----------------------------------+
| Content-Type          | String                | MIME type of the object.         |
|                       |                       |                                  |
|                       | (Required)            |                                  |
+-----------------------+-----------------------+----------------------------------+
| Date                  | Datetime              | Transaction date and time.       |
|                       |                       |                                  |
|                       | (Required)            |                                  |
+-----------------------+-----------------------+----------------------------------+
| X-Trans-Id            | Uuid                  | A unique transaction identifier. |
|                       |                       |                                  |
|                       | (Required)            |                                  |
+-----------------------+-----------------------+----------------------------------+

Response Body Parameters
------------------------

The request does not include response body parameters.

Error Responses
---------------

All the error responses are contained in :ref:`Table 1 <obs_03_0013__table30733758>`.
