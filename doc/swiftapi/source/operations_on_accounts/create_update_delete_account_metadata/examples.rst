:original_name: obs_03_0023.html

.. _obs_03_0023:

Examples
========

Create Account Metadata
-----------------------

Create Book and Subject metadata:

.. code-block:: text

   curl -i -H "X-auth-token:b8b574e33b0a4f74a1961bed1b4784b8" "http://172.28.5.31:80/v1/AUTH_0ce042a9be6140769b12c1001d41bcf9" -X POST -H "X-Account-Meta-Book:MobyDick" -H "X-Account-Meta-Subject:Literature"

.. code-block::

   HTTP/1.1 204 No Content
   X-Trans-Id: tx000001513971bc1a370c0-93967ab85f
   Content-Length: 0
   Content-Type: text/html;charset=UTF-8
   Date: Tue, 24 Nov 2015 12:22:13 GMT

Update Account Metadata
-----------------------

Update the Subject metadata:

.. code-block:: text

   curl -i -H "X-auth-token:b8b574e33b0a4f74a1961bed1b4784b8" "http://172.28.5.31:80/v1/AUTH_0ce042a9be6140769b12c1001d41bcf9" -X POST -H "X-Account-Meta-Subject:ChineseLiterature"

.. code-block::

   HTTP/1.1 204 No Content
   X-Trans-Id: tx0000015139725538370c0-f6e0c56435
   Content-Length: 0
   Content-Type: text/html;charset=UTF-8
   Date: Tue, 24 Nov 2015 12:22:53 GMT

Delete Account Metadata
-----------------------

Delete the Subject metadata:

.. code-block:: text

   curl -i -H "X-auth-token:b8b574e33b0a4f74a1961bed1b4784b8" "http://172.28.5.31:80/v1/AUTH_0ce042a9be6140769b12c1001d41bcf9" -X POST -H "X-Remove-Account-Meta-Subject:d"

.. code-block::

   HTTP/1.1 204 No Content
   X-Trans-Id: tx000001513972ce7c370c0-40b77d13e2
   Content-Length: 0
   Content-Type: text/html;charset=UTF-8
   Date: Tue, 24 Nov 2015 12:23:24 GMT
