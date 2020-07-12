# ansible_public
Ansible playbooks and information I've made public

This is a work in progress and subject to change. 

In the inventory file you need to specify password hashes for the
ansible user and for your root user. You can create a password hash 
with the following : 

echo -n "<password to hash>" | openssl dgst -sha256

Alternatively you can use Ansible Vault. You can do your own research
on how to integrate Ansible vault

SSH Keys
Create a ssh key for ansible to use for deployment and specify in your
ansible config where to find the key. For most of my deployments I just
use Ansible.key and put it in the root of my ansible directory. The 
CORRECT way is to store it in Ansible Vault.

An example of the format to deploy would be: 

ansible-playbook -i inventory/collective_local setup_docker.yml

If you want to just deploy to a single server in your inventory file you can 
limit your playbook like this: 

ansible-playbook -i inventory/collective_local --limit <ip address or name in inventory file> setup_docker.yml

