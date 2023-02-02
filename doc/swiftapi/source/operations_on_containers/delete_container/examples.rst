:original_name: obs_03_0040.html

.. _obs_03_0040:

Examples
========

Delete Empty Container
----------------------

Delete an empty **steven** container:

.. code-block:: text

   curl -i -H "X-auth-token:b85044aa87eb46b88552f1dcbae411e3" http://172.28.5.31:80/v1/AUTH_09ijuyhgt675432wert56yt789i0o98u/steven -X DELETE

.. code-block::

   HTTP/1.1 204 No Content
   X-Trans-Id: tx3d3e55d11af10dd917cdd-b205cb56e6
   Content-Length: 0
   Content-Type: text/html;charset=UTF-8
   Date: Sat, 19 Sep 2015 02:37:34 GMT

Delete Non-Existing Container
-----------------------------

Delete the non-existing **steve** container:

.. code-block:: text

   curl -i -H "X-auth-token:b85044aa87eb46b88552f1dcbae411e3" http://172.28.5.31:80/v1/AUTH_09ijuyhgt675432wert56yt789i0o98u/steve -X DELETE

.. code-block::

   HTTP/1.1 404 Not Found
   X-Trans-Id: txbfb5fe049899729a00e6d-e304231475
   Content-Type: text/html;charset=UTF-8
   Date: Sat, 19 Sep 2015 02:37:04 GMT
   Content-Length: 70

   <html><h1>Not Found</h1><p>The resource could not be found.</p></html>

Delete Non-Empty Container
--------------------------

Delete the non-empty **CONTAINER** container:

.. code-block:: text

   curl -i -H "X-auth-token:b85044aa87eb46b88552f1dcbae411e3" http://172.28.5.31:80/v1/AUTH_09ijuyhgt675432wert56yt789i0o98u/CONTAINER -X DELETE

.. code-block::

   HTTP/1.1 409 Conflict
   X-Trans-Id: tx920280c22ff4ec5f733a5-74a61c1cb9
   Content-Type: text/html;charset=UTF-8
   Date: Sat, 19 Sep 2015 02:33:28 GMT
   Content-Length: 95

   <html><h1>Conflict</h1><p>There was a conflict when trying to complete your request.</p></html>
