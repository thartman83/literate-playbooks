ANSIBLE= ansible-playbook
HOSTS= inventory/hosts.ini

.PHONY: tangle provision unprovision

tangle: README.org
	emacs $< --batch --eval '(org-babel-tangle-file "README.org")'

provision: tangle
	${ANSIBLE} -i ${HOSTS} provision-cert-manager.yml

unprovision: tangle
	${ANSIBLE} -i ${HOSTS} unprovision-cert-manager.yml
