RootAccessControl
=======================================================

A Namespace is a collection of Data Stream.

``GetRootNamespaceAcl()``
--------------------------------------------------------------------

Get the :ref:`AccessControlList <AccessControlListObj>` that is used to authorize access to a :ref:`Namespace <NamespaceObj>` if none is specified during creation.

**Http**

::

	GET api/Tenants/{tenantId}/AccessControl/Namespaces

**Parameters**

``String tenantId``
	The idenfifier for the account being accessed.

**Security**
	

**Returns**
	The root :ref:`AccessControlList <AccessControlListObj>` for :ref:`Namespace <NamespaceObj>`s.



|

**********************

``SetRootNamespaceAcl()``
--------------------------------------------------------------------

Set the :ref:`AccessControlList <AccessControlListObj>` that is used to authorize access to a :ref:`Namespace <NamespaceObj>` if none is specified during creation.

**Http**

::

	PUT api/Tenants/{tenantId}/AccessControl/Namespaces

**Parameters**

``String tenantId``
	The idenfifier for the account being modified.
``AccessControlList newAccessControlList``
	The new root :ref:`AccessControlList <AccessControlListObj>` for :ref:`Namespace <NamespaceObj>`s.

**Security**
	

**Returns**
	The new root :ref:`AccessControlList <AccessControlListObj>` for :ref:`Namespace <NamespaceObj>`s.



|

**********************


