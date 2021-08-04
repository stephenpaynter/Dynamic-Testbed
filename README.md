# Generate a Cisco pyATS/Genie Testbed file from an Ansible inventory

Create pyATS/Genie testbed files from pre-configured Ansible Inventories. If you've already configured and created Ansible Inventory files then this code will allow you to pull all the required data from these files and populate the data into a pyATS/Genie Testbed file.

The code is used to save the time and duplication of having to create an Interactive Testbed when an already provisioned Ansible Inventory files exist.


## Installation

To install, simply clone this repository. No code dependancies are required, only a standard installation of Ansible and pyATS/Genie.


## Code Adjustments

The code contains certain criteria which will require adjusting.

- The __devices

```bash
ansible_ssh_pass
ansible_user
ansible_password
```

## Usage

If the above variables are not configured in your inventory files then manually edit the templates/testbed.j2 jinja2 template

Replace
```yaml
password: {{ hostvars[inventory_hostname]['ansible_password'] }}
```

With
```yaml
password: yourpassword
```

The same applies for ansible_user and ansible_ssh_pass.

## Defaults

Any inventory group can be targetted by changing the _devices variable, the example given targets the ansible group named "routers"

By default the Testbed file is created in the same folder as the playbook ran from, change this via entering the PWD in the dest: under the template module.
