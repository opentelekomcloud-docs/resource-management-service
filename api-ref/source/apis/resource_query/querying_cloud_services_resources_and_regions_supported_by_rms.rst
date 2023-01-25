:original_name: rms_02_0009.html

.. _rms_02_0009:

Querying Cloud Services, Resources, and Regions Supported by RMS
================================================================

Function
--------

This API is used to query cloud services, resources, and regions supported by RMS.

URI
---

GET /v1/resource-manager/domains/{domain_id}/providers

.. table:: **Table 1** Path parameter

   +-----------------+-----------------+-----------------+---------------------------+
   | Parameter       | Mandatory       | Type            | Description               |
   +=================+=================+=================+===========================+
   | domain_id       | Yes             | String          | Specifies the account ID. |
   |                 |                 |                 |                           |
   |                 |                 |                 | Maximum length: **36**    |
   +-----------------+-----------------+-----------------+---------------------------+

.. table:: **Table 2** Query parameters

   +-----------------+-----------------+-----------------+----------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                        |
   +=================+=================+=================+====================================================+
   | offset          | No              | Number          | Specifies the pagination offset.                   |
   |                 |                 |                 |                                                    |
   |                 |                 |                 | Minimum value: **1**                               |
   |                 |                 |                 |                                                    |
   |                 |                 |                 | Maximum value: **1000**                            |
   +-----------------+-----------------+-----------------+----------------------------------------------------+
   | limit           | No              | Number          | Specifies the maximum number of records to return. |
   |                 |                 |                 |                                                    |
   |                 |                 |                 | Minimum value: **1**                               |
   |                 |                 |                 |                                                    |
   |                 |                 |                 | Maximum value: **200**                             |
   +-----------------+-----------------+-----------------+----------------------------------------------------+

Request Parameters
------------------

.. table:: **Table 3** Request header parameter

   +-----------------+-----------------+-----------------+------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                          |
   +=================+=================+=================+======================================================+
   | X-Language      | No              | String          | Specifies the language of the information to return. |
   |                 |                 |                 |                                                      |
   |                 |                 |                 | Default value: **en-us**                             |
   |                 |                 |                 |                                                      |
   |                 |                 |                 | Possible values are as follows:                      |
   |                 |                 |                 |                                                      |
   |                 |                 |                 | -  **zh-cn**                                         |
   |                 |                 |                 | -  **en-us**                                         |
   +-----------------+-----------------+-----------------+------------------------------------------------------+

Response Parameters
-------------------

**Status code: 200**

.. table:: **Table 4** Response body parameters

   +--------------------+-------------------------------------------------------------------------------------------------------+----------------------------------------------------------------+
   | Parameter          | Type                                                                                                  | Description                                                    |
   +====================+=======================================================================================================+================================================================+
   | resource_providers | Array of :ref:`Resource Provider Response <rms_02_0009____response_resourceproviderresponse>` objects | Specifies the list of cloud service details.                   |
   +--------------------+-------------------------------------------------------------------------------------------------------+----------------------------------------------------------------+
   | total_count        | Number                                                                                                | Specifies the total number of cloud services supported by RMS. |
   +--------------------+-------------------------------------------------------------------------------------------------------+----------------------------------------------------------------+

.. _rms_02_0009____response_resourceproviderresponse:

.. table:: **Table 5** Resource Provider Response

   +-----------------------+-----------------------------------------------------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter             | Type                                                                                          | Description                                                                                                                             |
   +=======================+===============================================================================================+=========================================================================================================================================+
   | provider              | String                                                                                        | Specifies the cloud service name. For details, see :ref:`Supported Resource <rms_02_0019>`.                                             |
   +-----------------------+-----------------------------------------------------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------+
   | display_name          | String                                                                                        | Specifies the display name of the cloud service. You can set the language by configuring **X-Language** in the request header.          |
   +-----------------------+-----------------------------------------------------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------+
   | category_display_name | String                                                                                        | Specifies the display name of the cloud service category. You can set the language by configuring **X-Language** in the request header. |
   |                       |                                                                                               |                                                                                                                                         |
   |                       |                                                                                               | Currently supported categories: Computing, Network, Storage, Database, Security, EI Enterprise.                                         |
   +-----------------------+-----------------------------------------------------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------+
   | resource_types        | Array of :ref:`Resource Type Response <rms_02_0009____response_resourcetyperesponse>` objects | Specifies the resource type list.                                                                                                       |
   +-----------------------+-----------------------------------------------------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------+

.. _rms_02_0009____response_resourcetyperesponse:

.. table:: **Table 6** Resource Type Response

   +---------------------+---------+--------------------------------------------------------------------------------------------------------------------------------+
   | Parameter           | Type    | Description                                                                                                                    |
   +=====================+=========+================================================================================================================================+
   | name                | String  | Specifies the resource type.                                                                                                   |
   +---------------------+---------+--------------------------------------------------------------------------------------------------------------------------------+
   | display_name        | String  | Specifies the display name of the resource type. You can set the language by configuring **X-Language** in the request header. |
   +---------------------+---------+--------------------------------------------------------------------------------------------------------------------------------+
   | global              | Boolean | Specifies whether the resource is a global resource.                                                                           |
   +---------------------+---------+--------------------------------------------------------------------------------------------------------------------------------+
   | regions             | Array   | Specifies the list of supported regions. Array of Strings.                                                                     |
   +---------------------+---------+--------------------------------------------------------------------------------------------------------------------------------+
   | console_endpoint_id | String  | Specifies the endpoint ID of the console.                                                                                      |
   +---------------------+---------+--------------------------------------------------------------------------------------------------------------------------------+
   | console_list_url    | String  | Specifies the URL of the resource list page.                                                                                   |
   +---------------------+---------+--------------------------------------------------------------------------------------------------------------------------------+
   | console_detail_url  | String  | Specifies the URL of the resource details page.                                                                                |
   +---------------------+---------+--------------------------------------------------------------------------------------------------------------------------------+

**Status code: 500**

.. table:: **Table 7** Response body parameters

   ========== ====== ============================
   Parameter  Type   Description
   ========== ====== ============================
   error_code String Specifies the error code.
   error_msg  String Specifies the error message.
   ========== ====== ============================

Example Request
---------------

None

Example Response
----------------

**Status code: 200**

Operation succeeded.

.. code-block::

   "total_count": 2
   "resource_providers": [ {
     "provider" : "ecs",
       "display_name": "ECS",
       "category_display_name": "Computing",
     "resource_types" : [ {
       "name" : "cloudservers",
        "display_name": "ECS",
       "global" : false,
       "regions" : [ "eu-de" ],
       "console_endpoint_id" : "ecm",
       "console_list_url" : "#/ecs/manager/vmList",
       "console_detail_url" : "#/ecs/manager/ecsDetail?instanceId={id}"
     } ]
   }, {
     "provider" : "vpc",
       "display_name": "VPC",
       "category_display_name": "Network",
     "resource_types" : [ {
       "name" : "vpcs",
         "display_name": "VPC",
       "global" : false,
       "regions" : [ "eu-de-01", "eu-de-04", "eu-de-03", "eu-de-02", "eu-de-01", "eu-de-02", "eu-de-01", "eu-de-02", "eu-de-03", "eu-de-01", "eu-de-02" ],
       "console_endpoint_id" : "vpc",
       "console_list_url" : "#/vpcs",
       "console_detail_url" : "#/vpc/vpcmanager/vpcDetail/subnets?vpcId={id}"
     }, {
       "name" : "bandwidths",
         "display_name": "Shared bandwidth",
       "global" : false,
       "regions" : [ "eu-de-01", "eu-de-04", "eu-de-03", "eu-de-02", "eu-de-01", "eu-de-02", "eu-de-01", "eu-de-02", "eu-de-03", "eu-de-01", "eu-de-02" ],
       "console_endpoint_id" : "vpc",
       "console_list_url" : "#/vpc/vpcmanager/shareBandwidth",
       "console_detail_url" : "#/vpc/vpcmanager/shareBandwidth?bandwidthId={id}"
     }, {
       "name" : "securityGroups",
        "display_name": "Security group",
       "global" : false,
       "regions" : [ "eu-de-01", "eu-de-04", "eu-de-03", "eu-de-02", "eu-de-01", "eu-de-02", "eu-de-01", "eu-de-02", "eu-de-03", "eu-de-01", "eu-de-02" ],
       "console_endpoint_id" : "vpc",
       "console_list_url" : "#/secGroups",
       "console_detail_url" : "#/vpc/vpcmanager/sgDetail/sgRules?instanceId={id}"
     }, {
       "name" : "publicips",
         "display_name": "EIP",
       "global" : false,
       "regions" : [ "eu-de-01", "eu-de-04", "eu-de-03", "eu-de-02", "eu-de-01", "eu-de-02", "eu-de-01", "eu-de-02", "eu-de-03", "eu-de-01", "eu-de-02" ],
       "console_endpoint_id" : "vpc",
       "console_list_url" : "#/vpc/vpcmanager/eips",
       "console_detail_url" : "#/vpc/vpcmanager/eipDetailNew?eipId={id}"
     } ]
   } ]

Status Codes
------------

=========== ======================
Status Code Description
=========== ======================
200         Operation succeeded.
500         Internal server error.
=========== ======================

Error Codes
-----------

See :ref:`Error Codes <rms_02_0018>`.
