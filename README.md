## Generate a Cisco pyATS/Genie Testbed file from an Ansible inventory

I use this basic code to create a pyATS/Genie testbed file from my Ansible Inventories. 
To use this code, ensure that your inventory files are fully populated with the following

ansible_ssh_pass<br/>
ansible_user<br/>
ansible_password<br/>

If they are not they will need to be added into the testbed.j2 template file.

ie if you are missing the ansible_password from your inventory then remove the following<br/>
{{ hostvars[inventory_hostname]['ansible_password'] }} and replace with your password without quotes etc

Any inventory group can be targetted by changing the devices variable, the example given targets the ansible group named "routers"

Testbed file is created in the same folder as the playbook ran from.

