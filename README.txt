Place this repository in dev-vagrant folder (near Vagrant file)
Login to ansible machine (on DEV: 192.168.0.41:22 or 127.0.0.1:2222) with ansible_user (Qwerty12)

1. Initial installation
	a. > cd /vagrant/ansible-playbooks/1-initial-installation
	b. Install SSH keys on all hosts:
	   > ansible-playbook -i dev ssh-setup.yml --extra-vars "ansible_user=ansible_user ansible_password=Qwerty12"
	c. Install everything else:
	   > ansible-playbook -i dev site.yml
	d. Connection to bitbucket (https://confluence.atlassian.com/bitbucket/set-up-an-ssh-key-728138079.html):
	   - Logon bitbucket
	   - Click on the profile icon on the left-bottom
	   - Choose "Bitbucket settings"
	   - On the top near Settings choose "ECSO team"
	   - Click "SSH keys" and "Add key"
	   - Copy info from file ~/.ssh/rsa.pub from your ansible_server to bitbucket "Add key" window
	   

	   
2. Deployments (for local VMs)
	a. > cd /vagrant/ansible-playbooks/2-deployments
	b. Fill components versions in {environment}/group_vars/all file
	c. Run deploy.yml playbook, but first start ssh agent:
	   > eval $(ssh-agent -s)
	   > ssh-add ~/.ssh/id_rsa
	   > ansible-playbook -i dev deploy.yml   OR with tags: ansible-playbook -i dev deploy.yml --tags "deploy-db"



3. Cloud (WEB)
	a. > cd /vagrant/ansible-playbooks/3-cloud
	b. Fill components versions in prod/group_vars/all file
	c. Run deploy.yml playbook, but first start ssh agent:
	   > eval $(ssh-agent -s)
	   > ssh-add ~/.ssh/id_rsa
	   > ansible-playbook -i prod deploy.yml





### Docker commands ###
sudo docker ps
sudo docker stop ID
sudo docker logs ID
sudo docker exec -it ID /bin/ash - open command line inside docker ALPINE
sudo docker system prune -a - remove stoped containers and unused images
