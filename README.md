## Production ready ansible pull for linux setup baseline
## AC 23/09/23

# Setup ansible on node that will pull from git
# below example is from ubuntu
sudo apt update -y
sudo apt install software-properties-common -y
sudo add-apt-repository --yes --update ppa:ansible/ansible
sudo apt install ansible -y

# Run this once, it will pull playbook from main branch and setup crontab to sync every 10 mins if the repo changes
sudo ansible-pull -o -C main -d /var/ansible/linuxbootstrap -i /var/ansible/linuxbootstrap/inventory -U https://github.com/SimplifyTechTeam/LinuxBootstrap.git | sudo tee -a /var/log/ansible/linuxbootstrap/ansible-pull.log