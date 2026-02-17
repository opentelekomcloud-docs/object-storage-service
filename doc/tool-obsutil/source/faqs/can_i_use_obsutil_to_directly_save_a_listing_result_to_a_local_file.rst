:original_name: obs_11_0076.html

.. _obs_11_0076:

Can I Use obsutil to Directly Save a Listing Result to a Local File?
====================================================================

obsutil does not allow you to directly save a listing result to a local file, but you can redirect a listing result displayed on the screen in standard output to a specified local file by relying on the redirection supported by OS. The following uses the listing of objects in a bucket as an example:

-  In Windows, run the following redirection command in the CLI:

   .. code-block::

      obsutil ls obs://bucketName  -limit=0 > D:/result.txt

-  In Linux or macOS, run the following command:

   .. code-block::

      ./obsutil ls obs://bucketName  -limit=0 > /root/result.txt

   .. note::

      In Windows, you need to perform the redirection operation in the CLI to redirect the output to a local file. Do not run the redirection command in the obsutil executable file because obsutil does not support redirection.
