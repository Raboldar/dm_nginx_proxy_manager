# Deploy Nginx Proxy Manager

Deploy Nginx Proxy Manager via Ansible and Docker-Compose.

## Authentication
Use the following steps to generate a SSH key that will be used for the connection towards the target host.
The will be copied to the target host as a trusted user.

### Generate the SSH key
Execute the following command to generate the SSH key in your home folder.
```bash
ssh-keygen -o -a 100 -t ed25519 -f ~/.ssh/nginx_proxy_manager_host -C me@me.com
```

### Push the SSH key to the target host
Execute the following command to copy the SSH key from your home folder to the target machine.
The admin@192.168.1.1 corresponds to the [admin account on the target machine]@[IP of the target machine]
```bash
ssh-copy-id -i ~/.ssh/nginx_proxy_manager_host admin@192.168.1.1
```

## Variables
All the variables related to the host are found within the "inventory.yml" file.
ansible_user: defines the user that will be used to login, use the same as in the ssh-copy-id command.
ansible_host: defines the IP address of the target host, use the same IP as in the ssh-copy-id command.

## Executing the playbook
Enter the password used by the ansible_user for sudo.
```bash
ansible-playbook run.yml -K
```
