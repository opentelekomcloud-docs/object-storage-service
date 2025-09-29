:original_name: obs_40_0010.html

.. _obs_40_0010:

Accessing OBS Using an IAM Agency
=================================

The IAM agency is a function of Identity and Access Management (IAM). In scenarios such as CDN private bucket retrieval and cross-region replication, IAM agencies are required to grant other accounts or cloud services the permissions to access and to securely and efficiently manage OBS resources.

For example, when creating a cross-region replication rule, if you want to synchronously replicate encrypted objects, you need to select or create an agency to authorize OBS to access Key Management Service (KMS).

For details about IAM agencies, see `Identity and Access Management User Guide <https://docs.otc.t-systems.com/en-us/usermanual/iam/iam_01_0026.html>`__.
