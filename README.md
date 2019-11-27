# microstack deployment Lab
MicroStack is a single-machine, snap-deployed OpenStack cloud.

Common purposes include:

* Development and testing of OpenStack workloads
* Continuous integration (CI)
* IoT and appliances
* Edge clouds (experimental)
* Introducing new users to OpenStack

Currently provided OpenStack services are: Nova, Keystone, Glance, Horizon, and
Neutron.

MicroStack is frequently updated to provide the latest stable updates of the
most recent OpenStack release.

> **Requirements**:
  You will need at least 2 CPUs, 8 GiB of memory, and 100 GiB of disk space.

 **Verify CPUs and Memory**:
 
    $ free -h
    
    $ grep -c ^processor /proc/cpuinfo

 **Configure Hostname**:
    
    $ sudo hostnamectl set-hostname  openstack-lab-XY.bdren.net.bd --static
    
    $ sudo reboot
    
    $hostname


## Installation

At this time you can install from the `--beta` or `--edge` snap channels:

    sudo snap install microstack --classic --beta

## Initialisation

Initialisation will set up databases, networks, flavors, an SSH keypair, a
CirrOS image, and open ICMP/SSH security groups:

    sudo microstack.init --auto

## OpenStack client

The OpenStack client is bundled as `microstack.openstack`. For example:

    microstack.openstack network list
    microstack.openstack flavor list
    microstack.openstack keypair list
    microstack.openstack image list
    microstack.openstack security group rule list

## Creating an instance

To create an instance (called "Test-VM") based on the CirrOS image:

    microstack.launch cirros --name Test-VM

## SSH to an instance

The launch output will show you how to connect to the instance. For the CirrOS
image, the user account is 'cirros'.

    ssh -i ~/.ssh/id_microstack cirros@<ip-address>

## Horizon

The launch output will also provide information for the Horizon dashboard. Its
credentials are:

    username: admin
    password: keystone

