:original_name: obs_03_0073.html

.. _obs_03_0073:

Examples
========

Show Object Metadata
--------------------

Show metadata of the **goodbye** object in the **marketwain** container:

.. code-block:: text

   curl -i http://172.28.54.12:80/v1/AUTH_4b34aa268d8c45879cf4da16443d3f95/marketwain/goodbye -H "X-Auth-Token:74565091b56b4783818430cecb283e7f"  -XHEAD

.. code-block::

   HTTP/1.1 200 OK
   X-Trans-Id: tx000001513cbab7ca370c1-d95dee8729
   Accept-Ranges: bytes
   Content-Length: 15
   Content-Type: application/octet-stream
   Date: Wed, 25 Nov 2015 03:40:48 GMT
   ETag: e85f5c28b588fa64a379ba876e3591d2
   Last-Modified: Wed, 25 Nov 2015 03:40:30 GMT
   X-Object-Meta-Author: other
   X-Timestamp: 1448422830.47760
