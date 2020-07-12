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
use Ansible.key and put it in the root of my ansible directory.I believe
the best practice is to store it in Ansible Vault, but follow your own 
judgement.

An example of the format to deploy would be: 

ansible-playbook -i inventory/collective_local deploy_container.yml

If you want to just deploy to a single server in your inventory file you can 
limit your playbook like this: 

ansible-playbook -i inventory/collective_local --limit <ip address or name in inventory file> deploy_container.yml

Docker Container - 

This playbook will deploy a container to whatever hosts you have specified
in the 'docker' inventory group. 

The playbook will prompt you for a name for your container and what container
image you wish to deploy. Look on Docker Hub if you need to find an image.

I have tested this with ghost:latest and ghost:alpine 

Will update when I add other playbooks. 

