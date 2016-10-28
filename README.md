# This repository is being used for the purpose of David Tacheny's application process for NWEA
# The role inventory vault and site.yml have been designed and writen by David Tacheny

#Prerequisites
This challenge was tested with: 
Ansible 2.0.1.0
Python 2.7.12
  libselinux-python
  policycoreutils-python

#steps to execute
* git clone https://github.com/davidtacheny/nweatest.git 
* Decrypt the RSA Key from the root of this repository
	$ansible-vault decrypt vault/nwea 
* Run the Site Playbook to execute the challenge
	$ansible-playbook -i inventory/hosts site.yml --private-key vault/nwea
         pass = 

# Execution Host
Google Compute Engine
New base Centos 7 104.199.129.41 base image

# Directory Layout
This is the directory layout of this repository with explanation.

    site.yml                # the main playbook
    inventory/
            hosts           # inventory file for production 
    vault/
         nwea               # ansible-vault ecrypted file 
    
    roles/                  # All the information for the server roles
        nginx/              # nginx server role 
            tasks/
                main.yml    # playbook to execute the installation of nginx webserver / fix SELinux port 8888 / restart service
            templates/
                index.html  # The index.html that is close to the challenge request
                nginx.conf  # nginx.conf is the configuration file for the nginx webserver
            handlers          
                main.yml    # sets up the service handles in this case to start stop or restart nginx
           

