Login to ansible machine (on DEV: 192.168.0.41:22 or 127.0.0.1:2222) with ansible_user (Qwerty12)

1. Initial installation
	a. > cd /vagrant/ansible-playbooks/1-initial-installation
	b. Install SSH keys on all hosts:
	   > ansible-playbook -i dev ssh-setup.yml --extra-vars "ansible_user=ansible_user ansible_password=Qwerty12"
	c. Install everything else:
	   > ansible-playbook -i dev site.yml
	   
2. Deployments
	a. > cd /vagrant/ansible-playbooks/2-deployments
	b. Fill components versions in {environment}/group_vars/all file
	c. Run deploy.yml playbook:
	   > ansible-playbook -i dev deploy.yml