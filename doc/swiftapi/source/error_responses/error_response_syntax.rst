:original_name: obs_03_0014.html

.. _obs_03_0014:

Error Response Syntax
=====================

Error Response Headers
----------------------

When an error occurs, the header information contains:

Content-Type: application/``*``, which may be in HTML or text format

HTTP status code 3xx, 4xx, or 5xx. For details, see :ref:`Table 1 <obs_03_0013__table30733758>`.

Error Response Body
-------------------

The response body also contains information about the error. The following is an example of an error response body in an authentication failure.

.. code-block::

   <html><h1>Unauthorized</h1><p>This server could not verify that you are authorized to access the document you requested.</p></html>
