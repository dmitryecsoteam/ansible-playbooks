Login to ansible machine (on DEV: 192.168.0.41) with ansible_user (Qwerty12)

1. Initial installation
	a. > cd /vagrant/ansible-playbooks/1-initial-installation
	b. Install SSH keys on all hosts:
	   > ansible-playbook -i dev/hosts/ ssh-setup.yml --extra-vars "ansible_user=ansible_user ansible_password=Qwerty12"
	b. 