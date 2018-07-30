Compression
===========
To more efficiently utilize network bandwidth the OCS Sequential Data Store supports ``gzip`` and ``deflate`` compression schemes for reading data and writing data through the REST API

Request compression (writing data)
----------------------------------
HTTP request body content can be compressed using the supported compression schemes. 
To indicate that the content of a request is compressed, the compression scheme should be specified in the ``Content-Encoding`` HTTP header of the request.

Response compression (reading data)
-----------------------------------
When reading data 