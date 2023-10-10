## Production ready ansible pull for linux setup baseline
be careful pushing commits to this repo as it will effect live systems
ideally this is applied at boot to any clean linux system
further playbooks are required for additional customisations that deviate from what can be applied to all systems
for example the firewall will only allow ssh in this playbook 
this will automatically setup users and pull their ssh keys from the TeamSSHKeys repo based on username
add your username-a to the vars/user_var.yml and your account will be automatically added to all systems ready for ssh key based auth

# Requirements
run the below command to setup a node, the below example is for Ubuntu

sudo mkdir /var/log/ansible /var/log/ansible/linuxbootstrap && \
sudo apt update -y && \
sudo apt install software-properties-common -y && \
sudo add-apt-repository --yes --update ppa:ansible/ansible && \
sudo apt install ansible -y && \
sudo ansible-pull -o -C main -d /var/ansible/linuxbootstrap -i /var/ansible/linuxbootstrap/inventory -U https://github.com/SimplifyTechTeam/LinuxBootstrap.git | sudo tee -a /var/log/ansible/linuxbootstrap/ansible-pull.log

# Setup
complete the below commands, everything will be automated from there using a crontab
see detailed comments in the playbook for more information
sudo ansible-pull -o -C main -d /var/ansible/linuxbootstrap -i /var/ansible/linuxbootstrap/inventory -U https://github.com/SimplifyTechTeam/LinuxBootstrap.git | sudo tee -a /var/log/ansible/linuxbootstrap/ansible-pull.log

# diag
complete the below command if you want to do a manual pull
ansible-pull -C main -d /var/ansible/linuxbootstrap -i /var/ansible/linuxbootstrap/inventory -U https://github.com/SimplifyTechTeam/LinuxBootstrap.git | sudo tee -a /var/log/ansible/linuxbootstrap/ansible-pull.log

# onboarded systems
sbdsimzdb001
sbdsimzfe001
sbdsimzpr001
alcsimipam01