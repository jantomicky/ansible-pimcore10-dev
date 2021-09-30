# Ansible: Pimcore 10 Development Server

Ansible playbook for setting up a **dev** server conforming to the [Pimcore 10 Requirements](https://pimcore.com/docs/pimcore/10.0/Development_Documentation/Installation_and_Upgrade/System_Requirements.html), on [Ubuntu Server 20.04 LTS (Focal Fossa)](https://releases.ubuntu.com/20.04/).

> Note: Do not store sensitive data on the managed node(s) as the **dev** server won't be properly secured & hardened.

## Instructions

1) Install dependencies (see `requirements.yml`) by running:

        ansible-galaxy install -r requirements.yml --roles-path ~/.ansible/roles

2) Create your `hosts` inventory file and configure your servers there:

        cp hosts.example hosts

    User server credentials, as well as default secrets, can be set in the hosts file, under `[webservers:vars]`.

3) Ping the node(s) to verify access:

        ansible -i hosts webservers -m ping

4) Run the playbook:

        ansible-playbook set_up.yml -i hosts --ask-become-pass

## Links

- https://docs.ansible.com/ansible/latest/user_guide/playbooks_intro.html
- https://docs.ansible.com/ansible/latest/user_guide/intro_inventory.html
