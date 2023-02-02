:original_name: obs_03_0061.html

.. _obs_03_0061:

Examples
========

Create Object
-------------

Create **marktwain/goodbye**:

.. code-block:: text

   curl -i http://172.28.54.12:80/v1/AUTH_4b34aa268d8c45879cf4da16443d3f95/marketwain/goodbye -H "X-Auth-Token:74565091b56b4783818430cecb283e7f"  -XPUT -T ./goodbye.txt

.. code-block::

   HTTP/1.1 201 Created
   X-Trans-Id: tx000001513c8f12fd370c0-b7e3f340fc
   Content-Type: text/html;charset=UTF-8
   Date: Wed, 25 Nov 2015 02:53:08 GMT
   ETag: e85f5c28b588fa64a379ba876e3591d2
   Last-Modified: Wed, 25 Nov 2015 02:53:08 GMT
   Content-Length: 0

Replace Object
--------------

Replace **marktwain/goodbye** (repeated creation):

.. code-block:: text

   curl -i http://172.28.54.12:80/v1/AUTH_4b34aa268d8c45879cf4da16443d3f95/marketwain/goodbye -H "X-Auth-Token:74565091b56b4783818430cecb283e7f"  -XPUT -T ./goodbye.txt

.. code-block::

   HTTP/1.1 201 Created
   X-Trans-Id: tx000001513c99de91370c0-8a64466f2c
   Content-Type: text/html;charset=UTF-8
   Date: Wed, 25 Nov 2015 03:04:55 GMT
   ETag: e85f5c28b588fa64a379ba876e3591d2
   Last-Modified: Wed, 25 Nov 2015 03:04:55 GMT
   Content-Length: 0
