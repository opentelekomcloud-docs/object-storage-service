:original_name: obs_03_0064.html

.. _obs_03_0064:

Response
========

Response Headers
----------------

The following table describes response header parameters:

+-----------------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------+
| Header                      | Type                  | Description                                                                                                                    |
+=============================+=======================+================================================================================================================================+
| Content-Length              | String                | If the operation succeeds, this value is 0.                                                                                    |
|                             |                       |                                                                                                                                |
|                             | (Required)            | If the operation fails, this value is the length of the error text in the response body.                                       |
+-----------------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------+
| Last-Modified               | String                | Date and time that the object was created or the last time that the metadata was changed.                                      |
|                             |                       |                                                                                                                                |
|                             | (Required)            |                                                                                                                                |
+-----------------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------+
| X-Copied-From-Last-Modified | String                | For a copied object, it shows the last modified date and time.                                                                 |
|                             |                       |                                                                                                                                |
|                             | (Optional)            |                                                                                                                                |
+-----------------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------+
| X-Copied-From               | String                | For a copied object, it shows the container name and object name in the **{container}/{object}** format.                       |
|                             |                       |                                                                                                                                |
|                             | (Optional)            |                                                                                                                                |
+-----------------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------+
| X-Copied-From-Account       | String                | Account ID of the user who owns the object to be copied.                                                                       |
|                             |                       |                                                                                                                                |
|                             | (Optional)            |                                                                                                                                |
+-----------------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------+
| Etag                        | String                | For ordinary objects, this value is the MD5 checksum of the uploaded object content.                                           |
|                             |                       |                                                                                                                                |
|                             | (Required)            | For static large objects, this value is the MD5 checksum of the concatenated string of MD5 checksums for each of the segments. |
|                             |                       |                                                                                                                                |
|                             |                       | For dynamic large objects, the value is the MD5 checksum of the manifest file.                                                 |
+-----------------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------+
| X-Object-Meta-name          | String                | The custom object metadata item.                                                                                               |
|                             |                       |                                                                                                                                |
|                             | (Optional)            | **{name}** is the name of the metadata item.                                                                                   |
+-----------------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------+
| Content-Type                | String                | MIME type of the object.                                                                                                       |
|                             |                       |                                                                                                                                |
|                             | (Required)            |                                                                                                                                |
+-----------------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------+
| Date                        | String                | Transaction date and time.                                                                                                     |
|                             |                       |                                                                                                                                |
|                             | (Required)            |                                                                                                                                |
+-----------------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------+
| X-Trans-Id                  | Uuid                  | A unique transaction identifier.                                                                                               |
|                             |                       |                                                                                                                                |
|                             | (Required)            |                                                                                                                                |
+-----------------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------+
