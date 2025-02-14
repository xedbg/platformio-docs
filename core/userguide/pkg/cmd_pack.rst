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

.. _cmd_pkg_pack:

pio pkg pack
============

.. contents::

Usage
-----

.. code-block:: bash

    pio pkg pack [<source directory, tar.gz or zip>] [OPTIONS]

Description
-----------

Create a tarball from a package (library, :ref:`platforms`, or tool). If no arguments
are supplied, then platformio packs the current package folder.

A source of a package must contain a manifest (should be located in a root of a package)
depending on a package type:

:Library:
  A :ref:`library_json` is a manifest file of a library package.

:Platform:
  A ``platform.json`` is a manifest file of a development platform package. See :ref:`platform_creating_manifest_file`.

:Tool:
  A ``package.json`` is a manifest file of a tool package. It is intended for toolchains,
  flashers, debugging servers, simulators, and other tools.

See a `manifest validation scheme <https://github.com/platformio/platformio-core/blob/develop/platformio/package/manifest/schema.py>`_.

Options
-------

.. program:: pio pkg pack

.. option::
    -o, --output

Specify a destination path (folder or a full path to file) where to store a tarball.
The default is to create a tarball in the current working directory.

Files included in package
-------------------------

All files are included by default, with the following exceptions:

* Certain files that are relevant to package installation and distribution are always
  included. For example, ``library.json``, ``README.md``, ``LICENSE``, etc.
* If the :ref:`libjson_export` field is not declared in the manifest, the `next default filters <https://github.com/platformio/platformio-core/blob/develop/platformio/package/pack.py#L35>`__ will be applied
* If the :ref:`libjson_export` field is not declared in the manifest and there is a
  ``.gitignore`` file, then ignored files in that and all child directories will be
  excluded from the package.

See Also
--------

* :ref:`library_json`
* :ref:`cmd_pkg_publish`
