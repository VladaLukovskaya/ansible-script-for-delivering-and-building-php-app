## Ansible playbook
What this project does: 
1. Checks whether the remote server (RS) has everything required installed. If not, install it. Make it with help from the geerlingguy's repo.
1. Delivers the docker-compose.yml to the RS.
3. Passes variables to the nginx.conf template. 
4. Adds condition of restarting nginx if the nginx.conf was changed. 
5. Runs the app. 


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

Run playbook script (inside the main dir):
```bash
ansible-playbook -i <path_to_inventory> playbook.yml -bK
```
then type the password of the remote server's ansible user
