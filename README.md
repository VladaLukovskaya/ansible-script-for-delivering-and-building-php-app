## Before creating playbook
1. Create Dockerfile for the app.
2. Write docker-compose.yml file.
3. Create an nginx.conf template.


## Ansible playbook
What steps should be described in the ansible playbook: 
1. Check whether the remote server (RS) has Docker installed. If not, to install it. 
At first, I connect to
 Check whether docker-compose installed? Turn them all on via the systemd module?
1. Deliver the Dockerfile and docker-compose.yml to the RS.
2. Build the app.
3. Pass variables to the nginx.conf template. 
4. Add condition of restarting nginx if the nginx.conf was changed. 
5. Run the app. 


### Misc remarks and instructions

I assume that python is already installed on the remote server. 

Connect to the mysql server:
mysql -h localhost -P 3306 --protocol=tcp -u root -p

Credentials are stored as plain text, not in the vault !!
vault: ansible-vault create secrets.yaml, then define creds as (vault_mysql_password)
run: ansible-playbook playbook.yml --vault_pass_file=<path/name>

network is shared for all services

To export and use tasks from git:
ansible-galaxy role install -r requirements.yml --force (yozh did it)
or
ansible-galaxy install -r requirements.yml
or
ansible-galaxy install -r requirements.yml --roles-path roles/git