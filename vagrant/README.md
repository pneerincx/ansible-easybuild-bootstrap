Local deployment with Vagrant
=============================

Tested with Vagrant 1.7.4.

This provides easy deployment on a local virtual machine using Vagrant. The
configuration is based on a
[CentOS 6.7 box](https://atlas.hashicorp.com/bento/boxes/centos-6.7).


Usage
-----

To get a machine up, run:

    vagrant up

If you just want to re-play the Ansible playbook, run:

    vagrant provision

You can SSH into the machine with:

    vagrant ssh

Running Ansible manually can be done like this:

    ANSIBLE_HOST_KEY_CHECKING=False ansible-playbook -i inventory playbook.yml

(Unfortunately, there seems to be no easier way to disable host key checking
for the Vagrant host only.)


Configuration
-------------

The machine configuration can be changed by setting the following environment
variables:

### `EASYBUILD_IP`

Default: 192.168.111.230

IP address of the virtual machine.

### `EASYBUILD_PORT_FORWARD_SSH`

Default: 2530

Local port forward for SSH (VM port 22).


Notes
-----

The `vagrant` user is added to the `easybuild` group, so it can install
packages with EasyBuild.
