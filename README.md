# Create Slave

#### Prerequisites

* [Git](https://git-scm.com/download/)
* [Ansible](http://docs.ansible.com/ansible/latest/intro_installation.html)


#### Setup

* `git clone https://github.com/toddstoffel/galera_demo.git`
* cd to cloned folder
* edit inventory file with your own information
* `ansible-playbook -i inventory create_slave.yml`
