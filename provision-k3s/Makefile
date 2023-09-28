ANSIBLE= ansible-playbook
HOSTS=inventory/hosts.ini
EMACS=emacs

.PHONY: provision k3s-controller k3s-workers helm loadbalancer tangle

tangle: README.org
	emacs $< --batch --eval '(org-babel-tangle-file "README.org")'

provision: tangle
	${ANSIBLE} -i ${HOSTS} provision-k3s.yml

k3s-controller: tangle
	${ANSIBLE} -i ${HOSTS} provision-k3s.yml --tags "k3s-controller"

k3s-workers: tangle
	${ANSIBLE} -i ${HOSTS} provision-k3s.yml --tags "k3s-workers"

helm: tangle
	${ANSIBLE} -i ${HOSTS} provision-k3s.yml --tags "helm"

loadbalancer: tangle
	${ANSIBLE} -i ${HOSTS} provision-k3s.yml --tags "loadbalancer"

unprovision: tangle
	${ANSIBLE} -i ${HOSTS} unprovision-k3s.yml
