:original_name: obs_03_0052.html

.. _obs_03_0052:

Examples
========

Delete Empty Containers
-----------------------

Delete two empty containers: **8projectidprojectidproject000023.bucket.test6.0** and **8projectidprojectidproject000023.bucket.test6.1**, and delete the container text file **deletesample**:

.. code-block::

   /8projectidprojectidproject000023.bucket.test6.0
   /8projectidprojectidproject000023.bucket.test6.1

Execute the deletion:

.. code-block:: text

   curl -i -H "X-auth-token:b85044aa87eb46b88552f1dcbae411e3" http://172.28.5.31:80/v1/AUTH_09ijuyhgt675432wert56yt789i0o98u?bulk-delete -XPOST -T ./deletesample

.. code-block::

   HTTP/1.1 100 Continue

   HTTP/1.1 200 OK
   X-Trans-Id: tx0000015f80c43411770b1-a2dbb9e7c9
   Date: Fri, 03 Nov 2017 07:24:22 GMT
   Content-Type: text/plain;charset=ISO-8859-1
   Transfer-Encoding: chunked

   Number Deleted: 2
   Number Not Found: 0
   Response Body:
   Response Status: 200 OK
   Errors:
