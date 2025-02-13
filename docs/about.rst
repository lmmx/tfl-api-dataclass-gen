============
Introduction
============

The Transport for London (TfL) API provides a Swagger schema file, but as discussed
`on the TfL Tech Forum <https://techforum.tfl.gov.uk/t/swagger-file-outdated/2085>`_
this is outdated and instead you should use "a YAML/JSONWADL definition file"
from the *API definition* drop-down menu.

Unfortunately, while there are fewer errors shown on the `Swagger Editor <https://editor.swagger.io/>`_
with the Open API 3 JSON than with the original Unified API Swagger JSON,
there are still some. Rather than *"Declared path parameter...needs to be defined as a path
parameter at either the path or operation level"* and *"Operations must have unique operationIds."*
there are only *"Schemas with 'type: array', require a sibling 'items: ' field"*.

In other words, the array-type entries must also define the type of the items in the array.
From inspecting the responses, it appears that these types are defined in the responses,
and can differ from item to item within a single array.

For the :code:`StopPoint` API these are:

* :code:`/ServiceTypes.get.parameters.lineIds`
* :code:`/ServiceTypes.get.parameters.modes`
* :code:`/.get.parameters.modes`
* :code:`/.get.parameters.categories`
* :code:`/Search/{query}.get.parameters.modes`
* :code:`/Search/{query}.get.parameters.lines`
* :code:`/Search.get.parameters.modes`
* :code:`/Search.get.parameters.lines`

In other words, line IDs, modes, categories of properties ("in the StopPoint's property bag"
as given by the :code:`/StopPoint/Meta/categories` endpoint, or the keyword "none"),
and lines (presumably again the line IDs).
