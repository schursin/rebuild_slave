# Automatic Replica Creation Utility For MariaDB 10.3+

## Description
This playbook will automatically rebuild and configure a replication slave.  It can be run from any host that can access your database servers via SSH.

On the **master**, it will:

1. Launch [MariaBackup](https://mariadb.com/kb/en/library/mariabackup-overview/).
1. Create a streaming snapshot of your data directory using [xbstream/mbstream](https://www.percona.com/doc/percona-xtrabackup/2.3/xbstream/xbstream.html).
1. Compress the stream with [pigz](https://zlib.net/pigz/).
1. Stream to the slave via [socat](http://www.dest-unreach.org/socat/).

On the **slave**, it will:
1. Receive the stream.
1. Decompress.
1. Prepare the backup.
1. Find the GTID position.
1. Register with the master.
1. Start slave replication.

#### Prerequisites

* [Ansible](http://docs.ansible.com/ansible/latest/intro_installation.html)
* Port **4444** must be open between your master and slave.

#### Setup

* `git clone https://github.com/toddstoffel/rebuild_slave.git`
* **cd** to cloned folder
* Edit the **inventory** file with your own information
* `ansible-playbook -i inventory create_slave.yml`

#### Need Additional Help?

* Consulting: https://mariadb.com/services/consulting
