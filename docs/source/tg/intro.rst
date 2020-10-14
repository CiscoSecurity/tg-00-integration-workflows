Getting Started
===============

`Cisco Threat Grid API Docs <https://panacea.threatgrid.com/mask/doc/mask/api-getting-started>`_

A list of Threat Grid scripts can be found `here <https://github.com/CiscoSecurity/tg-01-basics>`_.

Threat Grid has four primary uses:

    1. Submitting samples for analysis
    2. Using the data
    3. Curated feeds
    4. Organization sample data.

Most tasks that can be completed within the Threat Grid UI can be performed using APIs.

Receiving an API Key
--------------------
The primary means of authentication is the Threat Grid API key. The ``api_key`` parameter identifies the user and authorizes
their access to the API.

1. Login into the Threat Grid `console <https://panacea.threatgrid.com/mask/>`_.
2. Click your username in the upper right corner and scroll down to API
3. Click show and copy your API Key
4. Under "Can Download Sample Content Via API" select ``True``

API Versions 2 and 3
____________________

.. NOTE::

    The main difference between api/v2 and api/v3 is that v2 is the original, and v3 is a newer,
    more modern generation of the Threat Grid APIs. However, api/v3 does not replace or supersede
    v2. Newer features are being added to api/v3 but api/v2 is still current. For example, api/v2
    includes submissions, and v3 includes account management. For more information, see the `API
    docs. <https://panacea.threatgrid.com/mask/doc/mask/api-getting-started>`_

