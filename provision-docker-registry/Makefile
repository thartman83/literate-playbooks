ANSIBLE= ansible-playbook
HOSTS= inventory/hosts.ini

.PHONY: tangle provision unprovision

tangle: README.org
	emacs $< --batch --eval '(org-babel-tangle-file "README.org")'

provision: tangle
	${ANSIBLE} -i ${HOSTS} provision-docker-registry.yml

unprovision: tangle
	${ANSIBLE} -i ${HOSTS} unprovision-docker-registry.yml
