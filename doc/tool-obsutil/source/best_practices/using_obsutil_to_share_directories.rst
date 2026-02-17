:original_name: obs_11_0069.html

.. _obs_11_0069:

Using obsutil to Share Directories
==================================

The directory sharing function allows the owner of a bucket to share directories in a bucket or the entire bucket with other users by using the authorization code and access code. If you have the valid authorization code and access code of a shared folder, you can use OBS tools (OBS Browser and obsutil) to access the folder, list objects, and download objects. Alternatively, you can directly enter the authorization code in the address box of a web browser to list and download objects.

obsutil provides three commands to implement directory sharing. The procedure is as follows:

#. Run the **obsutil create-share** command to create an authorization code for sharing a directory. For example, you can run the following command to share the **test** directory in the bucket named **bucket** with the access code set to **123456** and the validity period set to **10** days:

   .. code-block::

      obsutil create-share obs://bucket/test/ -ac=123456 -vp=10d

   .. note::

      -  When creating an authorization code, you are advised to end the name of the directory to be shared always with a slash (/). If no directory name is specified in the command (for example, only **obs://bucket** is specified in the command), the entire bucket is shared.
      -  If you do not use the **ac** option to set the access code, obsutil will prompt you to enter the access code. The access code must be a six-digit string.
      -  For details about this command, see :ref:`Creating an Authorization Code for Directory Sharing <obs_11_0062>`.

#. Run the **obsutil share-ls** command to list objects in the bucket. For example, to list the first 100 objects in the **test** directory in the bucket using the authorization code, run the following command:

   .. code-block::

      obsutil share-ls file://d:/authorizationCode.txt -ac=123456 -prefix=test/ -limit=100

   .. note::

      -  If the value of **prefix** is not specified, all objects in the authorized path are listed by default. If you do not want to list all objects, set **prefix** to a subset of the authorized path in the authorization code.
      -  For details about this command, see :ref:`Listing Objects by Using an Authorization Code <obs_11_0063>`.

#. Run the **obsutil share-cp** command to download objects from the bucket. For example, if you want to download all objects in the **sub** subdirectory of the **test** directory, run the following command:

   .. code-block::

      obsutil share-cp file://d:/authorizationCode.txt ./ -ac=123456 -key=test/sub/ -r -f

   .. note::

      For details about this command, see :ref:`Downloading Objects by Using an Authorization Code <obs_11_0064>`.

.. note::

   -  You can also create an authorization code on OBS Console or OBS Browser, and then use obsutil to list and download objects.
   -  You can use obsutil to create an authorization code and enter the authorization code in the address box of a web browser to list and download objects, or use the authorization code to log in to OBS Browser to list and download objects.
