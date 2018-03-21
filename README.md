# Ansible-manege-Remote-Windows

Step 1: Installing Ansible on Cent OS 7

Reference Ansible official web (http://docs.ansible.com/ansible/latest/intro_installation.html#latest-release-via-yum) and installing Ansible by yum.

After installing Ansible successfully, we can find out Ansible under path /etc/ansible/.

Step 2: Configuring Ansible and doing some simple tests

Opening /etc/ansible/hosts and editing it with following message:
[windows]
  windows.ip.address1
  windows.ip.address2
  
$ ansible all -m ping

Step 3: Installing pywinrm

$ pip install pywinrm

Please refer to https://github.com/diyan/pywinrm for more details

Step 4: Creating Inventory for remote Windows hosts

Creating a inventory /etc/ansible/group_vars/windows.yum with following content

all:
   hosts:
      windows:
         ansible_host: windows.ip.address1
         ansible_user: Administrator
         ansible_port: 9200
         ansible_password: changeit
         ansible_connection: winrm
ansible_winrm_server_cert_validation: ignore

(Note: the name of inventory must match with the group name specified in the /etc/ansible/hosts)

