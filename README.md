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

See the full [MicroStack documentation][microstack-docs].

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

To create an instance (called "awesome") based on the CirrOS image:

    microstack.launch cirros --name awesome

## SSH to an instance

The launch output will show you how to connect to the instance. For the CirrOS
image, the user account is 'cirros'.

    ssh -i ~/.ssh/id_microstack cirros@<ip-address>

## Horizon

The launch output will also provide information for the Horizon dashboard. Its
credentials are:

    username: admin
    password: keystone

## Customising and contributing

To customise services and settings, look in the `.d` directories under
`/var/snap/microstack/common/etc`. You can add services with your package
manager, or take a look at `CONTRIBUTING.md` and make a code based argument for
adding a service to the default list.

## Reporting a bug

Please report bugs to the [MicroStack][microstack] project on Launchpad.

<!-- LINKS -->

[microstack-docs]: https://microstack.run/docs/
[snap-build-badge]: https://build.snapcraft.io/badge/CanonicalLtd/microstack.svg
[snap-build-status]: https://build.snapcraft.io/user/CanonicalLtd/microstack
[microstack]: https://bugs.launchpad.net/microstack
