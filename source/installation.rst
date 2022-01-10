.. _pbm.installation:
.. _install:

Installing |pbm|
********************************************************************************

.. contents::
   :local:

|percona| provides and supports |pbm| installation packages for Debian, Ubuntu, Red Hat Enterprise Linux and derivative distributions. Find detailed information about supported Linux distributions on the `Percona Software and Platform Lifecycle <https://www.percona.com/services/policies/percona-software-platform-lifecycle#mongodb>`_ page.

You can install |pbm| from source code <source-code>` 

The following tools are at
your disposal after the installation completes:

===============  ===============================================================
Tool             Purpose
===============  ===============================================================
pbm              Command-line interface for controlling the backup system
pbm-agent        An agent for running backup/restore actions on a database host
pbm-speed-test   An interface for field-testing compression and backup upload 
                 speed
===============  ===============================================================

|

Install |pbm-agent| on every server that has ``mongod`` nodes in the
MongoDB cluster (or non-sharded replica set). You don't need to install |pbm-agent| on arbiter nodes since they don't have the data set.

You can install |pbm.app| CLI 
on any or all servers or desktop computers you wish to use it from, so long as
those computers aren't network-blocked from accessing the MongoDB cluster.


.. _source-code:

Building from source code
================================================================================

Building the project requires:

- Go 1.15 or above
- make
- git
- gcc
- ``krb5-devel`` for Red Hat Enterprise Linux / CentOS or ``libkrb5-dev`` for Debian / Ubuntu. This package is required for Kerberos authentication in Percona Server for MongoDB.

.. seealso::

   Installing and setting up Go tools
      https://golang.org/doc/install

To build the project (from the project dir):

.. code-block:: bash

   $ git clone https://github.com/percona/percona-backup-mongodb
   $ cd percona-backup-mongodb && git checkout pbm_2.0
   $ make build

After :program:`make` completes, you can find |pbm.app| and |pbm-agent| binaries
in the :dir:`./bin` directory:

.. code-block:: bash

   $ cd bin
   $ ./pbm version

By running :program:`pbm version`, you can verify if |pbm| has been built correctly and is ready for use.

.. admonition:: Output

   .. code-block:: bash

      Version:   [pbm version number]
      Platform:  linux/amd64
      GitCommit: [commit hash]
      GitBranch: pbm_2.0
      BuildTime: [time when this version was produced in UTC format]
      GoVersion: [Go version number]

.. tip::

   Instead of specifying the path to pbm binaries, you can add it to the PATH environment variable:

   .. code-block:: bash
   
      export PATH=/percona-backup-mongodb/bin:$PATH

See :ref:`initial-setup` for guidelines how to set up |PBM|.  


.. include:: .res/replace.txt
