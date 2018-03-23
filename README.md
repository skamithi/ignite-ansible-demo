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
