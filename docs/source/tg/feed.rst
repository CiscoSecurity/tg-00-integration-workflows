Curated Feeds
=============

Threat Grid curates multiple feeds hourly and daily. These feeds are based on the files Threat Grid has analyzed in that
time frame. The feeds are only generated in the Threat Grid cloud and are available via the Threat Grid appliance.

Requirements
------------
There are three minimum required features for interacting with the feeds API endpoint in Threat Grid:

1. Ability to enter an API key
2. Ability to choose which feeds to pull

3. Ability to change the URI to allow for regional operability

    - Use https://panacea.threatgrid.com/cloud.json to get a list of current regional clouds

.. NOTE::

    There are two additional features that make for a more thorough integration with an improved workflow and user experience:

    1. Link to the indicator search in the Threat Grid portal
    2. Link to the sample in the Threat Grid portal the indicator came from


Example API Endpoints
---------------------

.. NOTE::

    For comprehensive documentation about Threat Grid Curated Feeds view the documentation `here <https://panacea.threatgrid.com/mask/doc/mask/feeds>`_ for details about the feeds API endpoint view the documentation `here <https://panacea.threatgrid.com/mask/api-doc-tree/api/v3/feeds>`_.


Example Fetch of Hourly Generate Feed for Banking Trojans
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

.. http:example::

    GET https://panacea.threatgrid.com/api/v3/feeds/banking-dns.json&api_key=12345abcde HTTP/1.1

Example response:

.. code-block:: JSON

    [
      {
        "description": "Banking Trojan Network Communications",
        "ips": [],
        "sample_md5": "e6b69a898a8fbf9b7f2036047bbe39e9",
        "sample": "https://panacea.threatgrid.com/feeds/banking-dns/samples/be3e9b5957855b54985523bc7dcf1e76",
        "sample_sha256": "1cd736904ce2a65a1d03a2996060ceb0b8bdab10209a91fc0a71ea248c1dd097",
        "info": "https://panacea.threatgrid.com/feeds/banking-dns/domains/ethhink.online",
        "domain": "ethhink.online",
        "sample_sha1": "c9508c22ab2b4ca8c9d2ddf7e05311c014abc9cd",
        "timestamp": "2020-10-16T13:45:15Z"
      },
      {
        "description": "Banking Trojan Network Communications",
        "ips": [],
        "sample_md5": "e6b69a898a8fbf9b7f2036047bbe39e9",
        "sample": "https://panacea.threatgrid.com/feeds/banking-dns/samples/be3e9b5957855b54985523bc7dcf1e76",
        "sample_sha256": "1cd736904ce2a65a1d03a2996060ceb0b8bdab10209a91fc0a71ea248c1dd097",
        "info": "https://panacea.threatgrid.com/feeds/banking-dns/domains/africadamx.com",
        "domain": "africadamx.com",
        "sample_sha1": "c9508c22ab2b4ca8c9d2ddf7e05311c014abc9cd",
        "timestamp": "2020-10-16T13:45:15Z"
      }
    ]

Example Fetch of Generate Feed From a Specific Date for Banking Trojans
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

.. http:example::

    GET https://panacea.threatgrid.com/api/v3/feeds/banking-dns_2016-07-14.json&api_key=12345abcde HTTP/1.1

Example response:

.. code-block:: JSON

    [
      {
        "description": "Banking Trojan Chthonic Network Communications",
        "ips": [],
        "sample_md5": "831098a9d8db43bebf3d6ee67914888d",
        "sample": "https://panacea.threatgrid.com/feeds/banking-dns/samples/b64457c8d42b084e8479f5e02809e1ad",
        "sample_sha256": "7581ed4dc11e62725b70f18fe63b47ab54cb29ea80aea0fbe7b6afb40e954ab7",
        "info": "https://panacea.threatgrid.com/feeds/banking-dns/domains/reportcollecsysdump.com",
        "domain": "reportcollecsysdump.com",
        "sample_sha1": "bc55679d74034d417910f16838839913931326ca",
        "timestamp": "2020-04-20T01:24:34Z"
      },
      {
        "description": "Banking Trojan Chthonic Network Communications",
        "ips": [],
        "sample_md5": "831098a9d8db43bebf3d6ee67914888d",
        "sample": "https://panacea.threatgrid.com/feeds/banking-dns/samples/b64457c8d42b084e8479f5e02809e1ad",
        "sample_sha256": "7581ed4dc11e62725b70f18fe63b47ab54cb29ea80aea0fbe7b6afb40e954ab7",
        "info": "https://panacea.threatgrid.com/feeds/banking-dns/domains/micagentudate14.com",
        "domain": "micagentudate14.com",
        "sample_sha1": "bc55679d74034d417910f16838839913931326ca",
        "timestamp": "2020-04-20T01:24:34Z"
      },
      {
        "description": "Banking Trojan Panda Network Communications",
        "ips": [],
        "sample_md5": "b365fcdd218728117da399eab0f953c5",
        "sample": "https://panacea.threatgrid.com/feeds/banking-dns/samples/277683b2e7a8c7a9e058de7f313952eb",
        "sample_sha256": "c8accd8740536c862a8cd32ceee85ecd5125b428a50cfa9b923db6c1f196fb72",
        "info": "https://panacea.threatgrid.com/feeds/banking-dns/domains/servidortrojan1233.ddns.net",
        "domain": "servidortrojan1233.ddns.net",
        "sample_sha1": "743152543424ab31593a7265d91818e519c819aa",
        "timestamp": "2020-04-20T04:27:15Z"
      },
      {
        "description": "Banking Trojan ShadesRAT Network Communications",
        "ips": [
          "78.159.131.121"
        ],
        "sample_md5": "fb749784a34504a9687b38375717c96b",
        "sample": "https://panacea.threatgrid.com/feeds/banking-dns/samples/4722c33924e4c6c9dd5c48fa495ab10d",
        "sample_sha256": "cda66cce7ac98baece36a58fe29c9b8afc4249d3b45bf15c7f64d4ac39ae1a4f",
        "info": "https://panacea.threatgrid.com/feeds/banking-dns/domains/gunner.no-ip.biz",
        "domain": "gunner.no-ip.biz",
        "sample_sha1": "002931dab485803bdfb16fcd18997c7daa238df2",
        "timestamp": "2020-04-20T16:18:16Z"
      }
    ]

