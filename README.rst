################################
Django Channels Tutorial project
################################

=========
Main goal
=========

* Get familiar with Django Channels

================
Additional goals
================

* Start using RST for documentation (this file)
* Continue using docker and git

===========
Reflections
===========

* If commits have been pushed to remote, ``git commit --amend`` on them can be dangerous.
* ``docker-compose run ...`` creates new container. So changes in this (e.g. ``pip install X``) don't get to the "main" container that is run with ``docker-compose up``.
* Related to Channels:

    * Consumer instance is created per connected client
    * Consumer instances can talk to each other using ``channel_layer``

        * Channel layers require something like Redis as a backend (can be set up in settings file)

    * There are two main entities in Channels: channels and groups

        * Channel is like an id of a consumer that allows to manage interactions with other consumers
        * Group is collection of channels that allows easily share events.
        * Event is an activity that can be initiated by one of consumers and trigger specific action by other consumers.

    * Synchronous consumers are less performant.
    * Asynchronous consumers are more perfomant, especially when they don't deal with blocking functions. Calling blocking functions require using helpers from ``asgiref``.
