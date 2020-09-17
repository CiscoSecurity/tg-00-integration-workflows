Organization Sample Data
========================

Customers may want data from all of their submissions to Threat Grid to be collected and stored for easy local analysis
or correlation.

Requirements
------------
There are two minimum required features for an integration with Threat Grid:

1. Ability to enter an API key
2. The ``org_only=True`` parameter must be set to prevent scraping the entire global dataset

.. NOTE::

    There is one additional feature that makes for a more thorough integration with an improved workflow and user experience:

    1. Generate stats based on the submitting user and time stamps


Example API Endpoints
---------------------

.. NOTE::

    To view the complete and up to date Threat Grid documentation and release notes head to the help page in the Threat Grid portal `here <https://panacea.threatgrid.com/mask/doc>`_.

.. Warning::

    Properly implementing this use case is non-obvious and requires the use of multiple API endpoints.

Fetch Organization Samples
^^^^^^^^^^^^^^^^^^^^^^^^^^

The first step is to fetch the organizations samples within the last hour and then parse the ``state`` of each Sample
ID, storing all Sample IDs that have ``state=run``. Do this at a maximum of every minute.

.. http:example::

    GET https://panacea.threatgrid.com/api/v2/samples?org_only=True&after=last_hour&api_key=12345abcde HTTP/1.1

Check for State Change of the Running Samples
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Check the state of the stored Sample IDs every 5 minutes. This can be done in bulk by passing a JSON list of Sample IDs
in the ``ids`` parameter. Once the state has changed to ``state=succ`` you can fetch the analysis results. Any sample
that changes to state other than ``succ`` can be logged or discarded.

.. http:example::

    GET https://panacea.threatgrid.com/api/v2/samples/state?ids=&api_key=12345abcde HTTP/1.1

Download Analysis Elements
^^^^^^^^^^^^^^^^^^^^^^^^^^

Once the samples have reached ``state=succ`` the analysis elements can be fetched to be parsed or stored.

.. http:example::

    GET https://panacea.threatgrid.com/api/v2/samples/$ID/viedo.webm&api_key=12345abcde HTTP/1.1

.. http:example::

    GET https://panacea.threatgrid.com/api/v2/samples/$ID/analysis.json&api_key=12345abcde HTTP/1.1

.. http:example::

    GET https://panacea.threatgrid.com/api/v2/samples/$ID/processes.json&api_key=12345abcde HTTP/1.1

.. http:example::

    GET https://panacea.threatgrid.com/api/v2/samples/$ID/network.pcap&api_key=12345abcde HTTP/1.1


