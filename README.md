# LinuxBootstrap
Bootstrapping Linux using Ansible pull

# Install ansible
sudo apt update -y
sudo apt install software-properties-common -y
sudo add-apt-repository --yes --update ppa:ansible/ansible
sudo apt install ansible -y

# configure with itself as a managed node
echo "[pull_mode_hosts]" | sudo tee -a /etc/ansible/hosts >/dev/null
hostname="$(hostname)" && echo $(hostname) | sudo tee -a /etc/ansible/hosts >/dev/null
cat /etc/ansible/hosts

# Manual test run
url='https://github.com/SimplifyTechTeam/LinuxBootstrap.git'      # URL of the playbook repository
checkout='main'                                                   # branch/tag/commit to checkout
directory='/var/projects/ansible-bootstrap'                       # directory to checkout repository to
logfile='/var/log/ansible-bootstrap.log'                          # where to put the logs

sudo ansible-pull -o -C ${checkout} -d ${directory} -i ${directory}/inventory -U ${url} 2>&1 | sudo tee -a ${logfile}


https://github.com/harrounmoussa/ansible-pull/blob/master/ansible_pull.yml