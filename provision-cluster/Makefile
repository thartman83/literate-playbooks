ANSIBLE= ansible-playbook
HOSTS=inventory/hosts.ini

provision:
	${ANSIBLE} -i ${HOSTS} provision-cluster.yml

unprovision:
	${ANSIBLE} -i ${HOSTS} unprovision-cluster.yml
