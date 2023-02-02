:original_name: obs_03_0044.html

.. _obs_03_0044:

Examples
========

Create Container Metadata
-------------------------

Create container metadata **Author** with the value set to **MarkTwain**:

.. code-block:: text

   curl -i -H "X-auth-token:b85044aa87eb46b88552f1dcbae411e3" http://172.28.5.31:80/v1/AUTH_09ijuyhgt675432wert56yt789i0o98u/marktwain -X POST -H "X-Container-Meta-Author:MarkTwain"

.. code-block::

   HTTP/1.1 204 No Content
   X-Trans-Id: tx756aafaa7d2725f407980-172957b1a5
   Content-Type: text/html;charset=UTF-8
   Date: Sat, 19 Sep 2015 03:53:50 GMT
   Content-Length: 0

Update Container Metadata
-------------------------

Update container metadata **Author** with the value set to **Other**:

.. code-block:: text

   curl -i -H "X-auth-token:b85044aa87eb46b88552f1dcbae411e3" http://172.28.5.31:80/v1/AUTH_09ijuyhgt675432wert56yt789i0o98u/marktwain -X POST -H "X-Container-Meta-Author:Other"

.. code-block::

   HTTP/1.1 204 No Content
   X-Trans-Id: tx78195a4320339a358ef6b-7d910daaf2
   Content-Type: text/html;charset=UTF-8
   Date: Sat, 19 Sep 2015 03:54:07 GMT
   Content-Length: 0

Delete Container Metadata
-------------------------

Delete container metadata **Author** with the value set to any non-empty character string:

.. code-block:: text

   curl -i -H "X-auth-token:b85044aa87eb46b88552f1dcbae411e3" http://172.28.5.31:80/v1/AUTH_09ijuyhgt675432wert56yt789i0o98u/marktwain -X POST -H "X-Remove-Container-Meta-Author:x"

.. code-block::

   HTTP/1.1 204 No Content
   X-Trans-Id: txd55ee251c5c4eb7747016-84b51a54c0
   Content-Type: text/html;charset=UTF-8
   Date: Sat, 19 Sep 2015 03:54:30 GMT
   Content-Length: 0
