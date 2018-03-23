# ignite-ansible-demo
Palo Alto Address Object Management Using Ansible


This Git repository provides a demo of Palo Alto Address Object Management using Ansible.


## PreRequisites

To run this demo, one needs

* Ansible
* pandevice - Palo Alto Python Library
* dnspython - DNS Python library

On Mac OS use the following steps

```
brew install python

easy_install pip

pip install virtualenv

virtualenv test_ansible

source test_ansible/bin/activate

pip install ansible xmltodict pandevice

```

> Windows does not currently support Ansible. Either use MacOS or any flavor of Debian or Red Hat.
