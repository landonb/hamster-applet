#####################################
Building and Installing using ``waf``
#####################################

The Waf (meta) build system: https://waf.io/

Source code: https://github.com/waf-project/waf

History
=======

Hamster used to use ``autotools`` and now uses ``waf``.

Uninstalled Runnings
====================

To run hamster uninstalled, just use the ``-w`` switch:

.. code-block:: bash

    cd src
    ./hamster-applet -w

Install Hamster
===============

To install hamster using ``waf``:

.. code-block:: bash

    ./waf --prefix=/usr configure build
    sudo ./waf install

