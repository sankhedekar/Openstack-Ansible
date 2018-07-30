# Openstack-Ansible
Using OpenStack Ansible to create Network Topology

-------------------------------------------------------------------------------------------------------------

- Install Ansible:
• sudo yum install ansible
• sudo pip install shade

- Certain assumptions before working with ansible playbook:
• We already have an external network for our project called as “Public01”.
• We have default image which comes with the devstack installation called as “cirros”
• There are many flavors created already. I’m using the flavor called as “m1.micro”.

- Ansible files:
• clouds.yml
  clouds.yaml is a configuration file that contains everything needed to connect to one or more clouds.
  It looks for a file called clouds.yaml in the following locations:
  • current directory - Which we have created in the current directory.
  • ~/.config/openstack - Which is present in /etc/openstack/
  • /etc/openstack
  
• hosts
  Ansible works against multiple systems in the infrastructure at the same time. It does this by selecting portions of systems listed in Ansible’s inventory.

- It looks for a file called hosts in the following locations:
  • Directory mentioned in the command
  • /etc/ansible/hosts

- You can specify a different inventory file using the -i <path> option on the command line.
  • hosts - Which we have created in the current directory.
  • hosts - Which is present in /etc/ansible/
  
- Following command executes the topology playbook with ansible:
  • “-i” is used to specify a different inventory file.
  • “-vvv” is used for verbose mode (more details)
  • Network after running the play-book:
  • After running the play-book, it will create the following element:
  • Three networks will be created namely Private01, Private02, Private03.
  • A subnet in each network will be created namely Private01_Subnet, Private02_Subnet, Private03_Subnet.
  • A Router01 will be created which is connected to the Private01_Subnet, Private02_Subnet and the external network.
  • A Router02 will be created which is connected to the Private03_Subnet and the external network.
  • We have set the auto_ip parameter, which automatically assigns a floating IP to the instance.

