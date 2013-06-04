.. python-shirka documentation master file, created by
   sphinx-quickstart on Tue Jun  4 23:53:33 2013.
   You can adapt this file completely to your liking, but it should at least
   contain the root `toctree` directive.

Welcome to python-shirka's documentation!
=========================================

Shirka is a **python** based **bot** heavily relying on **twisted**, it's mostly a python learning project.

The principle is quite simple, you have a **consumer** which is able to collect/send messages,
messages collected by the **consumer** are passed to **responders**, if a **responder** 'supports'
the **message**, it should send a message back to the **consumer**.

**input messages** can be referred to as **commands**.

.. code-block:: none

   +------------------------------------------------+
   |  messages  <--->  consumer  <--->  responders  |
   +------------------------------------------------+

Contents:

.. toctree::
   :maxdepth: 2

   install
   config
   start
   responders



Indices and tables
==================

* :ref:`genindex`
* :ref:`modindex`
* :ref:`search`

