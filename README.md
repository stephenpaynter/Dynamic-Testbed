# Generate a Cisco pyATS/Genie Testbed file from an Ansible inventory

I use this code to create a pyATS/Genie testbed file from my Ansible Inventories. 

## Installation

To use this code, ensure that your inventory files are fully populated with the following

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
