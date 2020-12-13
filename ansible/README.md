# Ansible

Contents of folder:

* `lxc_containers.yml`
* `dante.yml`
* `squid.yml`

`lxc_containers.yml` will run on localhost to install containers.

Other two will only apply to their specific containers.

To execute a playbook, run:

`ansible-playbook PLAYBOOK_NAME -i inventory`

Inventory should match hostnames in `/etc/hosts`. Not sure how inventory management works in Ansible and at this rate I'm too hungry to ask :D
