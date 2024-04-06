### Wordpress Ansible and Vagrant

This repository contains a playbook for provisioning modern WordPress and vagrantfile for provisionning VM machine in VirtualBox. It's based on How to Install WordPress on AlmaLinux 8. The following is handled out of the box:

- User Setup (Mysql and user localy)
- SSH

The following software is installed :

- HTTPD
- PHP and dependencies
- Pytohn3
- Mysql Server
- Wordpress

### Configuration

Before running the vagrant file, follow the following instructions:

1 - Run the Vagrantfile SRV-01 FIRST! with `vagrant up` then log in as root and copy the contents /home/osadmin/.ssh/id_rsa.pub.

2 - Open the Vagrantfile SRV-WEB-01 then paste the contents in the echo quotes "PUB_KEY" line 15 and save. Finally launch the vagrantfile with `vagrant up`

3 - Log in as osadmin in SRV-01 with password of "Password" and go to the /etc/ansible/ folder and modify the hosts file like this:

```bash
[linux-client]
`IP SRV-WEB-01` ansible_become=true ansible_become_pass=Password
```

Then run the command :

```bash 
ansible-playbook -v playbook_deploy_wordpress.yml
```

4 - Open your browser go to http://ip_SRV-WEB-01/wordpress