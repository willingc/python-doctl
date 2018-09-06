.. python-doctl documentation master file, created by
   sphinx-quickstart on Mon May 28 15:31:17 2018.
   You can adapt this file completely to your liking, but it should at least
   contain the root `toctree` directive.

.. python-doctl-docs:

python-doctl
============

`python-doctl`_, or more simply Python library ``doctl``, is a Python wrapper for the
excellent `doctl CLI <https://github.com/digitalocean/doctl>`_
command-line utility, from `Digital Ocean <https://digitalocean.com>`_.

----

This documentation exists to guide you through the usage of the library,
``doctl``, which is a Pythonic wrapper around the `doctl CLI`_ command-line
utility, for managing your `DigitalOcean <https://digitalocean.com/>`_ 
infrastructure.

Please enjoy!


.. _installation:

Installation
------------

.. note:: **Python prerequisites**

   - ``python-doctl`` requires a recent Python 3 version.
   - Install `Pipenv` for package management using the `Pipenv documentation`_.

First, ensure you have the `doctl CLI`_ command-line utility installed on your
system.

Then you can add ``python-doctl`` to your project with
`Pipenv <https://pipenv.org/>`_::

    $ pipenv install doctl


.. _python-doctl: https://pypi.org/project/doctl/
.. _doctl CLI: https://github.com/digitalocean/doctl
.. _Pipenv documentation: https://pipenv.readthedocs.io/en/latest/#install-pipenv-today


.. _usage:

Usage
-----

The ``DIGITALOCEAN_ACCESS_TOKEN`` environment variable will automatically be
honored::

    $ pipenv shell
    $ export DIGITALOCEAN_ACCESS_TOKEN=xxxx
    $ python

    >>> import doctl

    >>> for droplet in doctl.compute.droplet.list():
    ...     print(droplet['name'])
    pypi.kennethreitz.org
    code.kennethreitz.org
    build.kennethreitz.org
    …

    >>> for key in doctl.compute.ssh_key.list():
    ...     print(key['name'])
    Blink (iPad)
    thoth
    macbook

Alternatively, you can pass a token in explicitly::

    >>> from doctl import DigitalOcean
    >>> doctl = DigitalOcean(token="xxxxx")

Notes
+++++

Use of the ``DIGITALOCEAN_ACCESS_TOKEN`` environment variable is recommended.

Things to Know
++++++++++++++

- All reasonable ``doctl`` commands are available as methods within the
  ``doctl`` module. Sub–commands are referenced with another method call
  (e.g. ``doctl.compute.ssh_key.list()``.
- All methods return Python data structures, including timezone–aware 
  ``Datetime`` objects.


.. _namespaces:

Available Namespaces
--------------------

The entire API surface of ``doctl`` is covered by this library, so the following
namespaces are available for your use and enjoyment:

- ``compute.account``
- ``compute.action``
- ``compute.certificate``
- ``compute.domain``
- ``compute.domain_records``
- ``compute.droplet``
- ``compute.firewall``
- ``compute.floating_ip``
- ``compute.image``
- ``compute.image_action``
- ``compute.load_balancer``
- ``compute.plugin``
- ``compute.region_list``
- ``compute.size_list``
- ``compute.snapshot``
- ``compute.ssh_key``
- ``compute.tag``
- ``compute.volume``
- ``compute.volume_action``


.. _API-docs:

API Documentation
=================

.. _main-interfaces:

Main Interfaces
---------------

.. module:: doctl

The ``Compute`` class is the main interface to ``doctl``. A built in instance,
``doctl.compute`` is available at the module–level.


.. autoclass:: Compute
   :members:

This is also an `Account` class, for viewing your authentication information,
as well as your rate-limiting. A built in instance, ``doctl.account`` is
available at the module-level.

.. autoclass:: Account
    :members:


.. _low-level:

Low–Level Classes
-----------------

.. autoclass:: DigitalOcean
    :members:


.. _compute:

Compute Classes
---------------

.. autoclass:: ComputeAction
    :members:

.. autoclass:: ComputeCertificate
    :members:

.. autoclass:: ComputeDroplet
    :members:

.. autoclass:: ComputeDomain
    :members:

.. autoclass:: ComputeDomainRecords
    :members:

.. autoclass:: ComputeFirewall
    :members:

.. autoclass:: ComputeFloatingIP
    :members:

.. autoclass:: ComputeFloatingIPAction
    :members:

.. autoclass:: ComputeImage
    :members:

.. autoclass:: ComputeImageAction
    :members:

.. autoclass:: ComputeLoadBalancer
    :members:

.. autoclass:: ComputePlugin
    :members:

.. autoclass:: ComputeSnapshot
    :members:

.. autoclass:: ComputeSSHKey
    :members:

.. autoclass:: ComputeTag
    :members:

.. autoclass:: ComputeVolume
    :members:

.. autoclass:: ComputeVolumeAction
    :members:

Indices and tables
==================

* :ref:`genindex`
* :ref:`modindex`
* :ref:`search`

