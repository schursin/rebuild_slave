# Automatic Replica Creation Utility For MariaDB 10.3+

## Description
This playbook will create a replication slave by using the [MariaBackup](https://mariadb.com/kb/en/library/mariabackup-overview/) tool.  It can be run from any machine that can access your database servers via SSH. It will launch the backup utility on your master and create a streaming snapshot of your data directory using [xbstream/mbstream](https://www.percona.com/doc/percona-xtrabackup/2.3/xbstream/xbstream.html).  It will then pass through the [pigz](https://zlib.net/pigz/) utility for additional compression before streaming over your network to your slave via the [socat](http://www.dest-unreach.org/socat/) utility.  On the target side, it will receive the file and decompress before preparing the backup, finding the GTID position, registering with the master and starting slave replication.

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
