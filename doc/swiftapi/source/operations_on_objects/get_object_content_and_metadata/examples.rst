:original_name: obs_03_0057.html

.. _obs_03_0057:

Examples
========

Show Object Details
-------------------

Show the content and metadata of the **goodbye** object in the **marktwain** container:

.. code-block:: text

   curl -i http://172.28.54.12:80/v1/AUTH_4b34aa268d8c45879cf4da16443d3f95/marketwain/goodbye -H "X-Auth-Token:74565091b56b4783818430cecb283e7f"  -XGET

.. code-block::

   HTTP/1.1 200 OK
   X-Trans-Id: tx000001513c8f3596370c0-d09b6a1f24
   Accept-Ranges: bytes
   Content-Length: 15
   Content-Type: application/octet-stream
   Date: Wed, 25 Nov 2015 02:53:17 GMT
   ETag: e85f5c28b588fa64a379ba876e3591d2
   Last-Modified: Wed, 25 Nov 2015 02:53:08 GMT
   X-Timestamp: 1448419988.76750

   [15 Byte data content]

Show Object Details for a Non-Existing Object
---------------------------------------------

Show object details for the **notexist** object, which does not exist, in the **marktwain** container:

.. code-block:: text

   curl -i http://172.28.54.12:80/v1/AUTH_4b34aa268d8c45879cf4da16443d3f95/marketwain/notexist -H "X-Auth-Token:74565091b56b4783818430cecb283e7f"  -XGET

.. code-block::

   HTTP/1.1 404 Not Found
   X-Trans-Id: tx000001513c90aab6370c0-b90ea4b1b7
   Content-Type: text/html;charset=UTF-8
   Date: Wed, 25 Nov 2015 02:54:52 GMT
   Content-Length: 70

   <html><h1>Not Found</h1><p>The resource could not be found.</p></html>
