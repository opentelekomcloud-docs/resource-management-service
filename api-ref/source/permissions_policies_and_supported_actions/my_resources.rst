:original_name: rms_02_0016.html

.. _rms_02_0016:

My Resources
============

+---------------------------------------+------------------------------------------------------------------------------------------------------+--------------------+-------------+--------------------+
| Permission                            | API                                                                                                  | Action             | IAM Project | Enterprise Project |
+=======================================+======================================================================================================+====================+=============+====================+
| Querying resources of a specific type | GET /v1/resource-manager/domains/{domain_id}/provider/{provider}/type/{type}/resources               | rms:resources:list | Y           | N/A                |
+---------------------------------------+------------------------------------------------------------------------------------------------------+--------------------+-------------+--------------------+
| Querying a resource                   | GET /v1/resource-manager/domains/{domain_id}/provider/{provider}/type/{type}/resources/{resource_id} | rms:resources:get  | Y           | N/A                |
+---------------------------------------+------------------------------------------------------------------------------------------------------+--------------------+-------------+--------------------+
