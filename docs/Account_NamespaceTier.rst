NamespaceTier
=======================================================

An attribute that specifies namespace performance.

	For HTTP requests and responses, the NamespaceTier object has the following properties and JSON-serialized body: 

.. _NamespaceTierObj: 

``String Id``
	GUID for this Namespace Tier.
``String Description``
	Description of this Tier.
``Int32 ThroughputUnits``
	The number of throughput units associated with this Tier.
``Int32 StorageUnits``
	The number of Storage units associated with this Tier.

.. highlight:: C#

::

	HTTP/1.1 200
	Content-Type: application/json

 {
	"Id": "id",
	"Description": "description",
	"ThroughputUnits": 0,
	"StorageUnits": 0
 }

``GetNamespaceTier()``
--------------------------------------------------------------------

Retrieves a Namespace tier associated with a specified id

**Http**

::

	GET api/NamespaceTiers/{namespaceTierId}

**Parameters**

``String namespaceTierId``
	The tier identifier for this request

**Security**
	Allowed by Account Member :ref:`Role <RoleObj>`

**Returns**
	A :ref:`NamespaceTier <NamespaceTierObj>` object with the specified namespaceTierId



|

**********************

``GetAllNamespaceTiers()``
--------------------------------------------------------------------

Retrieves a list of all available namespace tiers.

**Http**

::

	GET api/NamespaceTiers

**Parameters**


**Security**
	Allowed by Account Member :ref:`Role <RoleObj>`

**Returns**
	An array of :ref:`NamespaceTier <NamespaceTierObj>` objects



|

**********************


