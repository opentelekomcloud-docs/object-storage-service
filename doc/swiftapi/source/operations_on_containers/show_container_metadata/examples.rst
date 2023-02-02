:original_name: obs_03_0048.html

.. _obs_03_0048:

Examples
========

Show Container Metadata
-----------------------

Show metadata of container **marktwain**:

.. code-block:: text

   curl -i -H "X-auth-token:b85044aa87eb46b88552f1dcbae411e3" http://172.28.5.31:80/v1/AUTH_09ijuyhgt675432wert56yt789i0o98u/marktwain -X HEAD

.. code-block::

   HTTP/1.1 204 No Content
   X-Trans-Id: tx0e8b58d90e74b1b043db5-15554c1c1a
   Accept-Ranges: bytes
   Content-Type: text/plain;charset=UTF-8
   Date: Sat, 19 Sep 2015 04:35:29 GMT
   X-Container-Bytes-Used: 27
   X-Container-Meta-Author: Other
   X-Container-Object-Count: 1
   X-Timestamp: 1442632853817
   Content-Length: 0
