Namespace
=======================================================

A Namespace is a collection of Data Streams.

	For HTTP requests and responses, the Namespace object has the following properties and JSON-serialized body: 

.. _NamespaceObj: 

``string Id``
	Name of this Namespace. Unique within a Tenant's Namespaces.
``string TenantId``
	GUID of the Tenant that this Namespace corresponds to
``string Description``
	Description of this Namespace.
``string TierId``
	Id of the Tier that this Namespace is associated with.
``int32 ThroughputUnits``
	Number of Throughput units for this Namespace.
``int32 StorageUnits``
	Number of Storage units for this Namespace.
``NamespaceProvisioningState State``
	Current state of this Namespace.
``OwnerTrustee Owner``
	Owner :ref:`Trustee <TrusteeObj>` of this Namespace.
``AccessControlList AccessControlList``
	Access Control List.

.. highlight:: C#

::

	HTTP/1.1 200
	Content-Type: application/json

 {
	"Id": "id",
	"TenantId": "tenantid",
	"Description": "description",
	"TierId": "tierid",
	"ThroughputUnits": 0,
	"StorageUnits": 0,
	"State": 0,
	"Owner":  {
		"Type": 2,
		"TenantId": "string",
		"ApplicationId": "string"
	 },
	"AccessControlList":  {
		"RoleTrusteeAccessControlEntries": []
	 }
 }

|

**********************

``GetAll()``
--------------------------------------------------------------------

Returns all :ref:`Namespaces <NamespaceObj>` owned by the specified tenant that the caller has access to.

**Http**

::

	GET api/Tenants/{tenantId}/Namespaces

**Parameters**

``string tenantId``
	The :ref:`Tenant <TenantObj>` identifier for the request.

**Security**
	A :ref:`Namespace <NamespaceObj>` can only be retrieved if the current principle has Read access.

**Returns**
	An array of all :ref:`Namespace <NamespaceObj>` objects for the specified tenantId that the caller has access.



|

**********************

``GetNamespaceById()``
--------------------------------------------------------------------

Returns the Namespace with the specified Id.

**Http**

::

	GET api/Tenants/{tenantId}/Namespaces/{namespaceId}

**Parameters**

``string tenantId``
	The account identifier for the request
``string namespaceId``
	The Namespace identifier for this request

**Security**
	A :ref:`Namespace <NamespaceObj>` can only be retrieved if the current principle has Read access.

**Returns**
	A :ref:`Namespace <NamespaceObj>` object with the specified namespaceId



|

**********************

``Create()``
--------------------------------------------------------------------

Creates a namespace.

**Http**

::

	POST api/Tenants/{tenantId}/Namespaces

**Parameters**

``string tenantId``
	The idenfifier for the account the namespace is to be created for.
``Namespace namespaceObj``
	The :ref:`Namespace <NamespaceObj>` to be created.

**Security**
	A :ref:`Namespace <NamespaceObj>` can only be create if the current principle has Write access.

**Returns**
	The created :ref:`Namespace <NamespaceObj>` object



|

**********************

``Update()``
--------------------------------------------------------------------

Updates Namespace information - Description, TierId, AccessControl, and Owner.

**Http**

::

	PUT api/Tenants/{tenantId}/Namespaces/{namespaceId}

**Parameters**

``string tenantId``
	The identifier of Namespace's Account.
``string namespaceId``
	The identifier for the Namespace to update.
``Namespace newProperties``
	The new details to store for the Namespace.

**Security**
	A :ref:`Namespace <NamespaceObj>` can only be updated if the current principle has Write access.
            The AccessControlList and Owner can only be updated if the current principle has ManageAccessControl access.

**Returns**
	The updated :ref:`Namespace <NamespaceObj>`.



|

**********************

``Delete()``
--------------------------------------------------------------------

Deletes a namespace.

**Http**

::

	DELETE api/Tenants/{tenantId}/Namespaces/{namespaceId}

**Parameters**

``string tenantId``
	The identifier of namespace's account
``string namespaceId``
	The identifier of the namespace to be deleted

**Security**
	A :ref:`Namespace <NamespaceObj>` can only be deleted if the current principle has Delete access.

**Returns**
	Nothing is returned



|

**********************


