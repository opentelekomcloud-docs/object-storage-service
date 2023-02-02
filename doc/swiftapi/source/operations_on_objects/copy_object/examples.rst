:original_name: obs_03_0065.html

.. _obs_03_0065:

Examples
========

Use COPY Command to Copy Object
-------------------------------

Use the COPY command to copy an object. In this example, the source object is **janeausten/goodby** and the destination object is **marketwain/goodbye**.

.. code-block:: text

   curl -i http://172.28.54.12:80/v1/AUTH_4b34aa268d8c45879cf4da16443d3f95/marketwain/goodbye -H "X-Auth-Token:74565091b56b4783818430cecb283e7f"  -XCOPY -H "Destination:janeausten/goodbye"

.. code-block::

   HTTP/1.1 201 Created
   X-Trans-Id: tx000001513c9e87a1370c0-144543b5de
   Content-Type: text/html;charset=UTF-8
   Date: Wed, 25 Nov 2015 03:10:01 GMT
   ETag: e85f5c28b588fa64a379ba876e3591d2
   Last-Modified: Wed, 25 Nov 2015 03:10:01 GMT
   X-Copied-From: marketwain/goodbye
   X-Copied-From-Account: AUTH_4b34aa268d8c45879cf4da16443d3f95
   X-Copied-From-Last-Modified: Wed, 25 Nov 2015 03:04:55 GMT
   Content-Length: 0

Use PUT Command to Copy Object
------------------------------

Use the PUT command to copy an object. In this example, the source object is **janeausten/goodby** and the destination object is **marketwain/goodbye**.

.. code-block:: text

   curl -i http://172.28.54.12:80/v1/AUTH_4b34aa268d8c45879cf4da16443d3f95/janeausten/goodbye -H "X-Auth-Token:74565091b56b4783818430cecb283e7f" -H "X-Copy-from:/marketwain/goodbye" -XPUT -H "Content-Length:0"

.. code-block::

   HTTP/1.1 201 Created
   X-Trans-Id: tx000001513ca34816370c1-16ea772e65
   Content-Type: text/html;charset=UTF-8
   Date: Wed, 25 Nov 2015 03:15:12 GMT
   ETag: e85f5c28b588fa64a379ba876e3591d2
   Last-Modified: Wed, 25 Nov 2015 03:15:12 GMT
   X-Copied-From: marketwain/goodbye
   X-Copied-From-Account: AUTH_4b34aa268d8c45879cf4da16443d3f95
   X-Copied-From-Last-Modified: Wed, 25 Nov 2015 03:04:55 GMT
   Content-Length: 0
