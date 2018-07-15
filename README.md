prerequisites:
ansible
python
pip install passlib

# ansible-user
creating multiple users using ansible in linux

Securely create multiple users with Ansible
This Python script and Ansible playbook help you to create several user accounts on different servers, give each user a secure password and force the user to change the password on first login.

The Ansible playbook users.yml demonstrates how to use the generated user dictionary.

Generate a list of user names and passwords
Use the provided Python script generate_user_passwords.py to generate a dictionary of user names and secure passwords. There are several ways to specify the user names.

User names as parameters
python generate_user_passwords.py test1 test2 test3 
User names from stdin
User names can be piped in from a file

python generate_user_passwords.py < users.txt

python generate_user_passwords.py <user>:<pass> <user>:<pass> <user>:<pass> | ansible-vault encrypt > user_passwords.yml

python generate_user_passwords.py <user> <user> <user> | ansible-vault encrypt > user_passwords.yml

ansible-vault view user_passwords.yml


use below command to execute playbook

ansible-playbook main.yml --ask-vault-pass
