:original_name: rms_01_0005.html

.. _rms_01_0005:

Permissions Management
======================

With IAM, you can grant permissions to users to control their access to specific resource types. IAM provides identity authentication, permissions management, and access control, helping you to secure access to your Open Telekom Cloud (OTC) resources.

For further information see Identity and Access Management (IAM) documentation.

RMS Permissions
---------------

All users have the permissions to access the **My Resources** page. The resources displayed depend on the resource permissions of the users. For details about resource permissions of users, see :ref:`Resource Permissions <rms_01_0005__section311mcpsimp>`.

By default, new IAM users do not have permissions assigned. You need to add the users to one or more groups, and attach permissions policies or roles to these groups. Users inherit permissions from the groups to which they are added.

After authorization, the users can perform specified operations based on the permissions.

:ref:`Table1 <rms_01_0005____table298132619114>` lists system-defined roles and permissions supported by RMS.

.. _rms_01_0005____table298132619114:

.. table:: **Table 1** System-defined roles and permissions supported by RMS

   +----------------+-------------------------------------------------------------------+
   | Role           | Description                                                       |
   +================+===================================================================+
   | RMS FullAccess | Has the permissions to perform all operations on the RMS console. |
   +----------------+-------------------------------------------------------------------+

.. _rms_01_0005__section311mcpsimp:

Resource Permissions
--------------------

The resources displayed on the **My Resources** page depend on the resource permissions of the users.

User permission policies can be defined in IAM and Enterprise Management.

When you attempt to query the resource list, IAM checks whether you belong to the **admin** user group first. If yes, you have the administrator permissions for all resources. In a policy that contains both Allow and Deny statements, the Deny statements take precedence.
