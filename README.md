## Bootstrapping Linux using Ansible pull
## Will setup cron job on 10 min schedule for future runs

# Setup ansible on node that will pull from git
sudo apt update -y
sudo apt install software-properties-common -y
sudo add-apt-repository --yes --update ppa:ansible/ansible
sudo apt install ansible -y

# Only run if git changes, pull playbook from main branch
sudo ansible-pull -o -C main -d /var/ansible/linuxbootstrap -i /var/ansible/linuxbootstrap/inventory -U https://github.com/SimplifyTechTeam/LinuxBootstrap.git | sudo tee -a /var/log/ansible/linuxbootstrap/ansible-pull.log

# run regardless of changes, pull playbook from main branch
sudo ansible-pull -C main -d /var/ansible/linuxbootstrap -i /var/ansible/linuxbootstrap/inventory -U https://github.com/SimplifyTechTeam/LinuxBootstrap.git | sudo tee -a /var/log/ansible/linuxbootstrap/ansible-pull.log