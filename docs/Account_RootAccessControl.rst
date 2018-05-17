RootAccessControl
=======================================================

Apis to control default access to entities governed by an :ref:`AccessControlList <AccessControlListObj>`.

|

**********************

``GetRootNamespaceAcl()``
--------------------------------------------------------------------

Get the :ref:`AccessControlList <AccessControlListObj>` that is used to authorize access to a :ref:`Namespace <NamespaceObj>` if none is specified during creation.

**Http**

::

	GET api/Tenants/{tenantId}/AccessControl/Namespaces

**Parameters**

``string tenantId``
	The idenfifier for the account being accessed.

**Security**
	:ref:`CommonAccessRights.Read <CommonAccessRightsEnum>`

**Returns**
	The root :ref:`AccessControlList <AccessControlListObj>` for :ref:`Namespaces <NamespaceObj>`.



|

**********************

``SetRootNamespaceAcl()``
--------------------------------------------------------------------

Set the :ref:`AccessControlList <AccessControlListObj>` that is used to authorize access to a :ref:`Namespace <NamespaceObj>` if none is specified during creation.

**Http**

::

	PUT api/Tenants/{tenantId}/AccessControl/Namespaces

**Parameters**

``string tenantId``
	The idenfifier for the account being modified.
``AccessControlList newAccessControlList``
	The new root :ref:`AccessControlList <AccessControlListObj>` for :ref:`Namespaces <NamespaceObj>`.

**Security**
	:ref:`CommonAccessRights.ManageAccessControl <CommonAccessRightsEnum>`

**Returns**
	The new root :ref:`AccessControlList <AccessControlListObj>` for :ref:`Namespaces <NamespaceObj>`.



|

**********************


