Querying Threat Grid
=====================

All of the IOCs (IPs, Domains, Mutexes, Hashes, File Paths, Registry Keys, etc...) Threat Grid generates from analysis
are indexed providing the ability to enrich and add context to IOCs from other systems.

Requirements
------------
There are two minimum required features for an integration with Threat Grid:

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

Querying for an IOC
^^^^^^^^^^^^^^^^^^^

Initial IOC searches should always be done using the Submission Search API. The scope of a search can be limited with
various parameters. ``org_only=True`` or ``user_only=True`` will limit the searches to just their organization’s or
user's samples respectively.

.. http:example::

    GET https://panacea.threatgrid.com/api/v2/search/submissions?state=succ&q=$IOC HTTP/1.1

Download Analysis Elements
^^^^^^^^^^^^^^^^^^^^^^^^^^

.. http:example::

    GET https://panacea.threatgrid.com/api/v2/samples/$ID/viedo.webm HTTP/1.1

.. http:example::

    GET https://panacea.threatgrid.com/api/v2/samples/$ID/analysis.json HTTP/1.1

.. http:example::

    GET https://panacea.threatgrid.com/api/v2/samples/$ID/processes.json HTTP/1.1

.. http:example::

    GET https://panacea.threatgrid.com/api/v2/samples/$ID/network.pcap HTTP/1.1

Access Specific Elements of analysis.json
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

.. http:example::

    GET https://panacea.threatgrid.com/api/v2/samples/$ID/analysis/iocs HTTP/1.1

.. http:example::

    GET https://panacea.threatgrid.com/api/v2/samples/$ID/analysis/network_streams HTTP/1.1

.. http:example::

    GET https://panacea.threatgrid.com/api/v2/samples/$ID/analysis/processes HTTP/1.1

.. http:example::

    GET https://panacea.threatgrid.com/api/v2/samples/$ID/analysis/annotations HTTP/1.1

Download Artifacts
^^^^^^^^^^^^^^^^^^

.. http:example::

    GET https://panacea.threatgrid.com/api/v2/artifacts/$SHA256/download HTTP/1.1



