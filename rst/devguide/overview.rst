========
Overview
========

A content delivery network (CDN) is designed to improve the performance
of publicly distributed assets.  Assets can be anything from website
content, to web application components, to media like videos, ads, and
interactive experiences.  CDNs decrease the load time of these assets by
caching them on edge nodes, which are also called edge servers or point
of presence (PoP) servers.  Edge nodes are distributed around the globe,
and they cache content and serve it directly to customers, thus reducing
transit time to a customer's location. 

Rackspace CDN gives you the power to accelerate content on any public
resource at Rackspace. It provides a simple API and Control Panel
experience for you to manage your CDN-enabled domains and the origins
and assets associated with those domains. 

The Rackspace CDN architecture includes the following components:

-  A RESTful API

-  The ability to cache publicly accessible resources hosted on a Cloud
   Server instance, or a public Cloud Files container

-  A single global endpoint to access the API

-  Use of the Akamai Technologies content delivery network, which is one
   of the world's largest distributed computing platforms

In addition to this guide, see the `Rackspace CDN Getting
Started Guide`_, which explains how to start using the API.

.. _Rackspace CDN Getting Started Guide: http://docs.rackspace.com/cdn/api/v1.0/cdn-gettingstarted/content/Overview.html

Intended audience
-----------------

This document is intended for software developers who want to develop
applications that use the Rackspace CDN API. You should be familiar with
the following technologies:

-  RESTful web services

-  HTTP/1.1 conventions

-  JSON data serialization formats

Document change history
-----------------------

This version of the guide replaces and obsoletes all earlier versions.
The most recent changes are described in the following table:

+----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------+
| Revision Date  |         Summary of Changes                                                                                                                                  |
+================+=============================================================================================================================================================+
| June 10, 2015  |-  Rackspace CDN has been updated to allow HTTP traffic on an SSL domain. Consequently, the ``protocol`` parameter description for the request in "Create a  |
|                |   service" has been updated. The statement that indicated that domains must use the same protocol has been deleted.                                         |
|                |                                                                                                                                                             |
|                |-  The ``ttl`` parameter description for the request in "Create a service" has been updated. The maximum value that you can specify for ``ttl`` is 365 days. |
|                |                                                                                                                                                             |
|                |-  The table in "Absolute limits" has been updated to include the limits for TTL and the number of domains that can be listed.                               |
+----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------+
| June 8, 2015   |Updated the definition of ``limit`` for the request in "Retrieve all services". The maximum value is 20.                                                     |
+----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------+
| June 1, 20155  |Corrected ``log_delivery`` in the request body example in "Create a service" by removing the extra colon (:) after ``enabled``.                              |
+----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------+

Additional resources
--------------------

You can download the most current versions of the `Rackspace API-related documents`_.

Email all support questions to cdn@rackspace.com.

Visit our `Product Feedback Forum`_ and tell us what you think about Rackspace CDN.

Follow Rackspace updates and announcements `on Twitter`_.

This API uses `standard HTTP 1.1 response codes`_.

.. _Rackspace API-related documents: http://docs.rackspace.com/api/

.. _Product Feedback Forum: https://feedback.rackspace.com/forums/298161-storage/category/107829-rackspace-cdn

.. _on Twitter: http://www.twitter.com/rackspace

.. _standard HTTP 1.1 response codes: http://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html

API contract changes
--------------------

Rackspace notifies customers in release notes when and if the contract changes.

Pricing and service level
-------------------------

Your use of Rackspace CDN is billed according to the pricing schedule on the Rackspace CDN page at `www.rackspace.com <http://www.rackspace.com/cloud/cdn-content-delivery-network>`_.

The Service Level Agreement (SLA) for Rackspace CDN is available at `Rackspace CDN SLA <http://www.rackspace.com/information/legal/service-level-guarantee-rackspace-cdn>`_.