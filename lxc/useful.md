# Useful commands

## Read individual config

`cat /var/lib/lxc/CONTAINER_NAME/config`

## Check what's running

`lxc-ls -f`

## Stop&Delete container

`lxc-stop CONTAINER_NAME && lxc-destroy CONTAINER_NAME`
