================================
FogLAMP "Kafka" C++ North Plugin
================================

This is a simple FogLAMP north plugin for sending data to Apache Kafka.

FogLAMP acts as a Kafka producer, sending reading data to Kafka. This
implementation is a simplified producer that sends all data on a single
Kafka topic. Each message contains an asset name, timestamp and set of
readings values as a JSON document.

Copyright
---------

This plugin buils upon the open source librdkafka library and as such portions
of ths work are copyright Magnbus Edenhill.

librdkafka - Apache Kafka C driver library

Copyright (c) 2012-2018, Magnus Edenhill
All rights reserved.

Build
-----

The plugin is built on top of the librdkafka library. This must be downloaded, built
and installed before the plugin can be built.

.. code-block:: console

  $ git clone https://github.com/edenhill/librdkafka.git
  $ cd librdkafka
  $ ./configure
  $ make
  $ sudo make install

To build FogLAMP "Kafka" C++ north plugin:

.. code-block:: console

  $ mkdir build
  $ cd build
  $ cmake ..

- By default the FogLAMP develop package header files and libraries
  are expected to be located in /usr/include/foglamp and /usr/lib/foglamp
- If **FOGLAMP_ROOT** env var is set and no -D options are set,
  the header files and libraries paths are pulled from the ones under the
  FOGLAMP_ROOT directory.
  Please note that you must first run 'make' in the FOGLAMP_ROOT directory.

You may also pass one or more of the following options to cmake to override 
this default behaviour:

- **FOGLAMP_SRC** sets the path of a FogLAMP source tree
- **FOGLAMP_INCLUDE** sets the path to FogLAMP header files
- **FOGLAMP_LIB sets** the path to FogLAMP libraries
- **FOGLAMP_INSTALL** sets the installation path of Random plugin

NOTE:
 - The **FOGLAMP_INCLUDE** option should point to a location where all the FogLAMP 
   header files have been installed in a single directory.
 - The **FOGLAMP_LIB** option should point to a location where all the FogLAMP
   libraries have been installed in a single directory.
 - 'make install' target is defined only when **FOGLAMP_INSTALL** is set

Examples:

- no options

  $ cmake ..

- no options and FOGLAMP_ROOT set

  $ export FOGLAMP_ROOT=/some_foglamp_setup

  $ cmake ..

- set FOGLAMP_SRC

  $ cmake -DFOGLAMP_SRC=/home/source/develop/FogLAMP  ..

- set FOGLAMP_INCLUDE

  $ cmake -DFOGLAMP_INCLUDE=/dev-package/include ..
- set FOGLAMP_LIB

  $ cmake -DFOGLAMP_LIB=/home/dev/package/lib ..
- set FOGLAMP_INSTALL

  $ cmake -DFOGLAMP_INSTALL=/home/source/develop/FogLAMP ..

  $ cmake -DFOGLAMP_INSTALL=/usr/local/foglamp ..
