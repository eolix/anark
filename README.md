# Anark
Your own fully fledged email server + webmail + website

## Basic run
If you have plaintext password in `group_vars/all.yml -> mail_password`
ansible-playbook --private-key=~/.ssh/privkey.pem -i ./hosts 

## Vault-encrypted password, login as root
ansible-playbook -u root --private-key=~/.ssh/privkey.pem -i ./hosts --ask-vault-pass anark.yml