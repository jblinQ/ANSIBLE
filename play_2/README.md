

ssh -i .ssh/my_key ubuntu@51.20.34.53

ssh-agent bash
ssh-add .ssh/my_key

ansible -m ping 'test-server'
ansible -m ping all
ansible -a 'test-server' all
ansible -m command -a 'uptime' 'test-server'

# to display the expected public key that matches the private
ssh-keygen -y -e -f my_key
# to display the public key and check if both match
cat my_key.pub


# some ansible commands
ansile-playbook nginx_installation.yml
ansile-playbook nginx_installation.yml --check
ansile-playbook nginx_installation.yml --syntax-check
ansile-playbook nginx_installation.yml --start-at-task "Start nginx"
ansile-playbook nginx_installation.yml --tags "install"
ansile-playbook nginx_installation.yml --skip-tags "start"
ansile-playbook -i inventory nginx_installation.yml


# to use the configuration file not in the playbook directory
ANSIBLE_CONFIG=/location_of_cfg/playbook.cfg ansible-playbook playbook.yml

# to modify config file on the command line
ANSIBLE_CONFIG=explicit ansible-playbook playbook.yml    OR
export ANSIBLE_GATHERIMG=explicit #then run ansible-playbook playbook.yml


ansible-config list  # list all configurations
ansible-config view  # shows the current config file
ansible-config dump  # shows the current settings+


  vars_files:
    - httpd.vars
    - mariadb.vars
    - packages.vars