:original_name: rms_02_0011.html

.. _rms_02_0011:

Querying All Resources Under Your Account
=========================================

Function
--------

This API is to query all resources under your account and you must have the rms:resources:list permission.

URI
---

GET /v1/resource-manager/domains/{domain_id}/all-resources

.. table:: **Table 1** Path parameter

   +-----------------+-----------------+-----------------+---------------------------+
   | Parameter       | Mandatory       | Type            | Description               |
   +=================+=================+=================+===========================+
   | domain_id       | Yes             | String          | Specifies the account ID. |
   |                 |                 |                 |                           |
   |                 |                 |                 | Maximum length: **36**    |
   +-----------------+-----------------+-----------------+---------------------------+

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
   | type            | No              | String          | Specifies the resource type (**provider.type**)                                                                                                                             |
   |                 |                 |                 |                                                                                                                                                                             |
   |                 |                 |                 | Maximum length: **40**                                                                                                                                                      |
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

   +-----------+-------------------------------------------------------------------+----------------------------------+
   | Parameter | Type                                                              | Description                      |
   +===========+===================================================================+==================================+
   | resources | Array of :ref:`Resources Entity <rms_02_0011____d0e4538>` objects | Specifies the resource list.     |
   +-----------+-------------------------------------------------------------------+----------------------------------+
   | page_info | :ref:`Page Info <rms_02_0011____d0e4707>` object                  | Specifies the pagination object. |
   +-----------+-------------------------------------------------------------------+----------------------------------+

.. _rms_02_0011____d0e4538:

.. table:: **Table 4** Resources Entity

   +--------------------+--------+-----------------------------------------------------------------------------------------------------------------+
   | Parameter          | Type   | Description                                                                                                     |
   +====================+========+=================================================================================================================+
   | id                 | String | Specifies the resource ID.                                                                                      |
   +--------------------+--------+-----------------------------------------------------------------------------------------------------------------+
   | name               | String | Specifies the resource name.                                                                                    |
   +--------------------+--------+-----------------------------------------------------------------------------------------------------------------+
   | provider           | String | Specifies the cloud service name.                                                                               |
   +--------------------+--------+-----------------------------------------------------------------------------------------------------------------+
   | type               | String | Specifies the resource type.                                                                                    |
   +--------------------+--------+-----------------------------------------------------------------------------------------------------------------+
   | region_id          | String | Specifies the region ID.                                                                                        |
   +--------------------+--------+-----------------------------------------------------------------------------------------------------------------+
   | project_id         | String | Specifies the project ID in OpenStack.                                                                          |
   +--------------------+--------+-----------------------------------------------------------------------------------------------------------------+
   | project_name       | String | Specifies the project name in OpenStack.                                                                        |
   +--------------------+--------+-----------------------------------------------------------------------------------------------------------------+
   | ep_id              | String | Specifies the enterprise project ID.                                                                            |
   +--------------------+--------+-----------------------------------------------------------------------------------------------------------------+
   | ep_name            | String | Specifies the enterprise project name.                                                                          |
   +--------------------+--------+-----------------------------------------------------------------------------------------------------------------+
   | checksum           | String | Specifies the resource checksum.                                                                                |
   +--------------------+--------+-----------------------------------------------------------------------------------------------------------------+
   | created            | String | Specifies the time when the resource was created.                                                               |
   +--------------------+--------+-----------------------------------------------------------------------------------------------------------------+
   | updated            | String | Specifies the time when the resource was updated.                                                               |
   +--------------------+--------+-----------------------------------------------------------------------------------------------------------------+
   | provisioning_state | String | Specifies the status of the operation that causes the resource change.(Succeeded, Processing, Failed, Canceled) |
   +--------------------+--------+-----------------------------------------------------------------------------------------------------------------+
   | tags               | Object | Specifies the resource tag.                                                                                     |
   +--------------------+--------+-----------------------------------------------------------------------------------------------------------------+
   | properties         | Object | Specifies the detailed properties of the resource.                                                              |
   +--------------------+--------+-----------------------------------------------------------------------------------------------------------------+

.. _rms_02_0011____d0e4707:

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

-  Querying all resources under your account.

   .. code-block:: text

      GET https://{endpoint}/v1/resource-manager/domains/{domain_id}/all-resources

-  Querying your resources in the **default** enterprise project and setting to return the first 100 records.

   .. code-block:: text

      GET https://{endpoint}/v1/resource-manager/domains/{domain_id}/all-resources?limit=100&ep_id=0

Example Response
----------------

**Status code: 200**

Operation succeeded.

-  Example 1

   .. code-block::

      [ {
        "id" : "3ccd9191-6a5e-4939-a971-4652db18b370",
        "name" : "elb-265a",
        "provider" : "elb",
        "type" : "loadbalancers",
        "region_id" : "eu-de-04",
        "project_id" : "05498e12458025102ff5c0061a584a9f",
        "project_name" : "eu-de-04_region_service",
        "ep_id" : "0",
        "ep_name" : "default",
        "checksum" : "6e0271b107b764b19acb235f45c0d852f72104fe1d4b32970686e7eae8e87bf4",
        "created" : "2020-02-29T09:39:19Z",
        "updated" : "2020-02-29T09:39:19Z",
        "provisioning_state" : "Succeeded",
        "tags" : { },
        "properties" : {
          "tenant_id" : "05498e12458025102ff5c0061a584a9f",
          "listeners" : [ {
            "id" : "37de3be0-1803-43e2-9bb5-243b4b30b771"
          } ],
          "provisioning_status" : "ACTIVE",
          "description" : "",
          "pools" : [ {
            "id" : "a7ae4e7f-3e97-48ea-bdbc-334684aafac4"
          } ],
          "created_at" : "2020-02-29T09:39:19",
          "vip_subnet_id" : "4f91dfd8-cc4f-4c84-bbfd-8518e6b60cad",
          "tags" : [ ],
          "enterprise_project_id" : "0",
          "vip_address" : "192.168.1.127",
          "updated_at" : "2020-02-29T09:39:19",
          "project_id" : "05498e12458025102ff5c0061a584a9f",
          "provider" : "vlb",
          "operating_status" : "ONLINE",
          "admin_state_up" : true,
          "name" : "elb-265a",
          "id" : "3ccd9191-6a5e-4939-a971-4652db18b370",
          "vip_port_id" : "5968aa0e-df6a-42c8-adc3-af6acd482163"
        }
      }, {
        "id" : "274698f1-6ae5-4572-b026-edd5e3186343",
        "name" : "listener-cfcc",
        "provider" : "elb",
        "type" : "listeners",
        "region_id" : "eu-de-05",
        "project_id" : "39c2af998c334ed6bcbb75b27318f7b5",
        "project_name" : "eu-de-05",
        "ep_id" : "0",
        "ep_name" : "default",
        "checksum" : "2fa729ce34155377fe895ebd70e2523632ca34a7310d8a94e00a74b0d4f8ce76",
        "created" : "2020-06-10T03:38:42Z",
        "updated" : "2020-06-10T03:38:43Z",
        "provisioning_state" : "Succeeded",
        "tags" : { },
        "properties" : {
          "tenant_id" : "39c2af998c334ed6bcbb75b27318f7b5",
          "default_pool_id" : "524996fb-423e-46df-8ba4-cc00fb810cb8",
          "protocol_port" : 80,
          "description" : "",
          "created_at" : "2020-06-10T03:38:42",
          "sni_container_refs" : [ ],
          "connection_limit" : -1,
          "tags" : [ ],
          "protocol" : "TCP",
          "updated_at" : "2020-06-10T03:38:43",
          "project_id" : "39c2af998c334ed6bcbb75b27318f7b5",
          "admin_state_up" : true,
          "name" : "listener-cfcc",
          "insert_headers" : {
            "X-Forwarded-ELB-IP" : false,
            "X-Forwarded-Host" : true
          },
          "loadbalancers" : [ {
            "id" : "eafba5b9-c67f-4f32-a820-4bc48c0474ee"
          } ],
          "http2_enable" : false,
          "id" : "274698f1-6ae5-4572-b026-edd5e3186343"
         }
      }, {
        "id" : "ede7f295-056c-406a-98cf-551d250f8b44",
        "name" : "ecs-for-test",
        "provider" : "ecs",
        "type" : "cloudservers",
        "region_id" : "eu-de-05",
        "project_id" : "39c2af998c334ed6bcbb75b27318f7b5",
        "project_name" : "eu-de-05",
        "ep_id" : "ecf9bb02-bf2b-447c-bafa-bc4b35c31edf",
        "ep_name" : "test",
        "checksum" : "9e7d7a2cf3ff4fafb577fef177db606d41433bf1d9e6246e83ffb4b254ad3fd0",
        "created" : "2020-10-26T03:10Z",
        "updated" : "2020-10-26T03:10:29Z",
        "provisioning_state" : "Succeeded",
        "tags" : { },
        "properties" : {
          "accessIpv4" : "",
          "hostName" : "ecs-for-test",
          "addresses" : [ {
            "OsExtIpsType" : "fixed",
            "OsExtIpsPortId" : "a3dc68fd-bc03-4a48-9fc3-6854a7ada03d",
            "addr" : "192.168.20.27",
            "version" : 4,
            "OsExtIpsMacAddr" : "fa:16:3e:45:2e:44"
          }, {
            "OsExtIpsType" : "floating",
            "OsExtIpsPortId" : "a3dc68fd-bc03-4a48-9fc3-6854a7ada03d",
            "addr" : "4.4.4.4",
            "version" : 4,
            "OsExtIpsMacAddr" : "fa:16:3e:45:2e:44"
          } ],
          "accessIpv6" : "",
          "metadata" : {
            "chargingMode" : "0",
            "meteringImageType" : "shared",
            "imageName" : "test",
            "meteringImageId" : "74e96549-a512-44ea-a074-ff69492be31d",
            "meteringResourcesPerCode" : "si3.small.1.linux",
            "vpcId" : "1dc57489-4ad1-4905-a447-cd42d77b2525",
            "osBit" : "64"
          },
          "OsExtStsVmState" : "active",
          "configDrive" : "",
          "OsExtStsPowerState" : 1,
          "hostId" : "3c381dcfc3e628c1a504ad94ba8c4e89081306455273701333f32921",
          "securityGroup" : [ {
            "name" : "allow_all",
            "id" : "52d72165-0d36-48ed-bc51-647ab361c796"
          } ],
          "ExtVolumesAttached" : [ {
            "bootIndex" : "0",
            "id" : "7642fc7d-9f0e-4cf6-a43a-3c094d7bf596",
            "device" : "/dev/vda"
          } ],
          "userId" : "E2mdWyMJxjRLCkyvTLkRtDMldPnwidNC",
          "flavor" : {
            "disk" : "0",
            "name" : "Si3.small.1",
            "id" : "Si3.small.1",
            "vcpus" : "1",
            "ram" : "1024"
          },
          "OsDcfDiskConfig" : "MANUAL",
          "hostStatus" : "UP",
          "OsSrvUsgLaunchedAt" : "2020-10-26T03:10:14.000000",
          "OsExtAz" : "eu-de-05a",
          "progress" : 0,
          "locked" : false,
          "OS-EXT-SRV-ATTR" : {
            "hostName" : "ecs-for-test",
            "kernelId" : "",
            "ramdiskId" : "",
            "reservationId" : "r-o0t5i6lx",
            "instanceName" : "instance-00117d9e",
            "host" : "eu-de-05a-pod01.eu-de-05",
            "rootDeviceName" : "/dev/vda",
            "hypervisorHostName" : "nova001@7",
            "launchIndex" : 0
          },
          "status" : "ACTIVE",
          "schedulerHints" : { }
        }
      }, {
        "id" : "2954ab42-a61d-4545-8fb7-f3029c827f91",
        "name" : "dcs-test",
        "provider" : "dcs",
        "type" : "redis",
        "region_id" : "eu-de-01",
        "project_id" : "2dd15411042d4dd8a708ef86aafebb0c",
        "project_name" : "eu-de-01",
        "ep_id" : "0",
        "ep_name" : "default",
        "checksum" : "1408722b1da04fb609b377646aeac44d405fdf0aced097f5ec7b4e6c581b933a",
        "created" : "2019-03-09T09:27:38.340Z",
        "updated" : "2020-06-07T04:43:04.185Z",
        "provisioning_state" : "Succeeded",
        "tags" : { },
        "properties" : {
          "spec_code" : "redis.ha.au1.large.1",
          "vpc_name" : "vpc-a59a",
          "charging_mode" : 0,
          "vpc_id" : "723e6d68-7bd0-4945-ac44-d083e10df9c4",
          "user_name" : "test",
          "created_at" : "2019-03-09T09:27:38.340Z",
          "enable_ssl" : false,
          "max_memory" : 1024,
          "capacity" : 1,
          "maintain_begin" : "02:00:00",
          "domain_name" : "redis-2954ab4-dcs-test.dcs.huaweicloud.com",
          "engine" : "Redis",
          "maintain_end" : "06:00:00",
          "service_upgrade" : false,
          "no_password_access" : "false",
          "service_task_id" : "",
          "ip" : "192.168.1.53",
          "used_memory" : 2,
          "enterprise_project_id" : "0",
          "instance_id" : "2954ab42-a61d-4545-8fb7-f3029c827f91",
          "port" : 6379,
          "user_id" : "b32870f8945f443d8aeff4825acf695f",
          "enable_publicip" : false,
          "domainName" : "redis-2954ab4-dcs-test.dcs.huaweicloud.com",
          "name" : "dcs-test",
          "update_at" : "2020-06-07T04:43:04.185Z",
          "resource_spec_code" : "redis.ha.au1.large.1",
          "subnet_id" : "08b835de-6c72-493a-84e4-372f13e6c2d8",
          "engine_version" : "5.0",
          "status" : "RUNNING"
        }
      }, {
        "id" : "a6e56d05501944d3b2507ba506a43744",
        "name" : "console.huaweicloud.com",
        "provider" : "cdn",
        "type" : "domains",
        "region_id" : "global",
        "project_id" : "",
        "project_name" : "",
        "ep_id" : "0",
        "ep_name" : "default",
        "checksum" : "56afa8b76428f90e9abfbe5cbf33535d8816166114d32eeb119658d6c59eceda",
        "created" : "2020-01-04T13:42:37Z",
        "updated" : "2020-01-15T04:23:01Z",
        "provisioning_state" : "Succeeded",
        "tags" : { },
        "properties" : {
         "domain_name" : "console.huaweicloud.com",
          "domain_status" : "offline",
          "business_type" : "WEB",
          "modify_time" : 1579062181463,
          "cname" : "console.huaweicloud.com.c.cdnhwc1.com"
        }
      }, {
        "id" : "1aedefa734514d78baf484358b1066f8in01",
        "name" : "ecf-cm",
        "provider" : "rds",
        "type" : "instances",
        "region_id" : "eu-de-04",
        "project_id" : "9e3425927a954ea5a86d78c3e797acec",
        "project_name" : "eu-de-04_region_service",
        "ep_id" : "0",
        "ep_name" : "default",
        "checksum" : "e18552532a73fdfef172061a398212e8ab72e7901a092b240f09a9f250b8e0d1",
        "created" : "2019-05-21T06:32:52Z",
        "updated" : "2020-12-22T13:20:56Z",
        "provisioning_state" : "Succeeded",
        "tags" : { },
        "properties" : {
          "engineVersion" : "5.7.23.5",
          "volumeType" : "ULTRAHIGH",
          "payMode" : "0",
          "flavorCode" : "rds.mysql.c6.4xlarge.4.ha",
          "userId" : "04ef9c3e450026431f35c01f946b49d7",
          "instanceStatus" : "normal",
          "opsWindow" : "10:00-14:00",
          "haMode" : "Ha",
          "enableSsl" : "1",
          "securityGroupId" : "f6e60b4b-94ca-4d30-9bb2-4ac5366a07e9",
          "createdAt" : "2019-05-21T06:32:52Z",
          "port" : "3306",
          "dataVolumeSizeInGBs" : "1000",
          "dataVip" : "9.9.9.9",
          "vpcId" : "ccbea875-6268-473e-bf90-e63159394df2",
          "networkId" : "ae261422-51c8-4a26-ba53-cfa4cc7d6690",
          "engineName" : "mysql"
        }
      }, {
        "id" : "7c330b98-87ed-4098-93c7-fc1edc4b6b5a",
        "name" : "clouddeploy-2pod-env2_hyp-0002",
        "provider" : "bms",
        "type" : "servers",
        "region_id" : "eu-de-04",
        "project_id" : "9e3425927a954ea5a86d78c3e797acec",
        "project_name" : "eu-de-04_region_service",
        "ep_id" : "0",
        "ep_name" : "default",
        "checksum" : "e18552532a73fdfef172061a398212e8ab72e7901a092b240f09a9f250b8e0d1",
        "created" : "2019-05-21T06:32:52Z",
        "updated" : "2020-12-22T13:20:56Z",
        "provisioning_state" : "Succeeded",
        "tags" : {
          "__type_baremetal" : ""
        },
        "properties" : {
          "accessIpv4" : "",
          "hostName" : "clouddeploy-2pod-env2-hyp-0002",
          "addresses" : [ {
            "OsExtIpsType" : "fixed",
            "OsExtIpsPortId" : "2db3738d-cbbd-4698-906f-c972845cba3a",
            "addr" : "192.168.1.49",
            "version" : 4,
            "OsExtIpsMacAddr" : "fa:16:3e:29:23:33"
          } ],
          "accessIpv6" : "",
          "metadata" : {
            "chargingMode" : "1",
            "meteringImageType" : "private",
            "imageName" : "Ubuntu 17.10 aarch64 server 64bit for BareMetal",
            "meteringOderId" : "CS20122903366ZKVX",
            "meteringProductId" : "00301-215006-0--0",
            "meteringImageId" : "e5065d43-4964-4071-b1ab-b17c70f903cc",
            "meteringResourcesPerCode" : "physical.r1.xlarge.linux",
            "vpcId" : "d7d8f09b-8bfe-4cc5-87a1-99012253ef44",
            "osBit" : "64"
          },
          "OsExtStsVmState" : "stopped",
          "configDrive" : "",
          "OsExtStsPowerState" : 4,
          "hostId" : "c3499877cccf68446308b59a0efddb6754029a3b6ddbd14dcca07c46",
          "securityGroup" : [ {
            "name" : "default",
            "id" : "d7872289-f428-4690-9292-583c12fc8449"
          } ],
          "ExtVolumesAttached" : [ ],
          "userId" : "183c03ab1281490e8be2e93038a9079c",
          "flavor" : {
            "disk" : "2000",
            "name" : "physical.r1.xlarge",
            "id" : "physical.r1.xlarge",
            "vcpus" : "64",
            "ram" : "262144"
          },
          "OsDcfDiskConfig" : "MANUAL",
          "hostStatus" : "UP",
          "OsSrvUsgLaunchedAt" : "2019-09-05T11:07:15.000000",
          "OsExtAz" : "eu-de-06b",
          "locked" : false,
          "OS-EXT-SRV-ATTR" : {
            "hostName" : "clouddeploy-2pod-env2-hyp-0002",
            "kernelId" : "",
            "ramdiskId" : "",
            "reservationId" : "r-703tla9e",
            "instanceName" : "instance-00034cd1",
            "host" : "eu-de-04b-pod02.eu-de-04",
            "rootDeviceName" : "/dev/vda",
            "hypervisorHostName" : "nova004@2",
            "launchIndex" : 0
          },
          "status" : "SHUTOFF",
          "schedulerHints" : { }
        }
      } ]

-  Example 2

   .. code-block::

      {
        "current_count" : 7,
        "next_marker" : "CAESJhIkNGEzNWYxMmYtZjM0NC00YTNkLWE1NDEtZWFjMDBiNDIzMjg1GgTGWJss"
      }

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
