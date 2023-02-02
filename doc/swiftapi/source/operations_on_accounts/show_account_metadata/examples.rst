:original_name: obs_03_0027.html

.. _obs_03_0027:

Examples
========

Show Account Metadata
---------------------

Show account metadata.

.. code-block:: text

   curl -i -H "X-Auth-token:9d6c288edff8434ea23108e6516ae5a5" "http://172.28.5.30:80/v1/AUTH_0ce042a9be6140769b12c1001d41bcf9" -X HEAD

.. code-block::

   HTTP/1.1 204 No Content
   X-Trans-Id: tx000001513970d65e370c0-0480bf0ace
   Accept-Ranges: bytes
   Content-Length: 0
   Content-Type: text/plain;charset=UTF-8
   Date: Tue, 24 Nov 2015 12:21:14 GMT
   X-Account-Bytes-Used: 0
   X-Account-Container-Count: 0
   X-Account-Meta-Book: firstbook
   X-Account-Object-Count: 0
   X-Account-Project-Domain-Id: default
   X-Timestamp: 1448367617.422
