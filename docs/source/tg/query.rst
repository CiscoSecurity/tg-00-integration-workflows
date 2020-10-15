Querying Threat Grid
=====================

All of the IOCs (IPs, Domains, Mutexes, Hashes, File Paths, Registry Keys, etc...) Threat Grid generates from analysis
are indexed providing the ability to enrich and add context to IOCs from other systems.

Requirements
------------
There are two minimum required features for an integration to query Threat Grid:

1. Ability to enter an API key
2. Ability to change the URI to allow for appliance operability

.. NOTE::

    There are two additional features that make for a more thorough integration with an improved workflow and user experience:

    1. Ability to query both cloud and appliance simultaneously
    2. Allow users to search the global dataset, their organizational dataset, and their individual dataset

Example API Endpoints
---------------------

.. NOTE::

    To view the complete and up to date Threat Grid documentation and release notes head to the help page in the Threat Grid portal `here <https://panacea.threatgrid.com/mask/doc>`_.

.. _Querying for an IOC:

Querying for an IOC
^^^^^^^^^^^^^^^^^^^

Initial IOC searches should always be done using the Submission Search API. The scope of a search can be limited with
various parameters. ``org_only=True`` or ``user_only=True`` will limit the searches to just their organization’s or
user's samples respectively. The following types can be queried.

1. Checksum
2. Path
3. URL
4. Registry Key
5. Domain
6. IP
7. IOC
8. Tag
9. Sample

.. http:example::

    GET https://panacea.threatgrid.com/api/v2/search/submissions?state=succ&q=$IOC&api_key=12345abcde HTTP/1.1

Download Analysis Elements
^^^^^^^^^^^^^^^^^^^^^^^^^^

.. http:example::

    GET https://panacea.threatgrid.com/api/v2/samples/$ID/viedo.webm&api_key=12345abcde HTTP/1.1

.. http:example::

    GET https://panacea.threatgrid.com/api/v2/samples/$ID/analysis.json&api_key=12345abcde HTTP/1.1

.. http:example::

    GET https://panacea.threatgrid.com/api/v2/samples/$ID/processes.json&api_key=12345abcde HTTP/1.1

.. http:example::

    GET https://panacea.threatgrid.com/api/v2/samples/$ID/network.pcap&api_key=12345abcde HTTP/1.1

Access Specific Elements of analysis.json
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

.. http:example::

    GET https://panacea.threatgrid.com/api/v2/samples/$ID/analysis/iocs&api_key=12345abcde HTTP/1.1

.. http:example::

    GET https://panacea.threatgrid.com/api/v2/samples/$ID/analysis/network_streams&api_key=12345abcde HTTP/1.1

.. http:example::

    GET https://panacea.threatgrid.com/api/v2/samples/$ID/analysis/processes&api_key=12345abcde HTTP/1.1

.. http:example::

    GET https://panacea.threatgrid.com/api/v2/samples/$ID/analysis/annotations&api_key=12345abcde HTTP/1.1

Download Artifacts
^^^^^^^^^^^^^^^^^^

.. http:example::

    GET https://panacea.threatgrid.com/api/v2/artifacts/$SHA256/download&api_key=12345abcde HTTP/1.1

Entity Searches
^^^^^^^^^^^^^^^

These calls enable searches for the existence of things such as "Does this domain exist in TG?".
They also enable the ability of searching basic relationships of things (domains that have resolved to this IP).

Search for Artifacts Based on Single-term Searches
""""""""""""""""""""""""""""""""""""""""""""""""""

.. http:example::

    GET https://panacea.threatgrid.com/api/v2/search/artifacts&api_key=12345abcde HTTP/1.1

Search for Domains Based on Single-term Searches
""""""""""""""""""""""""""""""""""""""""""""""""

.. http:example::

    GET https://panacea.threatgrid.com/api/v2/search/domains&api_key=12345abcde HTTP/1.1

Search for IPs Based on Single-term Searches
""""""""""""""""""""""""""""""""""""""""""""

.. http:example::

    GET https://panacea.threatgrid.com/api/v2/search/ips&api_key=12345abcde HTTP/1.1

Search for Paths Based on Single-term Searches
""""""""""""""""""""""""""""""""""""""""""""""

.. http:example::

    GET https://panacea.threatgrid.com/api/v2/search/paths&api_key=12345abcde HTTP/1.1

Search for Registry Keys Based on Single-term Searches
""""""""""""""""""""""""""""""""""""""""""""""""""""""

.. http:example::

    GET https://panacea.threatgrid.com/api/v2/search/registry_keys&api_key=12345abcde HTTP/1.1

Search for Samples Based on Single-term Searches
""""""""""""""""""""""""""""""""""""""""""""""""

.. http:example::

    GET https://panacea.threatgrid.com/api/v2/search/samples&api_key=12345abcde HTTP/1.1

Search for URLs Based on Single-term Searches
"""""""""""""""""""""""""""""""""""""""""""""

.. http:example::

    GET https://panacea.threatgrid.com/api/v2/search/urls&api_key=12345abcde HTTP/1.1

Search for Submission Records About Submitted Samples
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

.. http:example::

    GET https://panacea.threatgrid.com/api/v2/search/submissions&api_key=12345abcde HTTP/1.1

Advanced Search
^^^^^^^^^^^^^^^

.. NOTE::

    Advance search is currently not supported in the API, but the following steps explain how to successfully do this through the UI.

1. Navigate to this website https://panacea.threatgrid.com/mask/advanced_search
2. Click on ``API`` next to the ``Copy Query`` and ``Import Query`` fields

On-Demand Organization Metrics
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

When on the dashboard all of the tiles (Threat Scores, Total Submission by Threat Score, Total Convictions, etc...) have
an API link in the upper right that show how to get the info in that tile

Documentation for those endpoints is located `here <https://panacea.threatgrid.com/mask/api-doc/api/v3/aggregations/submissions>`_.

