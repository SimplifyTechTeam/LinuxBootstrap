# Bootstrapping Linux using Ansible pull

# Install Ansible
sudo apt update -y
sudo apt install software-properties-common -y
sudo add-apt-repository --yes --update ppa:ansible/ansible
sudo apt install ansible -y

## Only run if git changes
sudo ansible-pull -o -C ${checkout} -d ${directory} -i ${directory}/inventory -U ${url} 2>&1 | sudo tee -a ${logfile}

## run anyway
sudo ansible-pull -C ${checkout} -d ${directory} -i ${directory}/inventory -U ${url} 2>&1 | sudo tee -a ${logfile}


https://github.com/harrounmoussa/ansible-pull/blob/master/ansible_pull.yml