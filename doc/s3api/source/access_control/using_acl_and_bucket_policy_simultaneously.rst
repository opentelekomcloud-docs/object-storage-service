:original_name: en-us_topic_0125560247.html

.. _en-us_topic_0125560247:

Using ACL and Bucket Policy Simultaneously
==========================================

If an ACL, roles, and a bucket policy are used at the same time and their authorization conflicts, the authorization priorities come as the bucket policy, roles, and the ACL.

If a bucket policy and an IAM policy are applied to an account together, an explicit deny overrides allows, and an allow overrides default denies.

Cross-tenant authorized access cannot be implemented for SSE-KMS-encrypted objects using the bucket ACL or policy.
