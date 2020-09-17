Curated Feeds
=============

Threat Grid curates multiple feeds hourly and daily. These feeds are based on the files Threat Grid has analyzed in that
time frame.

Requirements
------------
There are two minimum required features for an integration with Threat Grid:

1. Ability to enter an API key
2. Ability to choose which feeds to pull

.. NOTE::

    There are two additional features that make for a more thorough integration with an improved workflow and user experience:

    1. Link to the indicator search in the Threat Grid portal
    2. Link to the sample in the Threat Grid portal the indicator came from


Example API Endpoints
---------------------

.. NOTE::

    To view the complete and up to date Threat Grid documentation and release notes head to the help page in the Threat Grid portal `here <https://panacea.threatgrid.com/mask/doc>`_.

Example Fetch of One Hourly Feed
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

.. http:example::

    GET https://panacea.threatgrid.com/api/v3/feeds/banking-dns.json&api_key=12345abcde HTTP/1.1

Example Fetch of One Daily Feed
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

.. http:example::

    GET https://panacea.threatgrid.com/api/v3/feeds/banking-dns_2016-07-14.json&api_key=12345abcde HTTP/1.1



