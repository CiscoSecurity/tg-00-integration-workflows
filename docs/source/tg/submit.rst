Submitting Samples
==================
Samples (that are supported file types) can be submitted to Threat Grid either automatically or manually for analysis.

Requirements
------------
There are seven minimum required features for an integration with Threat Grid:

1. Ability to enter an API key

.. NOTE::

    To receive an API key go to the Threat Grid dashboard and click your username in the top right corner.
    Then click `My Account` and then `Generate API Key`.

2. Ability to change the URI to allow for appliance operability
3. Link back to the sample in the Threat Grid portal
4. Display the Threat Score for the sample
5. Render at a minimum the Behavioral Indicator count from the sample
6. Allow user to enter tags
7. Allow users to select privacy
8. Allow users to select VM

    - Use the `/api/v3/configuration/vms` to get a list of options to present to the user
9. Allow user to select playbook

    - Use the /api/v3/configuration/playbooks to get a list of options to present to the user
10. Allow user to select network simulation

    - Use the `/api/v3/configuration/network-exits` to get a list of options to present to the user
    - Use the network exits where the `simulation` is not `"none"`
11. Allow user to select network exit

    -  Use the `/api/v3/configuration/network-exits` to get a list of options to present to the user
12. Allow user to enter a password for password protected documents and archive submissions
13. Allow users to enable classification using the `classify` parameter

.. NOTE::

    There are seven additional features that make for a more thorough integration with an improved workflow and user experience:

    1. Glovebox Interaction
    2. Render / Parse full anlysis.json results
    3. Provide easily saved / copied list of IPs, Domains, Hashes, etc...
    4. Download artifacts,video,pcap
    5. Pull and display Rate-Limit informaiton
    6. Allow users to limit the number of daily submissions either by hard limit or % of rate limit
    7. Allow users to choose which filetypes are submitted

Automated Submission Requirements
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

1. Limit submissions to appropriate supported file types

    - Even though html and js files are supported, it often doesn't make sense for a system to automatically submit every html or js file it sees
2. Check if a file has been submitted in the organization within a configurable time window no less than 15 minutes and do not resubmit if it has

Automated Submission Requirements for Archives
""""""""""""""""""""""""""""""""""""""""""""""
1. Extract the contents of the archive and submit the appropriate supported file types individually

Example API Endpoints
---------------------

.. NOTE::

    To view the complete and up to date Threat Grid documentation and release notes head to the help page in the Threat Grid portal `here <https://panacea.threatgrid.com/mask/doc>`_.

Submitting a File
^^^^^^^^^^^^^^^^^

.. http:example::

    POST https://panacea.threatgrid.com/api/v2/samples&api_key=12345abcde HTTP/1.1

.. http:example::

    POST /api/v2/samples?api_key=12345abcde HTTP/1.1
    Content-Type: application/x-www-form-urlencoded
    Host: panacea.threatgrid.com
    Content-Disposition: form-data; name="sample"; filename="test_file.txt"
    Content-Disposition: form-data; name="network_exit"
    Content-Disposition: form-data; name="private"
    Content-Disposition: form-data; name="vm"

.. code-block:: bash

    curl -XPOST -F "sample=@readme.doc" -F api_key=MY_API_KEY
    https://panacea.threatgrid.com/api/v2/samples

Check State of a Sample
^^^^^^^^^^^^^^^^^^^^^^^

.. http:example::

    GET https://panacea.threatgrid.com/api/v2/samples/$ID/state&api_key=12345abcde HTTP/1.1

Check State of Multiple Samples (Recommended)
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

.. http:example::

    GET https://panacea.threatgrid.com/api/v2/samples/state&api_key=12345abcde HTTP/1.1

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

Download Artifacts
^^^^^^^^^^^^^^^^^^

.. http:example::

    GET https://panacea.threatgrid.com/api/v2/artifacts/$SHA256/download&api_key=12345abcde HTTP/1.1

Get Glovebox URI
^^^^^^^^^^^^^^^^

Via a feature called 'Glovebox' Threat Gird allows users to interact with samples while the VM they are being analyzed
in is running. The URI to the Glovebox environment can be loaded in an iFrame allowing users to interact with samples
from within your UI.

For this endpoint the URI is data.glovebox_url:

.. http:example::

    GET https://panacea.threatgrid.com/api/v2/samples/$ID&api_key=12345abcde HTTP/1.1

For this endpoint the URI is data.items[].glovebox_url

.. http:example::

    GET https://panacea.threatgrid.com/api/v2/samples?id=$ID&api_key=12345abcde HTTP/1.1


Rate Limit Information
----------------------

Threat Grid organizations have a limited number of submissions per 24 hour period. It may be useful to fetch this
information and render it in the UI so user can easily see how much of their limit remains. Doing this requires the
use of two API calls.

First:

.. http:example::

    GET https://panacea.threatgrid.com/api/v3/session/whoami&api_key=12345abcde HTTP/1.1

Store the value found at ``data.login`` and use it in the second API call.

Second:

.. http:example::

    GET https://panacea.threatgrid.com/api/v3/users/$login/rate-limit&api_key=12345abcde HTTP/1.1
