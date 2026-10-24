APPLICATION DEPLOYMENT AUTOMATION USING ANSIBLE

PROJECT OVERVIEW
================

This project automates the deployment and configuration of the Sedre Application using Ansible.

FEATURES IMPLEMENTED
====================

1. User Creation
----------------

Creates users:

- sedreuser
- supportuser
- deployuser

Implemented using:

- user module
- loop

2. Directory Structure Creation
-------------------------------

Creates:

/opt/sedre

/opt/sedre/logs

/opt/sedre/backup

/opt/sedre/config

Implemented using:

- file module
- loop

3. Application Configuration Deployment
----------------------------------------

Deploys:

application.properties

using:

template module

4. Vault Integration
--------------------

Sensitive information stored securely using:

ansible-vault

Variables:

db_user

db_password

Loaded using:

vars_files

5. Health Check
---------------

Performs:

hostname check

uptime check

date check

using:

command
register
debug

6. Production Validation
------------------------

Displays deployment success message only on Production servers.

Condition used:

when: env == "prod"

7. Handler
----------

Restart handler is triggered only when configuration file changes.

Implemented using:

notify

handler

8. Tags
-------

Supported Tags:

user

directory

config

healthcheck

statuscheck

PROJECT STRUCTURE
=================

Application_Deployement_Project

│

├── inventory.ini

├── MainDeploy.yml

├── vault_secreate.yml

│

└── Application_Deployment

    ├── tasks

    │   └── main.yml

    │

    ├── handlers

    │   └── main.yml

    │

    ├── vars

    │   └── main.yml

    │

    ├── templates

    │   └── application.properties.j2

    │

    ├── defaults

    ├── meta

    └── tests

INVENTORY EXAMPLE
=================

[appserver]

172.31.x.x env=prod

[dbserver]

172.31.y.y env=preprod

USEFUL COMMANDS
===============

Verify Connectivity:

ansible all -i inventory.ini -m ping


Check Playbook Syntax:

ansible-playbook -i inventory.ini --syntax-check MainDeploy.yml --ask-vault-pass


List Tasks:

ansible-playbook -i inventory.ini MainDeploy.yml --list-tasks --ask-vault-pass


List Tags:

ansible-playbook -i inventory.ini MainDeploy.yml --list-tags --ask-vault-pass


Execute Full Deployment:

ansible-playbook -i inventory.ini MainDeploy.yml --ask-vault-pass


Execute Only User Creation:

ansible-playbook -i inventory.ini MainDeploy.yml --tags user --ask-vault-pass


Execute Only Directory Creation:

ansible-playbook -i inventory.ini MainDeploy.yml --tags directory --ask-vault-pass


Execute Only Configuration Deployment:

ansible-playbook -i inventory.ini MainDeploy.yml --tags config --ask-vault-pass


Execute Only Health Check:

ansible-playbook -i inventory.ini MainDeploy.yml --tags healthcheck --ask-vault-pass


Execute Only Production Validation:

ansible-playbook -i inventory.ini MainDeploy.yml --tags statuscheck --ask-vault-pass


VAULT COMMANDS
==============

Create Vault File:

ansible-vault create vault_secreate.yml


View Vault:

ansible-vault view vault_secreate.yml


Edit Vault:

ansible-vault edit vault_secreate.yml


Encrypt Existing File:

ansible-vault encrypt vault_secreate.yml


Decrypt Vault File:

ansible-vault decrypt vault_secreate.yml


ANSIBLE CONCEPTS DEMONSTRATED
=============================

Inventory

SSH Authentication

Playbooks

Roles

Variables

Inventory Variables

Vault Variables

Loops

Conditions

Templates

Jinja2

Handlers

Notify

Tags

Vault

Register

Debug

File Module

User Module

Idempotency

PROJECT OUTCOME
===============

This project demonstrates an end-to-end application deployment automation workflow using Ansible.

It covers all core Ansible concepts including:

Roles
Variables
Loops
Conditions
Templates
Handlers
Tags
Vault
Health Checks
Deployment Validation

This project simulates a real-world production deployment scenario.
