# Simple Ansible playbook for app (with nginx, php, mysql containers)

## Ansible playbook
What this playbook does step-by-step: 
1. Checks whether the remote server has everything required installed. If not, installs it. And it makes it all with help from the geerlingguy's repo.
1. Delivers the docker-compose.yml to the remote server.
3. Passes variables to the nginx.conf template. 
4. Adds condition of restarting nginx if the nginx.conf was changed. 
5. Runs the app. 

### Running the playbook
At first, set the IP address of the desired remote server in the inventory file instead of the 127.0.0.1

To run the playbook, use the following command (inside the main dir):
```bash
ansible-playbook -i <path_to_inventory> playbook.yml -bK
```
then type the password of the remote server's ansible user (should be created beforehand).


### Misc remarks and instructions

I assume that python is already installed on the remote server. 

MySQl server isn't connected to the php app, to connect to the mysql server:
```bash
mysql -h localhost -P 3306 --protocol=tcp -u root -p
```

To make MySQL work with the app, add required php code. 

Credentials are stored as plain text, not in the Ansible Vault.

Network is shared for all services.

To export and use tasks from git (requires ansible config and inventory files):
```bash
ansible-galaxy role install -r requirements.yml --force
```
