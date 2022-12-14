:original_name: rms_02_0010.html

.. _rms_02_0010:

Querying a Resource
===================

Function
--------

This API is used to query details of a resource based on its ID. You must have the rms:resources:get permission. For example, to query ECSs whose resource type in RMS is ecs.cloudsrevers, you must set **provider** to **ecs** and **type** to **cloudservers** in the request.

URI
---

GET /v1/resource-manager/domains/{domain_id}/provider/{provider}/type/{type}/resources/{resource_id}

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
   | resource_id     | Yes             | String          | Specifies the resource ID.        |
   |                 |                 |                 |                                   |
   |                 |                 |                 | Maximum length: **256**           |
   +-----------------+-----------------+-----------------+-----------------------------------+

Request Parameters
------------------

None

Response Parameters
-------------------

**Status code: 200**

.. table:: **Table 2** Response body parameters

   +--------------------+--------+------------------------------------------------------------------------+
   | Parameter          | Type   | Description                                                            |
   +====================+========+========================================================================+
   | id                 | String | Specifies the resource ID.                                             |
   +--------------------+--------+------------------------------------------------------------------------+
   | name               | String | Specifies the resource name.                                           |
   +--------------------+--------+------------------------------------------------------------------------+
   | provider           | String | Specifies the cloud service name.                                      |
   +--------------------+--------+------------------------------------------------------------------------+
   | type               | String | Specifies the resource type.                                           |
   +--------------------+--------+------------------------------------------------------------------------+
   | region_id          | String | Specifies the region ID.                                               |
   +--------------------+--------+------------------------------------------------------------------------+
   | project_id         | String | Specifies the project ID in OpenStack.                                 |
   +--------------------+--------+------------------------------------------------------------------------+
   | project_name       | String | Specifies the project name in OpenStack.                               |
   +--------------------+--------+------------------------------------------------------------------------+
   | ep_id              | String | Specifies the enterprise project ID.                                   |
   +--------------------+--------+------------------------------------------------------------------------+
   | ep_name            | String | Specifies the enterprise project name.                                 |
   +--------------------+--------+------------------------------------------------------------------------+
   | checksum           | String | Specifies the resource checksum.                                       |
   +--------------------+--------+------------------------------------------------------------------------+
   | created            | String | Specifies the time when the resource was created.                      |
   +--------------------+--------+------------------------------------------------------------------------+
   | updated            | String | Specifies the time when the resource was updated.                      |
   +--------------------+--------+------------------------------------------------------------------------+
   | provisioning_state | String | Specifies the status of the operation that causes the resource change. |
   +--------------------+--------+------------------------------------------------------------------------+
   | tags               | Object | Specifies the resource tag.                                            |
   +--------------------+--------+------------------------------------------------------------------------+
   | properties         | Object | Specifies the detailed properties of the resource.                     |
   +--------------------+--------+------------------------------------------------------------------------+

**Status code: 400**

.. table:: **Table 3** Response body parameters

   ========== ====== ============================
   Parameter  Type   Description
   ========== ====== ============================
   error_code String Specifies the error code.
   error_msg  String Specifies the error message.
   ========== ====== ============================

**Status code: 403**

.. table:: **Table 4** Response body parameters

   ========== ====== ============================
   Parameter  Type   Description
   ========== ====== ============================
   error_code String Specifies the error code.
   error_msg  String Specifies the error message.
   ========== ====== ============================

**Status code: 404**

.. table:: **Table 5** Response body parameters

   ========== ====== ============================
   Parameter  Type   Description
   ========== ====== ============================
   error_code String Specifies the error code.
   error_msg  String Specifies the error message.
   ========== ====== ============================

**Status code: 500**

.. table:: **Table 6** Response body parameters

   ========== ====== ============================
   Parameter  Type   Description
   ========== ====== ============================
   error_code String Specifies the error code.
   error_msg  String Specifies the error message.
   ========== ====== ============================

Example Request
---------------

.. code-block:: text

   GET https://{endpoint}/v1/resource-manager/domains/059b5c937100d3e40ff0c00a7675a0a0/provider/ecs/type/cloudservers/resources/00337e93-82d1-40ca-911f-07cff94587cc

Example Response
----------------

**Status code: 200**

Operation succeeded.

.. code-block::

   {
     "id": "00337e93-82d1-40ca-911f-07cff94587cc"
     "name": "dev_machine"
     "provider":"ecs"
     "type": "cloudservers"
     "region_id": "eu-de-01"
     "project_id": "39c2af998c334ed6bcbb75b27318f7cc"
     "project_nmae": "eu-de-01"
     "ep_id": "0"
     "ep_name": "default"
     "checksum":"3a0075409edb156a74e041b7479f0d5993be1d62b4ccd2af3a1dd01ec80c8b39"
     "created": "2019-11-20T06:24:43Z"
     "updated": "2020-07-17T08:30:52Z"
     "provisioning_state": "Succeeded"
     "tags": {
       "usage": "Display"
     }
     "properties": {
      "accessIpv4" : "",
      "hostName" : "dev-machine",
      "addresss" : [ {
        "OsExtIpsType" : "fixed",
        "OsExtIpsPortId" : "f2fa750a-e2ab-434f-b14a-bfe7c8cea0cc",
        "addr" : "192.168.1.212",
        "version" : 4,
        "OsExtIpsMacAddr" : "fa:16:3e:6e:cf:33"
      }, {
        "OsExtIpsType" : "floating",
        "OsExtIpsPortId" : "f2fa750a-e2ab-434f-b14a-bfe7c8cea0cc",
        "addr" : "100.85.225.33",
        "version" : 4,
        "OsExtIpsMacAddr" : "fa:16:3e:6e:cf:33"
      } ],
      "accessIpv6" : "",
      "metadata" : {
        "chargingMode" : "0",
        "meteringImageType" : "private",
        "imageName" : "resource-manager-devmachine-template",
        "meteringImageId" : "9bcaace4-b8da-4008-a352-3f72e1f25333",
        "meteringResourcesPerCode" : "si2.large.2.linux",
        "vpcId" : "cf403ef5-90df-4e7e-829d-5d21b1cb7d1e",
        "osBit" : "64"
      },
      "OsExtStsVmState" : "active",
      "configDrive" : "",
      "OsExtStsPowerState" : 1,
      "hostId" : "3c381dcfc3e628c1a504ad94ba8c4e89081306455273701333f32921",
      "securityGroup" : [ {
        "name" : "default",
        "id" : "5d55b397-ad9c-462d-af72-6599cb941c49"
      } ],
      "ExtVolumesAttached" : [ {
        "bootIndex" : "0",
        "id" : "010d940e-a73e-417b-85ae-51b76c0d2ba0",
        "device" : "/dev/vda"
      } ],
      "userId" : "e311190745e94cc09d62d5779e55912d",
      "flavor" : {
        "disk" : "0",
        "name" : "Si2.large.2",
        "id" : "Si2.large.2",
        "vcpus" : "2",
        "ram" : "4096"
      },
      "OsDcfDiskConfig" : "MANUAL",
      "hostStatus" : "UP",
      "OsSrvUsgLaunchedAt" : "2019-11-20T06:24:56.000000",
      "OsExtAz" : "eu-de-01a",
      "progress" : 0,
      "locked" : false,
      "OS-EXT-SRV-ATTR" : {
        "hostName" : "dev-machine",
        "kernelId" : "",
        "ramdiskId" : "",
        "reservationId" : "r-hhux9o7m",
        "instanceName" : "instance-0009cb50",
        "host" : "eu-de-01a-pod01.eu-de-01",
        "rootDeviceName" : "/dev/vda",
        "hypervisorHostName" : "nova001@2",
        "launchIndex" : 0
      },
      "status" : "ACTIVE"
    }
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
