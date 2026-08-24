.. SPDX-License-Identifier: CC-BY-SA-4.0

.. _your-first-ubuntu-image:

Your first Ubuntu image
=======================

This tutorial will walk you through creating your first Ubuntu image
and launching it in a virtual machine.

Install dependencies
--------------------

.. prompt:: text $ auto

    $ sudo apt-get update
    $ sudo apt-get install git snapd qemu-user-static ubuntu-dev-tools
    $ sudo snap install --classic ubuntu-image

Clone the gadget repository
---------------------------

.. note::

    The ``main`` branch should contain a gadget targeting current Ubuntu **development release**.
    LTS branches like ``resolute`` and ``noble`` are available (add ``-b <branch>`` to the command below).

    If the target hardware does not support the RVA23 profile, ``noble`` is the only possible option,
    as ``resolute`` and above require RVA23.

.. prompt:: text $ auto

    $ git clone https://github.com/canonical/risc-v-gadget.git

Build the image
---------------

.. prompt:: text $ auto

    $ cd risc-v-gadget
    $ sudo ubuntu-image --workdir workdir --debug classic image-definition.yaml

Test the image
--------------

Navigate to the image and change the owner.

.. prompt:: text $ auto

    $ cd workdir
    $ sudo chown $USER ubuntu-*-preinstalled-server-riscv64.img

See :ref:`Install Ubuntu on QEMU (RISC-V) <qemu-riscv-edk2>`.
for the command to launch the virtual machine.

Login with user *ubuntu* and password *ubuntu*.

You will be asked to change the password.

Power off the virtual machine with

.. prompt:: text $ auto

    $ sudo poweroff
