Applications
=======================================================



``CreateClientApiKeyForApplication()``
--------------------------------------------------------------------

Create a :ref:`ClientApiKeySet <ClientApiKeySetObj>` for the specified application.

**Http**

::

	POST api/Tenants/{tenantId}/ClientApiKeySets/Keys

**Parameters**

``string tenantId``
	ID of the tenant the application belongs to.
``string applicationId``
	ID of the application for this request
``string description``
	Description of the :ref:`ClientApiKeySet <ClientApiKeySetObj>`

**Security**
	Allowed by Account Administrator :ref:`Role <RoleObj>`

**Returns**
	The created :ref:`ClientApiKeySet <ClientApiKeySetObj>`

**Notes**
	For HTTP requests and responses, the ClientApiKeySet object has the following properties and JSON-serialized body: 

.. _ClientApiKeySetObj: 

``string AppUri``
	App ID URI.
``bool CreateFirstKey``
	Create the first key in the Client API Key Set.
``string DisplayName``
	Display name.
``[string,[string]] RequiredResource``
	List of required resources.
``string TenantId``
	Tenant Id.

.. highlight:: C#

::

	HTTP/1.1 200
	Content-Type: application/json

 {
	"AppUri": "appuri",
	"CreateFirstKey": false,
	"DisplayName": "displayname",
	"RequiredResource":  { },
	"TenantId": "tenantid"
 }



|

**********************

``GetClientApiKeyCollectionFromApplication()``
--------------------------------------------------------------------

Get the :ref:`ClientApiKeyCollection <ClientApiKeyCollectionObj>` for the specified applicaiton.

**Http**

::

	GET api/Tenants/{tenantId}/ClientApiKeySets/Keys

**Parameters**

``string tenantId``
	ID of the tenant the application belongs to.
``string applicationId``
	ID of the application for this request

**Security**
	Allowed by Account Administrator :ref:`Role <RoleObj>`

**Returns**
	:ref:`ClientApiKeyCollection <ClientApiKeyCollectionObj>` for the specified applicaiton.

**Notes**
	For HTTP requests and responses, the ClientApiKeyCollection object has the following properties and JSON-serialized body: 

.. _ClientApiKeyCollectionObj: 

``string Id``
	Gets the identifier for this collection of API access keys, a GUID.
``[ClientApiKey] Keys``
	Gets a list of the application's access keys.

.. highlight:: C#

::

	HTTP/1.1 200
	Content-Type: application/json

 {
	"Id": "id",
	"Keys": []
 }



|

**********************

``DeleteClientApiKeyFromApplication()``
--------------------------------------------------------------------

Delete a specified :ref:`ClientApiKeySet <ClientApiKeySetObj>`.

**Http**

::

	DELETE api/Tenants/{tenantId}/ClientApiKeySets/Keys

**Parameters**

``string tenantId``
	ID of the tenant the application belongs to.
``string applicationId``
	ID of the application for this request
``string keyId``
	ID of the :ref:`ClientApiKeySet <ClientApiKeySetObj>` to be deleted.

**Security**
	Allowed by Account Administrator :ref:`Role <RoleObj>`

**Returns**
	HTTP status code - 200 OK if the :ref:`ClientApiKeySet <ClientApiKeySetObj>` was deleted.



|

**********************

``GetExternalApplicationsAsync()``
--------------------------------------------------------------------

Lists all applications from a customer's directory

**Http**

::

	GET api/Tenants/{tenantId}/externalapplications

**Parameters**

``string tenantId``
	ID of the tenant the application belongs to
``string skip``
	Number of applications to skip for paging purposes.
``string count``
	>Maximum number of applications to return in this page.
``string query``
	Prefix match to filter applications by applicationId or display name

**Security**
	Allowed by Account Administrator :ref:`Role <RoleObj>`

**Returns**
	An array of :ref:`Application <ApplicationObj>` objects that could be added to this account.

**Notes**
	For HTTP requests and responses, the Application object has the following properties and JSON-serialized body: 

.. _ApplicationObj: 

``string Id``
	Application Identifier
``string TenantId``
	Tenant Id
``string Name``
	Application Display Name
``[Role] Roles``
	List of roles for the application

.. highlight:: C#

::

	HTTP/1.1 200
	Content-Type: application/json

 {
	"Id": "id",
	"TenantId": "tenantid",
	"Name": "name",
	"Roles": []
 }



|

**********************

``RegisterClientApplicationAsync()``
--------------------------------------------------------------------

Registers the application with cloud services

**Http**

::

	POST api/Tenants/{tenantId}/Applications

**Parameters**

``string tenantId``
	ID of the tenant the application belongs to
``Application application``
	:ref:`Application <ApplicationObj>` object with required properties.

**Security**
	Account admin or Cluster operator

**Returns**
	The :ref:`Application <ApplicationObj>` for a tenant



|

**********************


