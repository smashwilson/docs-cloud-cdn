
.. THIS OUTPUT IS GENERATED FROM THE WADL. DO NOT EDIT.

.. _post-create-a-service-v1.0-project-id-services:

Create a service
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

.. code::

    POST /v1.0/{project_id}/services

Creates a service.

To create a new service, provide a JSON body for the new service with the required attributes.

For more information about rules ordering, caching rules, origin rules, and referrer rules, see `Creating rules <http://docs.rackspace.com/cdn/api/v1.0/cdn-devguide/content/createRules-d101.html>`__.

For origin rules, use the path /* to include all content for the site.

.. note::
   ``service_id``, which is used in several of the services operations, is returned in the response to create a service. Take note this value. You can also retrieve ``service_id`` using `List a service <http://docs.rackspace.com/cdn/api/v1.0/cdn-devguide/content/GET_getService__services__service_id__servicesOperations.html>`__.
   
   



This table shows the possible response codes for this operation:


+--------------------------+-------------------------+-------------------------+
|Response Code             |Name                     |Description              |
+==========================+=========================+=========================+
|202                       |Accepted                 |The request has been     |
|                          |                         |accepted for processing. |
+--------------------------+-------------------------+-------------------------+
|400                       |Bad Request              |Attempt to create a      |
|                          |                         |service with a flavor_id |
|                          |                         |that is not 'cdn'.       |
+--------------------------+-------------------------+-------------------------+
|400                       |Bad Request              |Invalid JSON.            |
+--------------------------+-------------------------+-------------------------+
|400                       |Bad Request              |Missing or empty domains |
|                          |                         |list.                    |
+--------------------------+-------------------------+-------------------------+
|400                       |Bad Request              |Missing or empty origins |
|                          |                         |list.                    |
+--------------------------+-------------------------+-------------------------+
|400                       |Bad Request              |Non-Boolean value for    |
|                          |                         |origins:origin:ssl.      |
+--------------------------+-------------------------+-------------------------+
|400                       |Bad Request              |Restrictions list        |
|                          |                         |present with no name.    |
+--------------------------+-------------------------+-------------------------+
|400                       |Bad Request              |Value for                |
|                          |                         |origins:origin:port is   |
|                          |                         |something other than 80  |
|                          |                         |or 443.                  |
+--------------------------+-------------------------+-------------------------+


Request
""""""""""""""""




This table shows the URI parameters for the request:

+-------------+-------+--------------------------------------------------------------+
|Name         |Type   |Description                                                   |
+=============+=======+==============================================================+
|{project_id} |String |The project ID for the user. If you do not set the ``X-       |
|             |       |Project-Id header`` in the request, use ``project_id`` in the |
|             |       |URI. For example: ``GET                                       |
|             |       |https://global.cdn.api.rackspacecloud.com/v1.0/{project_id}`` |
+-------------+-------+--------------------------------------------------------------+





This table shows the body parameters for the request:

+---------------+-------------+------------------------------------------------------------------------------+
|Name           |Type         |Description                                                                   |
+===============+=============+==============================================================================+
|name           |*(Required)* |Specifies the name of the service. The minimum length for ``name`` is 3. The  |
|               |             |maximum length is 256.                                                        |
+---------------+-------------+------------------------------------------------------------------------------+
|domains        |*(Required)* |Specifies a list of domains used by users to access their website.            |
+---------------+-------------+------------------------------------------------------------------------------+
|domain         |*(Required)* |Specifies the domain used to access the assets on your website, for which you |
|               |             |use a CNAME to the CDN provider. The minimum length for domain is 3. The      |
|               |             |maximum length is 253.                                                        |
+---------------+-------------+------------------------------------------------------------------------------+
|protocol       |*(Optional)* |Specifies the protocol used to access the assets on this domain. Only         |
|               |             |``http`` or ``https`` are allowed. The default ``protocol`` is ``http``.      |
+---------------+-------------+------------------------------------------------------------------------------+
|certificate    |*(Optional)* |Specifies the type of security certificate. For the ``certificate`` parameter |
|               |             |to apply, the ``protocol`` parameter must be set to ``https``. Use            |
|               |             |``shared``, ``san``, or ``custom``. For all 3 types of security certificates, |
|               |             |make sure that your origin (or origins) are SSL-enabled. Your SSL certificate |
|               |             |needs to come from a trusted certificate authority (CA). For more information |
|               |             |about security certificates and Rackspace CDN, see `Rackspace CDN secure      |
|               |             |delivery options                                                              |
|               |             |<https://www.rackspace.com/knowledge_center/article/rackspace-cdn-secure-     |
|               |             |delivery-options>`__.                                                         |
+---------------+-------------+------------------------------------------------------------------------------+
|shared         |*(Optional)* |Uses a shared https operator domain. The ``domain`` parameter must be a       |
|               |             |single word that is not dot separated.                                        |
+---------------+-------------+------------------------------------------------------------------------------+
|origins        |*(Required)* |Specifies a list of origin domains or IP addresses where the original assets  |
|               |             |are stored.                                                                   |
+---------------+-------------+------------------------------------------------------------------------------+
|origin         |*(Required)* |Specifies the URL or IP address from which to pull origin content. The        |
|               |             |minimum length for ``origin`` is 3. The maximum length is 253.                |
+---------------+-------------+------------------------------------------------------------------------------+
|port           |*(Optional)* |Specifies the port used to access the origin. The default is port 80. Note:   |
|               |             |Rackspace CDN cannot be used with custom ports. Services are required to run  |
|               |             |on HTTP (80) and HTTPS (443) for the origin servers. All origins in the       |
|               |             |origin specification must define the port so that it that corresponds to the  |
|               |             |domain's protocol. If the domain's protocol is http, the port should be 80;   |
|               |             |if the domain's protocol is https, the port should be 443.                    |
+---------------+-------------+------------------------------------------------------------------------------+
|ssl            |*(Optional)* |Uses HTTPS to access the origin. The default is false.                        |
+---------------+-------------+------------------------------------------------------------------------------+
|rules          |*(Required)* |Specifies a collection of rules that define the conditions when this origin   |
|               |             |should be accessed. If there is more than one origin, the ``rules`` parameter |
|               |             |is required.                                                                  |
+---------------+-------------+------------------------------------------------------------------------------+
|name           |*(Required)* |Specifies the name of this rule. The minimum length for ``name`` is 1. The    |
|               |             |maximum length is 256.                                                        |
+---------------+-------------+------------------------------------------------------------------------------+
|request_url    |*(Required)* |Specifies the request URL that this rule should match for this origin to be   |
|               |             |used. The minimum length for ``request_url`` is 1. The maximum length is      |
|               |             |1024. Regex is supported. Note: Use a Perl Compatible Regex (PCRE). For more  |
|               |             |information about PRCE, see `Regular Expressions (Perl-Compatible)            |
|               |             |<http://php.net/manual/en/book.pcre.php>`__.                                  |
+---------------+-------------+------------------------------------------------------------------------------+
|hostheadertype |*(Optional)* |Specifies the type for the host header. The default value is ``domain``.      |
|               |             |Other valid values are ``origin`` and ``custom``.                             |
+---------------+-------------+------------------------------------------------------------------------------+
|hostheadervalue|*(Optional)* |Specifies the value to be contained in the host header. The default value is  |
|               |             |``NULL``; this value is assigned only when ``hostheadertype`` is ``domain``.  |
|               |             |You are required to specify ``hostheadervalue`` only when ``hostheadertype``  |
|               |             |is specified as ``custom``. If you specify ``hostheadertype`` as ``origin``,  |
|               |             |``hostheadervalue`` takes the value of the origin domain.                     |
+---------------+-------------+------------------------------------------------------------------------------+
|caching        |*(Optional)* |Specifies the TTL rules for the assets under this service. Supports wildcards |
|               |             |for fine-grained control.                                                     |
+---------------+-------------+------------------------------------------------------------------------------+
|name           |*(Required)* |Specifies the name of this caching rule. The minimum length for ``name`` is   |
|               |             |1. The maximum length is 256. Note: ``default`` is a reserved name used for   |
|               |             |the default TTL setting.                                                      |
+---------------+-------------+------------------------------------------------------------------------------+
|ttl            |*(Required)* |Specifies the TTL to apply. The value of ``ttl`` must be greater than or      |
|               |             |equal to 0. The maximum value that you can specify is 365 days.               |
+---------------+-------------+------------------------------------------------------------------------------+
|rules          |*(Optional)* |Specifies a collection of rules that determine if this TTL should be applied  |
|               |             |to an asset. Note: This is a required property if more than one entry is      |
|               |             |present for caching.                                                          |
+---------------+-------------+------------------------------------------------------------------------------+
|name           |*(Required)* |Specifies the name of this rule. The minimum length for ``name`` is 1. The    |
|               |             |maximum length is 256.                                                        |
+---------------+-------------+------------------------------------------------------------------------------+
|request_url    |*(Required)* |Specifies the request URL that this rule should match for this TTL to be      |
|               |             |used. The minimum length for ``request_url`` is 1. The maximum length is      |
|               |             |1024. Regex is supported. Note: Use a Perl Compatible Regex (PCRE). For more  |
|               |             |information about PRCE, see `Regular Expressions (Perl-Compatible)            |
|               |             |<http://php.net/manual/en/book.pcre.php>`__.                                  |
+---------------+-------------+------------------------------------------------------------------------------+
|restrictions   |*(Optional)* |Specifies the restrictions that define who can access assets (content from    |
|               |             |the CDN cache).                                                               |
+---------------+-------------+------------------------------------------------------------------------------+
|name           |*(Required)* |Specifies the name of this restriction. The minimum length for ``name`` is 1. |
|               |             |The maximum length is 256.                                                    |
+---------------+-------------+------------------------------------------------------------------------------+
|access         |*(Optional)* |Specifies the type of this restriction. Valid values are ``whitelist``, which |
|               |             |is the default value and allows access, or ``blacklist``, which does not      |
|               |             |allow access.                                                                 |
+---------------+-------------+------------------------------------------------------------------------------+
|rules          |*(Optional)* |Specifies a collection of rules that determine if this restriction should be  |
|               |             |applied to an asset.                                                          |
+---------------+-------------+------------------------------------------------------------------------------+
|name           |*(Required)* |Specifies the name of this rule. The minimum length for ``name`` is 1. The    |
|               |             |maximum length is 256.                                                        |
+---------------+-------------+------------------------------------------------------------------------------+
|referrer       |*(Optional)* |Specifies the HTTP host that requests must come from. The minimum length for  |
|               |             |``referrer`` is 3. The maximum length is 1024.                                |
+---------------+-------------+------------------------------------------------------------------------------+
|request_url    |*(Optional)* |Specifies the request URL to which the rule applies. The default value is     |
|               |             |``/*``, which indicates all content at the request URL.                       |
+---------------+-------------+------------------------------------------------------------------------------+
|client_ip      |*(Optional)* |Specifies the client IP address to which the rule applies.                    |
+---------------+-------------+------------------------------------------------------------------------------+
|log_delivery   |*(Required)* |Specifies whether to enable log delivery to a Cloud Files container. You can  |
|               |             |use access log delivery to analyze the number of requests for each object,    |
|               |             |the client IP address, and time-based usage patterns (such as monthly or      |
|               |             |seasonal usage). Log files are named according to the following pattern:      |
|               |             |service name, log date, log hour, and MD5 hash. For example:                  |
|               |             |``www.mywebsite.com/2015/02/01/16/096e6c4473f235db081deb51f42a8d98.log.gz``.  |
|               |             |In this example, ``www.mywebsite.com`` is the name of the service,            |
|               |             |``2015/02/01`` is the date (February 1, 2015), and ``16`` is the hour that    |
|               |             |the log file was created. There might be multiple files for a given hour      |
|               |             |because the system splits log files based on both time and log file size. All |
|               |             |times in the access logs are UTC time. Within the gzip logs, the format of    |
|               |             |the entries is similar to National Center for Supercomputing Applications     |
|               |             |(NCSA) combined log format, but without cookies. The pattern follows. The     |
|               |             |dashes (-) denote fields that the NCSA combined log format dictates be        |
|               |             |present but that Rackspace CDN does not capture. For example: ``client_ip - - |
|               |             |[day/month/year:hour:minute:second timezone] “method request HTTP_version”    |
|               |             |return_code bytes_sent “referrer” “user_agent”`` Logs are stored in a Cloud   |
|               |             |Files container named.CDN_ACCESS_LOGS. If this container does not exist, it   |
|               |             |is created.                                                                   |
+---------------+-------------+------------------------------------------------------------------------------+
|enabled        |*(Required)* |Specifies whether to enable or disable log delivery. Valid values are         |
|               |             |``true`` and ``false``.                                                       |
+---------------+-------------+------------------------------------------------------------------------------+
|flavor_id      |*(Required)* |Specifies the CDN provider flavor ID to use. For a list of flavors, see the   |
|               |             |operation to list the available flavors. The minimum length for ``flavor_id`` |
|               |             |is 3. The maximum length is 256.                                              |
+---------------+-------------+------------------------------------------------------------------------------+





**Example Create a service: JSON request**


.. code::

   POST /v1.0/110011/services HTTP/1.1
   Host: global.cdn.api.rackspacecloud.com
   X-Auth-Token: 0f6e9f63600142f0a970911583522217
   Accept: application/json
   Content-type: application/json
   


.. code::

   {
       "name": "mywebsite.com",
       "domains": [
           {
               "domain": "www.mywebsite.com"
           },
           {
               "domain": "blog.mywebsite.com"
           }
       ],
       "origins": [
           {
               "origin": "mywebsite.com",
               "port": 80,
               "ssl": false,
               "hostheadertype": "origin",
               "rules": [
               ]
           }
       ],
       "restrictions": [
                        {
                        "name": "website only",
                        "rules": [
                                  {
                                  "name": "mywebsite.com",
                                  "referrer": "www.mywebsite.com"
                   }
               ]
           }
       ],
       "caching": [
           {
               "name": "default",
               "ttl": 3600
           }
       ],
       "log_delivery": {
           "enabled": true
       },   
       "flavor_id": "cdn"
      }





Response
""""""""""""""""










**Example Create a service: JSON response**


.. code::

   HTTP/1.1 202 Accepted
   Content-Type: application/json
   Location: https://global.cdn.api.rackspacecloud.com/v1.0/services/96737ae3-cfc1-4c72-be88-5d0e7cc9a3f0




