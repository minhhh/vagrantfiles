# INSTALLATION
## Install Vagrant, VirtualBox and Ansible
* http://docs-v1.vagrantup.com/v1/docs/getting-started/
* http://docs.ansible.com/intro_installation.html

## Add precise64 box
```
vagrant box add precise64 http://files.vagrantup.com/precise64.box 
```

## Add plugin guest plugin

```
vagrant plugin install vagrant-vbguest
```

## Create box

    cd [our_chosen_path]
    mkdir precise64_box
    cd precise64_box
    vagrant init precise64

## Override the Vagrantfile with the Vagrant file in the repo

## Run vagrant up
    cd precise64_box
    vagrant up

## Create ansible host /etc/ansible/hosts and add this
    [webservers]
    192.168.33.10 ansible_ssh_port=22 ansible_ssh_host=192.168.33.10 ansible_ssh_user=vagrant

If you want to change `192.168.33.10` to another IP look into the `Vagrantfile` file

## Add vagrant ssh key to your session

    ssh-agent
    ssh-add ~/.vagrant.d/insecure_private_key

## Run ansible-playbook for basic software
    cd ansible-playbooks/precise64
    ansible-playbook basic.yml

## Using the box

    cd precise64_box
    vagrant ssh

    # In the guest
    cd /vagrant

## Sharing files between guest and host
Your vagrant folder (the one which contains `Vagrantfile` file) is automatically mounted to guest `/vagrant` folder

## Stopping the box

    vagrant halt

## Throw away the box

    vagrant destroy

## Add more default software to box
Add another folder for your software in `ansible-playbooks/precise64`

Then modify `ansible-playbooks/precise64/basic.yml` and add your own `yml` file.


