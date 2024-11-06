:original_name: obs_03_0031.html

.. _obs_03_0031:

Overview
========

Application Scenario
--------------------

After you upload a file to a bucket, you can access this file using the bucket's access domain name by default. If you want to use a custom domain name to access the file, bind the custom domain name to the bucket.

Assume that you have a domain name **www.example.com** and you upload an image **image.png** to an OBS bucket. As long as you bind **www.example.com** to the bucket, you can use **http://www.example.com/image.png** to access **image.png**. The steps below describe the configurations:

#. Create a bucket on OBS and upload file **image.png** to the bucket.
#. On OBS Console, bind **www.example.com** to the created bucket.
#. On the DNS server, add a CNAME record and map **www.example.com** to the domain name of the bucket.
#. Send a request for image **image.png**. After the request for **http://www.example.com/image.png** reaches OBS, OBS finds the mapping between the **www.example.com** and the bucket's domain name, and redirects the request to the **image.png** file stored in the bucket. This way, a request for **http://www.example.com/image.png** actually accesses **http://**\ *Bucket domain name*\ **/image.png**.

Constraints
-----------

#. Only buckets whose version is 3.0 or later support the configuration of user-defined domain names. The version number of a bucket is displayed in the **Basic Information** area.
#. User-defined domain names currently allow requests over HTTP, instead of HTTPS.
#. A user-defined domain name can be bound to only one bucket.
#. The suffix of a user-defined domain name can contain 2 to 6 uppercase or lowercase letters.
