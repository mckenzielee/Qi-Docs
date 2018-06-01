Search Examples
===============

This topic presents several query examples you can use to perform more complex searches.


Perform a basic query 
---------------------

By default, specifying one or more strings in the query searches all
object fields for the strings in the query.

+-----------------+-----------------------+-----------------------------+
| Query string    | Matches field value   | Does not match field value  |
+=================+=======================+=============================+
| pump            | -  pump               | -  pumps                    |
|                 |                       |                             |
|                 | -  the pump           |                             |
+-----------------+-----------------------+-----------------------------+
| pump pressure   | -  pump               | -  pumps                    |
|                 |                       |                             |
|                 | -  pressure           | -  pressures                |
|                 |                       |                             |
|                 | -  pressure pump      |                             |
+-----------------+-----------------------+-----------------------------+

**REST API example**

::

  GET api/Tenants/{tenantId}/Namespaces/{namespaceId}/Streams?query=pump pressure

**C# example**

::

  GetStreamsAsync(query:”pump pressure”);

Search specific fields
-----------------------

You can qualify which fields are searched by using the following
syntax: 

::

  fieldname:fieldvalue

The field name is case sensitive and must
be lowercase; however, the field value is not case sensitive.


**REST API example**

::

  GET api/Tenants/{tenantId}/Namespaces/{namespaceId}/Streams?query=name:pump name:pressure

**C# example**

::

  GetStreamsAsync(query:”name:pump name:pressure”);

Search for a phrase
-------------------

The search engine automatically searches on strings delimited by
whitespace and dashes (with the exception of identifier fields like Id
or TypeId fields). To search for values that include delimiters, enclose the value in double quotes.

+-------------------+------------------------------+-----------------------------+
| Query string      | Matches field value          | Does not match field value  |
+===================+==============================+=============================+
| “pump pressure”   | -  pump pressure             | -  the pump                 |
|                   |                              |                             |
|                   | -  the pump pressure gauge   | -  pressure                 |
|                   |                              |                             |
|                   |                              | -  pressure pump            |
+-------------------+------------------------------+-----------------------------+

**REST API example**

::

  GET api/Tenants/{tenantId}/Namespaces/{namespaceId}/Streams?query=”pump pressure”

**C# example**

::

  GetStreamsAsync(query:”\\”pump pressure\\””);

Wildcard search
---------------

You can use the ‘\*’ character as a wildcard to specify an incomplete
string.

+----------------+-----------------------+-----------------------------+
| Query string   | Matches field value   | Does not match field value  |
+================+=======================+=============================+
| log\*          | -  log                | -  analog                   |
|                |                       |                             |
|                | -  logs               |                             |
|                |                       |                             |
|                | -  logger             |                             |
+----------------+-----------------------+-----------------------------+

Note the following restrictions to wildcard searches:

1) The ‘\*’ character cannot be the first character in the search term.
   For example, you can search for log\* or log\*r, but you cannot search
   for \*log.

2) Wildcards cannot be used in conjunction with a phrase search. The
   following search strings are invalid:

   a. “simple stream\*”

   b. “stream\* data”

   c. “sub string”\*


**REST API example**

::

  GET api/Tenants/{tenantId}/Namespaces/{namespaceId}/Streams?query=log\*

**C# example**

::

  GetStreamsAsync(query:”log\*”);


Use logical operators for complex multiple-term searches
--------------------------------------------------------

You can use the AND, OR, and NOT operators to build complex search terms.
In addition, you can specify the order of operations using parentheses.
Logical operators are specified in all uppercase letters.

+--------------------------------------------------+-----------------------------------------------------------------------------------+-----------------------------+
| Query string                                     | Matches field value                                                               | Does not match field value  |
+==================================================+===================================================================================+=============================+
| mud AND log                                      | -  log mud                                                                        | -  mud                      |
|                                                  |                                                                                   |                             |
|                                                  | -  mud log                                                                        | -  log                      |
+--------------------------------------------------+-----------------------------------------------------------------------------------+-----------------------------+
| mud OR log                                       | -  mud                                                                            |                             |
|                                                  |                                                                                   |                             |
|                                                  | -  log                                                                            |                             |
|                                                  |                                                                                   |                             |
|                                                  | -  mud log                                                                        |                             |
+--------------------------------------------------+-----------------------------------------------------------------------------------+-----------------------------+
| mud AND (NOT log)                                | -  mud                                                                            | -  mud log                  |
+--------------------------------------------------+-----------------------------------------------------------------------------------+-----------------------------+
| mud AND (log OR pump\*)                          | -  mud log                                                                        | -  mud bath                 |
|                                                  |                                                                                   |                             |
|                                                  | -  mud pumps                                                                      |                             |
+--------------------------------------------------+-----------------------------------------------------------------------------------+-----------------------------+
| name:stream\* AND (tags:pressure OR tags:pump)   | The name starts with “stream” and has tag values of either “pressure” or “pump”   |                             |
+--------------------------------------------------+-----------------------------------------------------------------------------------+-----------------------------+


