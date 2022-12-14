:original_name: rms_02_0013.html

.. _rms_02_0013:

Querying Resource Relationships
===============================

Function
--------

This API is used to query the relationship between the resource with a specific ID and other resources. You can set **Direction** to **in** or **out**.

URI
---

GET /v1/resource-manager/domains/{domain_id}/resources/{resource_id}/relations

.. table:: **Table 1** Path parameters

   +-----------------+-----------------+-----------------+----------------------------+
   | Parameter       | Mandatory       | Type            | Description                |
   +=================+=================+=================+============================+
   | domain_id       | Yes             | String          | Specifies the account ID.  |
   |                 |                 |                 |                            |
   |                 |                 |                 | Maximum length: **36**     |
   +-----------------+-----------------+-----------------+----------------------------+
   | resource_id     | Yes             | String          | Specifies the resource ID. |
   |                 |                 |                 |                            |
   |                 |                 |                 | Maximum length: **256**    |
   +-----------------+-----------------+-----------------+----------------------------+

.. table:: **Table 2** Query parameters

   +-----------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                                                                                                                 |
   +=================+=================+=================+=============================================================================================================================================================================+
   | direction       | Yes             | String          | Specifies the resource relationship direction.                                                                                                                              |
   |                 |                 |                 |                                                                                                                                                                             |
   |                 |                 |                 | Possible values are as follows:                                                                                                                                             |
   |                 |                 |                 |                                                                                                                                                                             |
   |                 |                 |                 | -  **in**                                                                                                                                                                   |
   |                 |                 |                 | -  **out**                                                                                                                                                                  |
   +-----------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | limit           | No              | Number          | Specifies the maximum number of records to return.                                                                                                                          |
   |                 |                 |                 |                                                                                                                                                                             |
   |                 |                 |                 | Minimum value: **1**                                                                                                                                                        |
   |                 |                 |                 |                                                                                                                                                                             |
   |                 |                 |                 | Maximum value: **1000**                                                                                                                                                     |
   +-----------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | marker          | No              | String          | Specifies the pagination parameter. You can use the **marker** value returned in the previous request as the number of the first page of records to return in this request. |
   |                 |                 |                 |                                                                                                                                                                             |
   |                 |                 |                 | Minimum length: **4**                                                                                                                                                       |
   |                 |                 |                 |                                                                                                                                                                             |
   |                 |                 |                 | Maximum length: **400**                                                                                                                                                     |
   +-----------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Request Parameters
------------------

None

Response Parameters
-------------------

**Status code: 200**

.. table:: **Table 3** Response body parameters

   +-----------+--------------------------------------------------------------------+---------------------------------------------------+
   | Parameter | Type                                                               | Description                                       |
   +===========+====================================================================+===================================================+
   | relations | Array of :ref:`Resource Relation <rms_02_0013____d0e6777>` objects | Specifies the list of the resource relationships. |
   +-----------+--------------------------------------------------------------------+---------------------------------------------------+
   | page_info | :ref:`Page Info <rms_02_0013____d0e6846>` object                   | Specifies the pagination object.                  |
   +-----------+--------------------------------------------------------------------+---------------------------------------------------+

.. _rms_02_0013____d0e6777:

.. table:: **Table 4** Resource Relation

   ================== ====== ==============================================
   Parameter          Type   Description
   ================== ====== ==============================================
   relation_type      String Specifies the relationship type.
   from_resource_type String Specifies the type of the source resource.
   to_resource_type   String Specifies the type of the associated resource.
   from_resource_id   String Specifies the source resource ID.
   to_resource_id     String Specifies the ID of the associated resource.
   ================== ====== ==============================================

.. _rms_02_0013____d0e6846:

.. table:: **Table 5** Page Info

   +-----------------------+-----------------------+------------------------------------------------------+
   | Parameter             | Type                  | Description                                          |
   +=======================+=======================+======================================================+
   | current_count         | Number                | Specifies the resource quantity on the current page. |
   |                       |                       |                                                      |
   |                       |                       | Minimum value: **0**                                 |
   |                       |                       |                                                      |
   |                       |                       | Maximum value: **200**                               |
   +-----------------------+-----------------------+------------------------------------------------------+
   | next_marker           | String                | Specifies the **marker** value of the next page.     |
   |                       |                       |                                                      |
   |                       |                       | Minimum length: **4**                                |
   |                       |                       |                                                      |
   |                       |                       | Maximum length: **400**                              |
   +-----------------------+-----------------------+------------------------------------------------------+

**Status code: 400**

.. table:: **Table 6** Response body parameters

   ========== ====== ============================
   Parameter  Type   Description
   ========== ====== ============================
   error_code String Specifies the error code.
   error_msg  String Specifies the error message.
   ========== ====== ============================

**Status code: 403**

.. table:: **Table 7** Response body parameters

   ========== ====== ============================
   Parameter  Type   Description
   ========== ====== ============================
   error_code String Specifies the error code.
   error_msg  String Specifies the error message.
   ========== ====== ============================

**Status code: 404**

.. table:: **Table 8** Response body parameters

   ========== ====== ============================
   Parameter  Type   Description
   ========== ====== ============================
   error_code String Specifies the error code.
   error_msg  String Specifies the error message.
   ========== ====== ============================

**Status code: 500**

.. table:: **Table 9** Response body parameters

   ========== ====== ============================
   Parameter  Type   Description
   ========== ====== ============================
   error_code String Specifies the error code.
   error_msg  String Specifies the error message.
   ========== ====== ============================

Example Request
---------------

.. code-block:: text

   GET https://{endpoint}/v1/resource-manager/domains/{domain_id}/resources/{resource_id}/relations?direction=out&limit=1000

Example Response
----------------

**Status code: 200**

Operation succeeded.

-  Example 1

   .. code-block::

      [ {
        "relation_type" : "isAttachedTo",
        "from_resource_type" : "ecs.cloudservers",
        "to_resource_type" : "evs.volumes",
        "from_resource_id" : "6af96128-d58d-426c-91e0-b38144c0f112",
        "to_resource_id" : "0075ed19-59dd-49be-961d-117bb6fbfd3e"
      }, {
        "relation_type" : "contains",
        "from_resource_type" : "ecs.cloudservers",
        "to_resource_type" : "vpc.publicips",
        "from_resource_id" : "6af96128-d58d-426c-91e0-b38144c0f112",
        "to_resource_id" : "3813d6d3-ef88-47b1-b343-cdf6390c6dcb"
      }, {
        "relation_type" : "isAssociatedWith",
        "from_resource_type" : "ecs.cloudservers",
        "to_resource_type" : "vpc.securityGroups",
        "from_resource_id" : "6af96128-d58d-426c-91e0-b38144c0f112",
        "to_resource_id" : "8cca3002-00af-4812-a853-b7a6fbee06a4"
      }, {
        "relation_type" : "isAttachedTo",
        "from_resource_type" : "ecs.cloudservers",
        "to_resource_type" : "evs.volumes",
        "from_resource_id" : "6af96128-d58d-426c-91e0-b38144c0f112",
        "to_resource_id" : "f4a107eb-4c6d-4dc8-88d8-de337923956f"
      }, {
        "relation_type" : "isContainedIn",
        "from_resource_type" : "ecs.cloudservers",
        "to_resource_type" : "vpc.vpcs",
        "from_resource_id" : "6af96128-d58d-426c-91e0-b38144c0f112",
        "to_resource_id" : "ff13d70d-17e5-4ec8-945a-c874e0db99d3"
      } ]

-  Example 2

   .. code-block::

      {
        "current_count" : 5,
        "next_marker" : null
      }

Status Codes
------------

=========== ======================
Status Code Description
=========== ======================
200         Operation succeeded.
400         Invalid parameter.
403         Authentication failed.
404         Resource not found.
500         Internal server error.
=========== ======================

Error Codes
-----------

See :ref:`Error Codes <rms_02_0018>`.
