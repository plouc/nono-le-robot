The startup file
================

Below, what your startup file (start.py) should look like

.. code-block:: python

    # vim: set fileencoding=utf-8 :

    import twistedhttpstream, yaml, sys, logging
    from twisted.internet import reactor
    import ioc

    logging.basicConfig(level=logging.DEBUG)

    container = ioc.build([
        'config.yml',
    ])

    if __name__ == "__main__":

        for flow in container.parameters.get('consumers'):
            if not container.has("consumer.%s.flowdock" % flow):
                continue

            twistedhttpstream.stream(
                container.get('ioc.extra.twisted.reactor'),
                "https://stream.flowdock.com/flows/%s/%s" % (container.parameters.get("flowdock.%s.organisation" % flow), flow),
                container.get("consumer.%s.flowdock" % flow),
                username=container.parameters.get("flowdock.user.token"),
                password=""
            )

        container.get('ioc.extra.twisted.reactor').run()


Launch shirka

.. code-block:: bash

    python start.py