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

Running the container setup will place your SSH key on those servers - don't forget to generate key beforehand.

If you recreate containers, ansible will freak out! You'll have to clear out `/root/.ssh/known_hosts` to proceed.

## Comments

Most templates, as they stand now, are not really templates, as they don't use any variables. Not sure whether that's common in Ansible...
