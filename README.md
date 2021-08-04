# Generate a Cisco pyATS/Genie Testbed file from an Ansible inventory

Create pyATS/Genie testbed files from pre-configured Ansible Inventories. If you've already configured and created Ansible Inventory files then this code will allow you to pull all the required data from these files and populate the data into a pyATS/Genie Testbed file.

## Use Case Description

The code is used to save the time and duplication of having to create an Interactive Testbed when an already provisioned Ansible Inventory files exist. The code uses an Ansible inventory group, flattens it to a list and runs a loop to populate a testbed file via a Jinja2 template.

## Installation

To install, simply clone this repository. No code dependancies are required, only a standard installation of Ansible and pyATS/Genie.


## Configuration

The code contains certain criteria which will require adjusting.

- The devices varible will require setting to target your chose inventory group. 
- The more complete the Ansible Inventory file is the less additional code adjusts will be required. The following fields within the Ansible Inventory are required for the code to function without any amends.

```bash
ansible_ssh_pass
ansible_user
ansible_password
ansible_network_os
```

- If the above fields do not exist they can be manually added within the /templates/testbed.j2 file. Simply remove the varible and replace with your chosen value.

For example if the ansible_password field is not configured and all your devices have the same password simple do the following.

Replace
```yaml
password: {{ hostvars[inventory_hostname]['ansible_password'] }}
```
With
```yaml
password: yourpassword
```

The same applies for other values. If you are using an encypted password ensure the encrypted value is surrounded by single quotes.

By default the Testbed file is created in the same folder as the playbook ran from, this can be changed via entering the PWD in the dest: under the template module in the PyatsTestbed.yml file.

## Usage

To run the code use the following command

```yaml
ansible-playbook PyatsTestbed.yml
```
