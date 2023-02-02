:original_name: obs_03_0013.html

.. _obs_03_0013:

Error Code List
===============

If OBS (compatible with OpenStack Swift) encounters an error when processing a request, a response containing the error code and error description is returned. :ref:`Table 1 <obs_03_0013__table30733758>` describes all error codes in OBS (compatible with OpenStack Swift).

.. _obs_03_0013__table30733758:

.. table:: **Table 1** List of error codes in OBS (compatible with OpenStack Swift)

   +--------------------------+---------------------------------------------------------------------------------------------------------------------+--------------------------------------------+
   | Error Code               | Description                                                                                                         | HTTP Status Code                           |
   +==========================+=====================================================================================================================+============================================+
   | Moved Permanently        | The requested resource must be addressed using a specified node. Send all future requests to the node.              | 301 Moved Permanently                      |
   +--------------------------+---------------------------------------------------------------------------------------------------------------------+--------------------------------------------+
   | Not Modified             | The requested resource has not changed (since the last access or based on the conditions specified in the request). | 304 Not Modified                           |
   +--------------------------+---------------------------------------------------------------------------------------------------------------------+--------------------------------------------+
   | Bad Request              | The syntax of a request was incorrect.                                                                              | 400 Bad Request                            |
   +--------------------------+---------------------------------------------------------------------------------------------------------------------+--------------------------------------------+
   | Unauthorized             | Unauthorized. The authentication failed or the token is invalid.                                                    | 401Unauthorized                            |
   +--------------------------+---------------------------------------------------------------------------------------------------------------------+--------------------------------------------+
   | Forbidden                | The access was denied.                                                                                              | 403 Forbidden                              |
   +--------------------------+---------------------------------------------------------------------------------------------------------------------+--------------------------------------------+
   | Not Found                | The requested resource does not exist.                                                                              | 404 Not Found                              |
   +--------------------------+---------------------------------------------------------------------------------------------------------------------+--------------------------------------------+
   | Method Not Allowed       | The specified method is not allowed on the requested resource.                                                      | 405 Method Not Allowed                     |
   +--------------------------+---------------------------------------------------------------------------------------------------------------------+--------------------------------------------+
   | Not Acceptable           | Not acceptable. The request may contain invalid parameters or headers.                                              | 406 Not Acceptable                         |
   +--------------------------+---------------------------------------------------------------------------------------------------------------------+--------------------------------------------+
   | Conflict                 | This operation caused a conflict. For example, a non-empty container is deleted.                                    | 409 Conflict                               |
   +--------------------------+---------------------------------------------------------------------------------------------------------------------+--------------------------------------------+
   | Missing Content Length   | HTTP headers must contain the **Content-Length** field.                                                             | 411 Length Required                        |
   +--------------------------+---------------------------------------------------------------------------------------------------------------------+--------------------------------------------+
   | Precondition Failed      | At least one specified precondition has not been met.                                                               | 412 Precondition Failed                    |
   +--------------------------+---------------------------------------------------------------------------------------------------------------------+--------------------------------------------+
   | Request Entity Too Large | The amount of data to be uploaded has exceeded what is supported.                                                   | 413 Request Entity Too Large               |
   +--------------------------+---------------------------------------------------------------------------------------------------------------------+--------------------------------------------+
   | Invalid Range            | The requested range cannot be obtained.                                                                             | 416 Client Requested Range Not Satisfiable |
   +--------------------------+---------------------------------------------------------------------------------------------------------------------+--------------------------------------------+
   | Unprocessable Entity     | The request format is correct but contains incorrect syntax, making it unprocessable.                               | 422 Unprocessable Entity                   |
   +--------------------------+---------------------------------------------------------------------------------------------------------------------+--------------------------------------------+
   | Internal Error           | Internal error. Please retry.                                                                                       | 500 Internal Server Error                  |
   +--------------------------+---------------------------------------------------------------------------------------------------------------------+--------------------------------------------+
   | Service Unavailable      | The service is unavailable.                                                                                         | 503 Service Unavailable                    |
   +--------------------------+---------------------------------------------------------------------------------------------------------------------+--------------------------------------------+
