:original_name: obs_03_0077.html

.. _obs_03_0077:

Examples
========

Create Object Metadata
----------------------

Create object metadata **Author** with the value set to **other**:

.. code-block:: text

   curl -i http://172.28.54.12:80/v1/AUTH_4b34aa268d8c45879cf4da16443d3f95/marketwain/goodbye -H "X-Auth-Token:74565091b56b4783818430cecb283e7f"  -XPOST  -H "X-Object-Meta-author:other"

.. code-block::

   HTTP/1.1 202 Accepted
   X-Trans-Id: tx000001513cba7176370c1-adee95a013
   Content-Type: text/html;charset=UTF-8
   Date: Wed, 25 Nov 2015 03:40:30 GMT
   Content-Length: 76

   <html><h1>Accepted</h1><p>The request is accepted for processing.</p></html>

Update Object Metadata
----------------------

Update object metadata **Author** with the value set to **marktwain**:

.. code-block:: text

   curl -i http://172.28.54.12:80/v1/AUTH_4b34aa268d8c45879cf4da16443d3f95/marketwain/goodbye -H "X-Auth-Token:74565091b56b4783818430cecb283e7f"  -XPOST  -H "X-Object-Meta-author:marktwain"

.. code-block::

   HTTP/1.1 202 Accepted
   X-Trans-Id: tx000001513cbfbf2f370c2-f9e7f1cf40
   Content-Type: text/html;charset=UTF-8
   Date: Wed, 25 Nov 2015 03:46:18 GMT
   Content-Length: 76

   <html><h1>Accepted</h1><p>The request is accepted for processing.</p></html>

Delete Object Metadata
----------------------

Delete the metadata author, and leave the value blank.

.. code-block:: text

   curl -i http://172.28.54.12:80/v1/AUTH_4b34aa268d8c45879cf4da16443d3f95/marketwain/goodbye -H "X-Auth-Token:74565091b56b4783818430cecb283e7f"  -XPOST  -H "X-Object-Meta-author:"

.. code-block::

   HTTP/1.1 202 Accepted
   X-Trans-Id: tx000001513cc10d85370c2-cddc60cba5
   Content-Type: text/html;charset=UTF-8
   Date: Wed, 25 Nov 2015 03:47:43 GMT
   Content-Length: 76

   <html><h1>Accepted</h1><p>The request is accepted for processing.</p></html>
