## Before creating playbook
1. Create Dockerfile for the app.
2. Write docker-compose.yml file.
3. Create an nginx.conf template.


## Ansible playbook
What steps should be described in the ansible playbook: 
1. Check whether the remote server (RS) has Docker installed. If not, to install it. 
 1.5 Check whether python is installed on the remote server ?? And ansible as well or not?
 Check whether docker-compose installed? Turn them all on via the systemd module?
1. Deliver the Dockerfile and docker-compose.yml to the RS.
2. Build the app.
3. Pass variables to the nginx.conf template. 
4. Add condition of restarting nginx if the nginx.conf was changed. 
5. Run the app. 


### Misc instructions

Connect to the mysql server:
mysql -h localhost -P 3306 --protocol=tcp -u root -p

Credentials are stored as plain text, not in the vault !!
vault: ansible-vault create secrets.yaml, then define creds as (vault_mysql_password)