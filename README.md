docker-centos-ssh-enabled
====================================================================

This is a Dockefile for CentOS container with SSH public key authentication enabled.

## Howto

1. ``git clone https://github.com/comutt/docker-centos-ssh-enabled.git``
1. ``cd docker-centos-ssh-enabled``
1. ``docker build -t ssh-enabled .``
1. ``CONTAINER_ID=$(docker run -P -d ssh-enabled) && SSH_PORT=$(docker port $CONTAINER_ID 22 | cut -d: -f2) && SSH_HOST=$(docker port $CONTAINER_ID 22 | cut -d: -f1);``
1. ``docker cp $CONTAINER_ID:/root/.ssh/id_rsa $CONTAINER_ID``
1. ``ssh -oUserKnownHostsFile=/dev/null -oStrictHostKeyChecking=no -i $CONTAINER_ID/id_rsa -p $SSH_PORT root@$SSH_HOST``
