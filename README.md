# ignite-ansible-demo
Palo Alto Address Object Management Using Ansible


This Git repository provides a demo of Palo Alto Address Object Management using Ansible.


## Prerequisites

To run this demo, one needs


* Ansible
* pandevice - Palo Alto Python Library
* dnspython - DNS Python library

If you have  Mac OS use the following steps

```
brew install python
easy_install pip
pip install virtualenv
virtualenv test_ansible
source test_ansible/bin/activate
pip install ansible xmltodict pandevice
```

Using  Linux the steps are similar. Here is an example using Centos7

```
yum install python-virtualenv
virtualenv test_ansible
source test_ansible/bin/activate
pip install ansible xmltodict pandevice

```
> Microsoft Windows does not currently support Ansible. Either use MacOS or any flavor of Debian or Red Hat.


## Example 1 - Adding Address Objects

Create an ``inventory.yml`` by copying the sample ``inventory.yml.sample`` and changing the IP address, username and password variables. These variables are ``ansible_host``, ``ansible_user`` and ``ansible_password`` respectively.

Run the playbook using the command
``ansible-playbook add_address_object.yml -e newhost=mynewhost``

> Ensure that the hostname specified in the ``newhost`` variable can be resolved by DNS.


## Example 2 - Address Group Management.

Using the inventory.yml created from Example 1,  run the following command to create and manage an address group.

```
ansible-playbook manage_address_groups.yml -e '{
    "addrlist": ["ad01", "ad02"],
    "addrgroup": "ldapservers"
    }'
```

The ``panos_object`` Ansible module has been modified to add the necessary functionality to make this demonstration work.
The ``addrlist`` is authoritative. So if a hostname is not listed in the ``addrlist`` but is present in the address group on the firewall,
that host will be removed from the static value host list on the firewall. The  ``panos_object`` as of Ansible 2.4 is additive. It only
adds new entries and is not able to delete existing addresses from an address group.

## LICENSE
MIT


