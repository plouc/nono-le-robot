Consumers
=========


FlowdockConsumer
----------------

configuration
,,,,,,,,,,,,,

.. code-block:: yaml

    parameters:
        consumers: [test]
        bot.name: nono
        bot.email: no-reply@shirka.com

        # configure flow parameterstest
        flowdock.test.organisation: shirka
        flowdock.test.flow.name:    FLOW_NAME
        flowdock.test.flow.token:   FLOW_TOKEN
        flowdock.test.user.name:    rande
        flowdock.test.user.token:   USER_TOKEN

    services:
        # Configure the bot
        bot:
            class:     shirka.consumers.Bot
            arguments: [ '%bot.name%', '%bot.email%']

        # Configure shared responders
        responders.math:
            class: shirka.responders.mate.MathResponder

        # Configure Stream API Consumer with valid responders
        consumer.test.flowdock:
            class: shirka.consumers.FlowDockConsumer
            arguments:
                - '@shirka.bot'
                - "%flowdock.test.flow.token%"
                -
                    - '@responders.math'
                    - ...

                - '@flowdock.test'


StdioProtocol
-------------