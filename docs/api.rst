.. currentmodule:: discord

API Reference
===============

The following section outlines the API of discord.py.


Client
-------

.. autoclass:: Client
    :members:

.. _discord-api-events:

Event Reference
~~~~~~~~~~~~~~~~

This page outlines the different types of events listened to by :meth:`Client.event`.


.. function:: on_ready()

    Called when the client is done preparing the data received from Discord. Usually after login is successful
    and the :attr:`Client.servers` and co. are filled up.

.. function:: on_message(message)

    Called when a message is created and sent to a server.

    :param message: A :class:`Message` of the current message.

.. function:: on_response(response)

    Called whenever a message is received from the websocket. Used mainly for debugging purposes.
    The parameter passed is raw data that was parsed via ``json.loads``.

    :param response: The received message response after gone through ``json.loads``.

.. function:: on_message_delete(message)
.. function:: on_message_edit(before, after)

    Called when a message is deleted or edited from any given server. If the message is not found in the
    :attr:`Client.messages` cache, then these events will not be called. This happens if the message
    is too old or the client is participating in high traffic servers. To fix this, increase
    the ``max_length`` option of :class:`Client`.

    :param message: A :class:`Message` of the deleted message.
    :param before: A :class:`Message` of the previous version of the message.
    :param after: A :class:`Message` of the current version of the message.

.. function:: on_status(server, user, status, game_id):

    Called whenever a user changes their status or game playing status.

    The status is usually either "idle", "online" or "offline".

    :param server: The :class:`Server` the user belongs to.
    :param user: The :class:`User` whose status changed.
    :param status: The new status of the user.
    :param game_id: The game ID that the user is playing. Can be None.


Data Classes
--------------

Some classes are just there to be data containers, this lists them. It should be assumed that *all* classes in this category are immutable and should not be modified.

.. autoclass:: User
    :members:

.. autoclass:: Message
    :members:

.. autoclass:: Server
    :members:

.. autoclass:: Channel
    :members:

.. autoclass:: PrivateChannel
    :members:

