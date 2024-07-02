## Before creating playbook
1. Create Dockerfile for the app.
2. Write docker-compose.yml file.
3. Create an nginx.conf template.


## Ansible playbook
What steps should be described in the ansible playbook: 
1. Check whether the remote server (RS) has Docker installed. If not, to install it. 
1. Deliver the Dockerfile and docker-compose.yml to the RS.
2. Build the app.
3. Pass variables to the nginx.conf template. 
4. Add condition of restarting nginx if the nginx.conf was changed. 
5. Run the app. 