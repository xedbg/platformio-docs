..  Copyright (c) 2014-present PlatformIO <contact@platformio.org>
    Licensed under the Apache License, Version 2.0 (the "License");
    you may not use this file except in compliance with the License.
    You may obtain a copy of the License at
       http://www.apache.org/licenses/LICENSE-2.0
    Unless required by applicable law or agreed to in writing, software
    distributed under the License is distributed on an "AS IS" BASIS,
    WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
    See the License for the specific language governing permissions and
    limitations under the License.

.. _cmd_test:

pio test
========

Helper command for local :ref:`unit_testing`.

.. contents::

Usage
-----

.. code-block:: bash

    pio test [OPTIONS]

Description
-----------

Run project tests on host (local) machine using PlatformIO :ref:`unit_testing`.

Options
-------

.. program:: pio test

.. option::
    -e, --environment

Process specified project environments.

.. option::
    -f, --filter

Process only the tests where the name matches specified patterns. More than one
pattern is allowed. If you need to filter some tests for a specific
environment, please take a look at :ref:`projectconf_test_filter` option from
:ref:`projectconf`.

.. list-table::
    :header-rows:  1

    * - Pattern
      - Meaning

    * - ``*``
      - matches everything

    * - ``?``
      - matches any single character

    * - ``[seq]``
      - matches any character in seq

    * - ``[!seq]``
      - matches any character not in seq

For example, ``pio test --filter "mytest*" -i "test[13]"``

.. option::
    -i, --ignore

Ignore tests where the name matches specified patterns. More than one
pattern is allowed. If you need to ignore some tests for a specific
environment, please take a look at :ref:`projectconf_test_ignore` option from
:ref:`projectconf`.

.. list-table::
    :header-rows:  1

    * - Pattern
      - Meaning

    * - ``*``
      - matches everything

    * - ``?``
      - matches any single character

    * - ``[seq]``
      - matches any character in seq

    * - ``[!seq]``
      - matches any character not in seq

For example, ``pio test --ignore "mytest*" -i "test[13]"``

.. option::
    --upload-port

A port that is intended for firmware uploading. To list available ports
please use the :ref:`cmd_device_list` command.

If the upload port is not specified, PlatformIO will try to detect it automatically.

.. option::
    --test-port

A Serial/UART port that PlatformIO uses as a communication interface between
PlatformIO Unit Test Engine and target device. To list available ports
please use :ref:`cmd_device_list` command.

If test port is not specified, PlatformIO will try to detect it automatically.

.. option::
    -d, --project-dir

Specify the path to the project directory. By default, ``--project-dir`` is equal
to a current working directory (``CWD``).

.. option::
    -c, --project-conf

Process project with a custom :ref:`projectconf`.

.. option::
    --without-building

Skip the building stage.

.. option::
    --without-uploading

Skip the uploading stage.

.. option::
    --without-testing

Skip the testing stage.

.. option::
    --no-reset

Disable software reset via ``Serial.DTR/RST`` before test running. In this case,
need to press the "reset" button manually after firmware uploading.

.. warning::
  If the board does not support software reset via ``Serial.DTR/RTS`` you
  should add >2 seconds delay before ``UNITY_BEGIN()``.
  We need that time to establish a ``Serial`` communication between the host
  machine and the target device. See :ref:`unit_testing`.

.. option::
    --monitor-rts

Set initial ``RTS`` line state for Serial Monitor (``0`` or ``1``),
default ``1``. We use it to gather test results via a Serial connection.

.. option::
    --monitor-dtr

Set initial ``DTR`` line state for Serial Monitor (``0`` or ``1``),
default ``1``. We use it to gather test results via a Serial connection.

.. option::
    --output-format

Generate unit testing report in the specified format.
The supported formats are:

* ``junit`` - `JUnit XML format <https://www.ibm.com/docs/en/developer-for-zos/14.1.0?topic=formats-junit-xml-format>`_
* ``json`` - `JSON format <https://en.wikipedia.org/wiki/JSON>`_.

.. option::
    --output-path

Save generated testing report to the specified path. If only a folder
path is provided, the file name will be generated automatically.
Please note that the parent folder must exist before.

.. option::
    -v, --verbose

Shows detailed information when processing environments.

Examples
--------

For the examples please follow to :ref:`unit_testing` page.
