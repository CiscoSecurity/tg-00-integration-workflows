Querying Threat Grid
=====================

All of the IOCs (IPs, Domains, Mutexes, Hashes, File Paths, Registry Keys, etc...) Threat Grid generates from analysis
are indexed providing the ability to enrich and add context to IOCs from other systems.

Requirements
------------
There are two minimum required features for an integration to query Threat Grid:

1. Ability to enter an API key

2. Ability to change the URI to allow for regional and `appliance operability <https://www.cisco.com/c/en/us/support/security/amp-threat-grid-appliances/products-installation-guides-list.html>`_.

    - Use https://panacea.threatgrid.com/cloud.json to get a list of current regional clouds

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

Initial IOC searches should always be done using the Submission Search API `/api/v2/search/submissions <https://panacea.threatgrid.com/mask/api-doc/api/v2/search/submissions>`_. The scope of a search can be limited with
various parameters. ``org_only=True`` or ``user_only=True`` will limit the searches to just their organization’s or
user's samples respectively. Examples of entities that can be queried for include:

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

    GET https://panacea.threatgrid.com/api/v2/search/submissions?state=succ&q=a92ddbbaf6c9a50a7125595a4119ca38&api_key=12345abcde HTTP/1.1

Example response:

.. code-block:: JSON

    {
        "api_version": 2,
        "id": 3209394,
        "data": {
            "index": 0,
            "total": 1,
            "took": 725,
            "timed_out": false,
            "items_per_page": 100,
            "current_item_count": 1,
            "items": [
                {
                    "matches": {},
                    "score": 1000000,
                    "item": {
                        "tags": [],
                        "vm_runtime": 300,
                        "md5": "a92ddbbaf6c9a50a7125595a4119ca38",
                        "private": false,
                        "organization_id": null,
                        "state": "succ",
                        "login": null,
                        "sha1": "2f9bc5c64eeca8c0504fd852032be29442f11ace",
                        "sample": "2163cc93b5daa51861397402eb94b6e3",
                        "filename": "sample.url",
                        "analysis": {
                            "behaviors": [
                                {
                                    "name": "network-file-downloaded-to-disk",
                                    "threat": 27,
                                    "title": "File Downloaded to Disk"
                                },
                                {
                                    "name": "js-uses-fromcharcode",
                                    "threat": 40,
                                    "title": "JavaScript Obfuscation Using \"fromCharCode()\" Function"
                                },
                                {
                                    "name": "script-contains-url",
                                    "threat": 60,
                                    "title": "Script Contains URL"
                                },
                                {
                                    "name": "network-communications-http-get-url",
                                    "threat": 6,
                                    "title": "Outbound HTTP GET Request From URL Submission"
                                },
                                {
                                    "name": "modified-file-in-user-dir",
                                    "threat": 56,
                                    "title": "Process Modified File in a User Directory"
                                },
                                {
                                    "name": "network-fast-flux-domain",
                                    "threat": 7,
                                    "title": "DNS Response Contains Low Time to Live (TTL) Value"
                                },
                                {
                                    "name": "artifact-flagged-anomaly",
                                    "threat": 48,
                                    "title": "Static Analysis Flagged Artifact As Anomalous"
                                },
                                {
                                    "name": "network-only-safe-domains-contacted",
                                    "threat": 19,
                                    "title": "Sample Communicates With Only Benign Domains"
                                }
                            ],
                            "threat_score": 60,
                            "metadata": {
                                "general_details": {
                                    "report_created": "2020-09-29T15:19:19Z",
                                    "sandbox_version": "pilot-d",
                                    "sandbox_id": "-"
                                },
                                "sandcastle_env": {
                                    "controlsubject": "-",
                                    "vm": "win7-x64",
                                    "vm_id": "2163cc93b5daa51861397402eb94b6e3",
                                    "sample_executed": 1601392400,
                                    "analysis_end": "2020-09-29T15:19:19Z",
                                    "analysis_features": [],
                                    "analysis_start": "2020-09-29T15:12:27Z",
                                    "display_name": "Windows 7 64-bit",
                                    "run_time": 300,
                                    "sandcastle": "-",
                                    "current_os": "7601.18798.amd64fre.win7sp1_gdr.150316-1654"
                                },
                                "analyzed_file": {
                                    "md5": "a92ddbbaf6c9a50a7125595a4119ca38",
                                    "filename": "sample.url",
                                    "sha1": "2f9bc5c64eeca8c0504fd852032be29442f11ace",
                                    "sha256": "76b523017eb04dc56b48e4c0585ded8746c11646238484e35710289e8a385af3",
                                    "size": 129,
                                    "type": "url",
                                    "magic": "MS Windows 95 Internet shortcut text (URL=<https://landmarkventuresvip.com/l/NbTVz2HLyCUHH4ohIiqMow/RpVmK9nmdTjwWh5CiY892daA/AUleeeldeOx76>), ASCII text"
                                },
                                "submitted_file": {
                                    "md5": "a92ddbbaf6c9a50a7125595a4119ca38",
                                    "filename": "sample.url",
                                    "sha1": "2f9bc5c64eeca8c0504fd852032be29442f11ace",
                                    "sha256": "76b523017eb04dc56b48e4c0585ded8746c11646238484e35710289e8a385af3",
                                    "size": 129,
                                    "type": "url",
                                    "magic": "MS Windows 95 Internet shortcut text (URL=<https://landmarkventuresvip.com/l/NbTVz2HLyCUHH4ohIiqMow/RpVmK9nmdTjwWh5CiY892daA/AUleeeldeOx76>), ASCII text"
                                },
                                "malware_desc": [
                                    {
                                        "md5": "a92ddbbaf6c9a50a7125595a4119ca38",
                                        "filename": "sample.url",
                                        "sha1": "2f9bc5c64eeca8c0504fd852032be29442f11ace",
                                        "sha256": "76b523017eb04dc56b48e4c0585ded8746c11646238484e35710289e8a385af3",
                                        "size": 129,
                                        "type": "url",
                                        "magic": "MS Windows 95 Internet shortcut text (URL=<https://landmarkventuresvip.com/l/NbTVz2HLyCUHH4ohIiqMow/RpVmK9nmdTjwWh5CiY892daA/AUleeeldeOx76>), ASCII text"
                                    }
                                ]
                            }
                        },
                        "status": "job_done",
                        "submitted_at": "2020-09-29T15:12:27Z",
                        "sha256": "76b523017eb04dc56b48e4c0585ded8746c11646238484e35710289e8a385af3"
                    }
                }
            ]
        }
    }

Download Analysis Elements
^^^^^^^^^^^^^^^^^^^^^^^^^^

You may want to retrieve detailed analysis results for the samples returned in the query.

Runtime Video
"""""""""""""

.. http:example::

    GET https://panacea.threatgrid.com/api/v2/samples/$ID/viedo.webm&api_key=12345abcde HTTP/1.1

Analysis JSON
"""""""""""""

.. http:example::

    GET https://panacea.threatgrid.com/api/v2/samples/$ID/analysis.json&api_key=12345abcde HTTP/1.1

Process Timeline JSON
"""""""""""""""""""""

.. http:example::

    GET https://panacea.threatgrid.com/api/v2/samples/$ID/processes.json&api_key=12345abcde HTTP/1.1

Network PCAP
""""""""""""

.. http:example::

    GET https://panacea.threatgrid.com/api/v2/samples/$ID/network.pcap&api_key=12345abcde HTTP/1.1

Access Specific Elements of analysis.json
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Instead of fetching analysis.json in its entirety you can query for individual sections from a given sample:

Behavioral Indicators
"""""""""""""""""""""

.. http:example::

    GET https://panacea.threatgrid.com/api/v2/samples/$ID/analysis/iocs&api_key=12345abcde HTTP/1.1

Network Streams
"""""""""""""""

.. http:example::

    GET https://panacea.threatgrid.com/api/v2/samples/$ID/analysis/network_streams&api_key=12345abcde HTTP/1.1

Processes
"""""""""

.. http:example::

    GET https://panacea.threatgrid.com/api/v2/samples/$ID/analysis/processes&api_key=12345abcde HTTP/1.1

Annotations
"""""""""""

.. http:example::

    GET https://panacea.threatgrid.com/api/v2/samples/$ID/analysis/annotations&api_key=12345abcde HTTP/1.1

Entity Searches
^^^^^^^^^^^^^^^

These calls enable searches for the existence of things such as “Does this domain exist in TG?”. They also enable the
ability of searching basic relationships between entities (domains that have resolved to this IP). A comprehensive list
of entity searches can be found in the `API documentation <https://panacea.threatgrid.com/mask/api-doc-tree/api/v2/search>`_.
See the search in the UI for detailed examples for each query: https://panacea.threatgrid.com/mask/search

IPs Threat Grid Has Observed a Domain Resolving To
"""""""""""""""""""""""""""""""""""""""""""""""""""

.. http:example::

    GET https://panacea.threatgrid.com/api/v2/search/ips?query=cisco.com&term=domain&api_key=12345abcde HTTP/1.1

Example Response:

.. code-block:: JSON

    {
        "api_version": 2,
        "id": 8531444,
        "data": {
            "index": 0,
            "items_per_page": 100,
            "current_item_count": 1,
            "items": [
                {
                    "result": "72.163.4.185",
                    "details": "/api/v2/ips/72.163.4.185"
                }
            ]
        }
    }

Domains Threat Grid Has Observed Resolving to an IP
"""""""""""""""""""""""""""""""""""""""""""""""""""

.. http:example::

    GET https://panacea.threatgrid.com/api/v2/search/domains?query=72.163.4.185&term=ip&api_key=12345abcde HTTP/1.1

Example Response:

.. code-block:: JSON

    {
        "api_version": 2,
        "id": 9288081,
        "data": {
            "index": 0,
            "items_per_page": 1000,
            "current_item_count": 1,
            "items": [
                {
                    "result": "cisco.com",
                    "details": "/api/v2/domains/cisco.com"
                }
            ]
        }
    }

Existence of a File Artifact by MD5
""""""""""""""""""""""""""""""""""""""""""""

.. http:example::

    GET https://panacea.threatgrid.com/api/v2/search/artifacts?query=f2adb5f1cfa13fbce8dcc8f3087732d9&term=md5&api_key=12345abcde HTTP/1.1

Example Response:

.. code-block:: JSON

    {
        "api_version": 2,
        "id": 9293412,
        "data": {
            "index": 0,
            "items_per_page": 1000,
            "current_item_count": 1,
            "items": [
                {
                    "result": "a2ed6cb1653b0fa64b2f53aedaafa7ea98ff895cbaee1da32bbdba6ad80587aa",
                    "details": "/api/v2/artifacts/a2ed6cb1653b0fa64b2f53aedaafa7ea98ff895cbaee1da32bbdba6ad80587aa"
                }
            ]
        }
    }

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

