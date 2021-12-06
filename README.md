# Anark
Your own fully fledged secure email+web server and webmail, with SSL and AntiSpam with Ansible.

## Requirements
- VM/Server with at least 1 vCPU + 1GB RAM. Might function with less, do not recommend.
- Debian 7+ (tested up to 11). Might work with equivalent Ubuntu.
- Sudo / root access.
- Domain name 
- (optional) DNS access for DKIM/SPF TXT entries.

## Stack
- Unbound DNS
- MariaDB MySQL
- Postfix 
- Dovecot (with fancy sieve filters)
- Rspamd AntiSpam (integrated nicely with sieve filters for learning)
- Sogo Webmail (with fancier sieve filters)
- Nginx Web Server
- Certbot Letsencrypt SSL certs

## Usage
### Edit `group_vars/all.yml`
`mail_password` can be either plaintext or encrypted via `ansible-vault encrypt_string`

You don't need any `mail_aliases` if you don't want them.

### Edit `inventory`
Simply replace the single host under `[mailserver]` with your server's IP or FQDN.

## Running
If you have a plaintext password:

`ansible-playbook --private-key=~/.ssh/privkey.pem -i ./inventory anark.yml` 

If you _have encrypted your password as you should_ then:

`ansible-playbook --private-key=~/.ssh/privkey.pem -i ./inventory --ask-vault-pass anark.yml`

Specify your username (for example if you're logging in via `root`) by adding `-u root` to the string.

Your MariaDB passwords will be saved locally on the `secret/*_db_password` directory of this playbook.


## Future plans / name
The anarchic nature of the name means you'll be able to run all common third-party -rovided services on your own server, with open source software, on your own terms.

That means, in the future, you'll have:
- VPN server with OpenVPN (ready soon)
- Cloud storage (with Nextcloud)
- Photo library (likely with Photoprism)
- [Submit your own idea](https://github.com/eolix/anark/issues/new/choose)