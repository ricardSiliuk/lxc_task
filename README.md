# OxyLabs from scratch

## LXC

* *N.B.*: This setup will produce privileged containers
* run `apt update` to get up-to-date package listings (otherwise `lxc` won't show)
* install `lxc` by running `apt install lxc --install-recommends` (not sure about the flag, think it will be useful for network setup since it'll fetch `lxc-net` or smth)

### LXC Network setup

Paste following into `/etc/default/lxc-net` (file might not exist) (content lifted from LXC/SimpleBridge from Debian Wiki):

```ini
USE_LXC_BRIDGE="true"
LXC_BRIDGE="lxcbr0"
LXC_ADDR="10.0.3.1"
LXC_NETMASK="255.255.255.0"
LXC_NETWORK="10.0.3.0/24"
LXC_DHCP_RANGE="10.0.3.2,10.0.3.254"
LXC_DHCP_MAX="253"
LXC_DHCP_CONFILE=""
LXC_DOMAIN=""

LXC_IPV6_ADDR="fc27::216:3eff:fe00:1"
LXC_IPV6_MASK="64"
LXC_IPV6_NETWORK="fc27::/64"
LXC_IPV6_NAT="true"
```

Then, change `/etc/lxc/default.conf` network part from:

```ini
lxc.network.type = empty
```

to

```ini
lxc.net.0.type = veth
lxc.net.0.link = lxcbr0
lxc.net.0.flags = up
lxc.net.0.hwaddr = 00:16:3e:xx:xx:xx
```

Then, enable and start `lxc-net` service.

```bash
systemctl enable lxc-net
systemctl start lxc-net
```

## Ansible

* Follow this to install `Ansible` <https://docs.ansible.com/ansible/latest/installation_guide/intro_installation.html#installing-ansible-on-debian>
* To allow *Ansible* to manage `lxc`, install community plugin with `ansible-galaxy collection install community.general`
* Plugin requires python2-lxc bindings, so...
* `wget https://github.com/lxc/python2-lxc/archive/master.zip`
* `apt install unzip`
* `unzip master.zip`
* `apt install gcc python-dev lxc-dev
* `python setup.py install`

You can *now* move onto ansible stuff...

### Running a playbook

To execute a playbook, run:

`ansible-playbook PLAYBOOK_NAME`
