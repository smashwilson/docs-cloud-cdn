
.. THIS OUTPUT IS GENERATED FROM THE WADL. DO NOT EDIT.

Retrieve Asset Analytics
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

.. code::

    GET /v1.0/{project_id}/services/{service_id}/analytics

Retrieves asset analytics - usage data (such as hits or misses) about the service.

The examples contain the expanded URL template with values inherited from parameters (for example, https://private-anon-afee1c004-cloudcdn.apiary-mock.com/services/mywebsite/analytics).



This table shows the possible response codes for this operation:


+--------------------------+-------------------------+-------------------------+
|Response Code             |Name                     |Description              |
+==========================+=========================+=========================+
|200                       |OK                       |Success.                 |
+--------------------------+-------------------------+-------------------------+


Request
""""""""""""""""

This table shows the URI parameters for the request:

+-------------+-------------+--------------------------------------------------------------+
|Name         |Type         |Description                                                   |
+=============+=============+==============================================================+
|{project_id} |xsd:string   |The project ID for the user. If you do not set the ``X-       |
|             |             |Project-Id header`` in the request, use ``project_id`` in the |
|             |             |URI. For example: ``GET                                       |
|             |             |https://global.cdn.api.rackspacecloud.com/v1.0/{project_id}`` |
+-------------+-------------+--------------------------------------------------------------+
|{service_id} |xsd:string   |Specifies the service ID that represents distributed content. |
|             |*(Required)* |The value is a UUID, such as 96737ae3-cfc1-4c72-be88-         |
|             |             |5d0e7cc9a3f0, that is generated by the server.                |
+-------------+-------------+--------------------------------------------------------------+



This table shows the query parameters for the request:

+--------------------------+-------------------------+-------------------------+
|Name                      |Type                     |Description              |
+==========================+=========================+=========================+
|url                       |xsd:string *(Optional)*  |Specifies the ``url`` of |
|                          |                         |the asset on which to    |
|                          |                         |get analytics. If left   |
|                          |                         |blank, analytics are     |
|                          |                         |reported against all the |
|                          |                         |assets of the service.   |
+--------------------------+-------------------------+-------------------------+




This operation does not accept a request body.




**Example Retrieve Asset Analytics: JSON request**


.. code::

    GET /v1.0/110011/services/serviceName/analytics?urlOfAssetToCheck HTTP/1.1
    Host: global.cdn.api.rackspacecloud.com
    X-Auth-Token: 0f6e9f63600142f0a970911583522217
    Accept: application/json
    Content-type: application/json


Response
""""""""""""""""


This operation does not accept a response body.




**Example Retrieve Asset Analytics: JSON response**


.. code::

    200 OK
    Content-Type: application/json
