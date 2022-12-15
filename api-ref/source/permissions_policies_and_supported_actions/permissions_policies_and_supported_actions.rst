:original_name: rms_02_0015.html

.. _rms_02_0015:

Permissions Policies and Supported Actions
==========================================

This chapter describes fine-grained permissions management for your RMS. If your OTC account does not need individual IAM users, then you may skip over this chapter.

A policy is a set of permissions defined in JSON format. By default, new IAM users do not have permissions assigned. You need to add a user to one or more groups, and attach permissions policies or roles to these groups. Users inherit permissions from the groups to which they are added and can perform specified operations on cloud services based on the permissions.

Based on the granularity of authorization, permissions are classified into roles and policies.

-  Roles are a type of service-based, coarse-grained authorization mechanism that defines permissions related to user responsibilities.
-  Policies define API-based permissions for operations on specific resources under certain conditions, allowing for more fine-grained, secure access control of cloud resources.

.. note::

   Policy-based authorization is useful if you want to allow or deny the access to an API.

An account has all the permissions required to call all APIs, but IAM users must be assigned the required permissions. The permissions required for calling an API are determined by the actions supported by the API. Only users who have been granted permissions allowing the actions can call the API successfully.

Supported Actions
-----------------

Operations supported by policies are specific to APIs. The following are common concepts related to policies:

-  Permissions: Statements in a policy that allow or deny certain operations.

-  APIs: REST APIs that can be called by a user who has been granted specific permissions.

-  Actions: Specific operations that are allowed or denied.

-  Related actions: Actions on which a specific action depends to take effect. When assigning permissions for the action to a user, you also need to assign permissions for the related actions.

-  IAM projects or enterprise projects: Type of projects in which policies can be used to grant permissions. A policy can be applied to IAM projects, enterprise projects, or both. Policies that contain actions for both IAM and enterprise projects can be used and take effect for both IAM and Enterprise Management. Policies that only contain actions for IAM projects can be used and only take effect for IAM.

   RMS supports the following actions that can be defined in custom policies:

   :ref:`My Resources <rms_02_0016>` includes actions supported by all resource APIs, such as the APIs for viewing resource history and listing resources of a specific type.

.. note::

   The check mark (Y) indicates that an action takes effect. The cross mark (x) indicates that an action does not take effect.
