:original_name: rms_02_0008.html

.. _rms_02_0008:

Querying Resources of a Specific Type
=====================================

Function
--------

This API is to query all your resources of a specific type and you must have the rms:resources:list permission. For example, to query ECSs whose resource type in RMS is ecs.cloudsrevers, you must set **provider** to **ecs** and **type** to **cloudservers** in the request.

URI
---

GET /v1/resource-manager/domains/{domain_id}/provider/{provider}/type/{type}/resources

.. table:: **Table 1** Path parameters

   +-----------------+-----------------+-----------------+-----------------------------------+
   | Parameter       | Mandatory       | Type            | Description                       |
   +=================+=================+=================+===================================+
   | domain_id       | Yes             | String          | Specifies the account ID.         |
   |                 |                 |                 |                                   |
   |                 |                 |                 | Maximum length: **36**            |
   +-----------------+-----------------+-----------------+-----------------------------------+
   | provider        | Yes             | String          | Specifies the cloud service name. |
   |                 |                 |                 |                                   |
   |                 |                 |                 | Maximum length: **20**            |
   +-----------------+-----------------+-----------------+-----------------------------------+
   | type            | Yes             | String          | Specifies the resource type.      |
   |                 |                 |                 |                                   |
   |                 |                 |                 | Maximum length: **20**            |
   +-----------------+-----------------+-----------------+-----------------------------------+

.. table:: **Table 2** Query parameters

   +-----------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                                                                                                                 |
   +=================+=================+=================+=============================================================================================================================================================================+
   | region_id       | No              | String          | Specifies the region ID.                                                                                                                                                    |
   |                 |                 |                 |                                                                                                                                                                             |
   |                 |                 |                 | Maximum length: **36**                                                                                                                                                      |
   +-----------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | ep_id           | No              | String          | Specifies the enterprise project ID.                                                                                                                                        |
   |                 |                 |                 |                                                                                                                                                                             |
   |                 |                 |                 | Maximum length: **36**                                                                                                                                                      |
   +-----------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | tag             | No              | Object          | Specifies the resource tag.                                                                                                                                                 |
   +-----------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | limit           | No              | Number          | Specifies the maximum number of records to return.                                                                                                                          |
   |                 |                 |                 |                                                                                                                                                                             |
   |                 |                 |                 | Minimum value: **1**                                                                                                                                                        |
   |                 |                 |                 |                                                                                                                                                                             |
   |                 |                 |                 | Maximum value: **200**                                                                                                                                                      |
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

   +-----------+------------------------------------------------------------------+----------------------------------+
   | Parameter | Type                                                             | Description                      |
   +===========+==================================================================+==================================+
   | resources | Array of :ref:`Resource Entity <rms_02_0008____d0e2713>` objects | Specifies the resource list.     |
   +-----------+------------------------------------------------------------------+----------------------------------+
   | page_info | :ref:`Page Info <rms_02_0008____d0e2882>` object                 | Specifies the pagination object. |
   +-----------+------------------------------------------------------------------+----------------------------------+

.. _rms_02_0008____d0e2713:

.. table:: **Table 4** Resource Entity

   +--------------------+--------+---------------------------------------------------------------------------------------------+
   | Parameter          | Type   | Description                                                                                 |
   +====================+========+=============================================================================================+
   | id                 | String | Specifies the resource ID.                                                                  |
   +--------------------+--------+---------------------------------------------------------------------------------------------+
   | name               | String | Specifies the resource name.                                                                |
   +--------------------+--------+---------------------------------------------------------------------------------------------+
   | provider           | String | Specifies the cloud service name. For details, see :ref:`Supported Resource <rms_02_0019>`. |
   +--------------------+--------+---------------------------------------------------------------------------------------------+
   | type               | String | Specifies the resource type.                                                                |
   +--------------------+--------+---------------------------------------------------------------------------------------------+
   | region_id          | String | Specifies the region ID.                                                                    |
   +--------------------+--------+---------------------------------------------------------------------------------------------+
   | project_id         | String | Specifies the project ID in OpenStack.                                                      |
   +--------------------+--------+---------------------------------------------------------------------------------------------+
   | project_name       | String | Specifies the project name in OpenStack.                                                    |
   +--------------------+--------+---------------------------------------------------------------------------------------------+
   | ep_id              | String | Specifies the enterprise project ID.                                                        |
   +--------------------+--------+---------------------------------------------------------------------------------------------+
   | ep_name            | String | Specifies the enterprise project name.                                                      |
   +--------------------+--------+---------------------------------------------------------------------------------------------+
   | checksum           | String | Specifies the resource checksum.                                                            |
   +--------------------+--------+---------------------------------------------------------------------------------------------+
   | created            | String | Specifies the time when the resource was created.                                           |
   +--------------------+--------+---------------------------------------------------------------------------------------------+
   | updated            | String | Specifies the time when the resource was updated.                                           |
   +--------------------+--------+---------------------------------------------------------------------------------------------+
   | provisioning_state | String | Specifies the status of the operation that causes the resource change.                      |
   +--------------------+--------+---------------------------------------------------------------------------------------------+
   | tags               | Object | Specifies the resource tags.                                                                |
   +--------------------+--------+---------------------------------------------------------------------------------------------+
   | properties         | Object | Specifies the detailed properties of the resource.                                          |
   +--------------------+--------+---------------------------------------------------------------------------------------------+

.. _rms_02_0008____d0e2882:

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

**Status code: 500**

.. table:: **Table 8** Response body parameters

   ========== ====== ============================
   Parameter  Type   Description
   ========== ====== ============================
   error_code String Specifies the error code.
   error_msg  String Specifies the error message.
   ========== ====== ============================

Example Request
---------------

-  Querying all VMs under your account.

   .. code-block:: text

      GET https://{endpoint}/v1/resource-manager/domains/{domain_id}/provider/ecs/type/cloudservers/resources

-  Querying your VMs in the eu-de-04 region and setting to return the first 100 records.

   .. code-block:: text

      GET https://{endpoint}/v1/resource-manager/domains/{domain_id}/provider/ecs/type/cloudservers/resources?limit=100&region_id=eu-de

Example Response
----------------

**Status code: 200**

Operation succeeded.

-  Example 1

   .. code-block::

      {
        "current_count" : 2,
        "next_marker" : null
       }

-  Example 2

   .. code-block::

      [ {
        "checksum" : "89ca775e88e04b2c200ccbf9e219ad0d7da42e3f446e5c953d443288134eec41",
        "created" : "2020-02-21T08:41:05Z",
        "ep_id" : "0",
        "ep_name" : "default",
        "id" : "7ffd8564-d88a-4bc9-ab51-d8b79a57d0e6",
        "name" : "vpc-489c",
        "project_id" : "059b5e0a2500d5552fa1c00adada8c06",
        "project_name" : "eu-de-07",
        "properties" : {
          "cidr" : "192.168.0.0/16",
          "status" : "OK"
        },
        "provider" : "vpc",
        "provisioning_state" : "Succeeded",
        "region_id" : "eu-de-07",
        "tags" : {
          "use" : "test"
        },
        "type" : "vpcs",
        "updated" : "2020-02-21T08:41:05Z"
       }, {
        "checksum" : "db2aad42804951c03a724b7501da9b6b4c14d319dd319d76bb7c658f256a37b0",
        "created" : "2020-02-24T08:43:05Z",
        "ep_id" : "0",
        "ep_name" : "default",
        "id" : "b63b33b7-f48c-4048-995b-0445d124a445",
        "name" : "VPC_TEST3_20200224163856",
        "project_id" : "059b5e0a2500d5552fa1c00adada8c06",
        "project_name" : "eu-de-07",
        "properties" : {
          "cidr" : "192.168.0.0/16",
          "status" : "OK"
        },
        "provider" : "vpc",
        "provisioning_state" : "Succeeded",
        "region_id" : "eu-de-07",
        "tags" : {
          "use" : "test1"
        },
        "type" : "vpcs",
        "updated" : "2020-08-11T11:55:08Z"
       } ]

Status Codes
------------

=========== ======================
Status Code Description
=========== ======================
200         Operation succeeded.
400         Invalid parameter.
403         Authentication failed.
500         Internal server error.
=========== ======================

Error Codes
-----------

See :ref:`Error Codes <rms_02_0018>`.
