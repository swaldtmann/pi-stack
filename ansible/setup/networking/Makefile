# Makefile for ssh handling for ansible

.PHONY: keyscan copyid setup update


keyscan:
	grep ^[0-9] inventory | xargs /usr/bin/ssh-keyscan >> ~/.ssh/known_hosts
	

copyid:
	grep ^[0-9] inventory | xargs -I IP /usr/bin/ssh-copy-id -i ~/.ssh/id_rsa pi@IP

setup:
	ansible-playbook -i inventory main.yml

update:
	ansible pis -m apt -a "upgrade=yes update_cache=yes" -b
