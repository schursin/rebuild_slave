# Automatic Slave Creation Utility For MariaDB 10.3+

## Description
This playbook will create replication slave by using the [Mariabackup](https://mariadb.com/kb/en/library/mariabackup-overview/) utility.  It will launch the mariabackup utility on your master and create snapshot copy of your data directory by streaming it with xbstream/mbstream.  It will then pass through the lz4 utility for additional compression before streaming over your network to your slave via the socat utility.  On the target side, it will receive the file and decompress before preparing the backup, find the GTID position and registering with the master.

#### Prerequisites

* [Git](https://git-scm.com/download/)
* [Ansible](http://docs.ansible.com/ansible/latest/intro_installation.html)

#### Setup

* `git clone https://github.com/toddstoffel/rebuild_slave.git`
* cd to cloned folder
* edit inventory file with your own information
* `ansible-playbook -i inventory create_slave.yml`

#### Need Additional Help?

* Consulting: https://mariadb.com/services/consulting
