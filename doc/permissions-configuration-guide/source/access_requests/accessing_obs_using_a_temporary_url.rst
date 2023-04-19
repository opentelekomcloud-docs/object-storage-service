:original_name: obs_40_0009.html

.. _obs_40_0009:

Accessing OBS Using a Temporary URL
===================================

You can use a temporary URL to access OBS and perform operations such as bucket creation or object upload and download. This section describes how to share objects using a temporary URL.

Sharing Objects
---------------

You can share objects (files or folders) stored in OBS with all users within a specified period.

**Sharing a file**

All URLs generated during file sharing are temporary and remain valid for a limited period of time.

A temporary URL uses V4 temporarily authorized requests. The following is a temporary URL sample:

.. code-block::

   https://oss.regionid.example.region.com/bucketname/objectname?X-Amz-Algorithm=xxx&X-Amz-Credential=xxx&X-Amz-Date=xxx&X-Amz-Expires=900&X-Amz-Signature=xxx&X-Amz-SignedHeaders=xxx&response-content-disposition=xxx

For details about the temporary authentication and parameters, see `V4 Temporarily Authorized Request <https://docs.otc.t-systems.com/en-us/api_obs/obs/en-us_topic_0125560420.html>`__ in the *Object Storage Service API Reference*. A temporary URL also contains the **response-content-disposition** parameter that defines whether an object is directly downloaded or previewed in a browser when it is accessed. This is determined by the browser based on the **Content-Type** of the shared object.

After you share an object by choosing **More** > **Copy Object URL** on OBS Console, the system will generate a URL that contains the temporary authentication information, valid for 900 seconds since its generation by default. Each time you click **Copy Object URL**, OBS will obtain the authentication information again to generate a new sharing URL whose validity period is reset.

Limitations and Constraints
---------------------------

-  The validity period of files shared through OBS Console is fixed at 900s. If you want a file to be accessed permanently, you can configure `a bucket policy or an object policy <https://docs.otc.t-systems.com/usermanual/obs/en-us_topic_0045853745.html>`__.
-  Only buckets 3.0 support file and folder sharing. You can view the bucket version in the **Basic Information** area on the **Overview** page of a bucket.
-  To share a cold object, restore it first.
