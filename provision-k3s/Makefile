ANSIBLE= ansible-playbook
HOSTS=inventory/hosts.ini
CHECK=

.PHONY: provision k3s-controller k3s-workers helm loadbalancer longhorn cert-manager docker-registry tangle

tangle: README.org
	emacs $< --batch --eval '(org-babel-tangle-file "README.org")'

provision: tangle
	${ANSIBLE} -i ${HOSTS} provision-k3s.yml

k3s-controller: tangle
	${ANSIBLE} -i ${HOSTS} provision-k3s.yml --tags "k3s-controller" ${CHECK}

k3s-workers: tangle
	${ANSIBLE} -i ${HOSTS} provision-k3s.yml --tags "k3s-workers" ${CHECK}

helm: tangle
	${ANSIBLE} -i ${HOSTS} provision-k3s.yml --tags "helm" ${CHECK}

loadbalancer: tangle
	${ANSIBLE} -i ${HOSTS} provision-k3s.yml --tags "loadbalancer" ${CHECK}

longhorn: tangle
	${ANSIBLE} -i ${HOSTS} provision-k3s.yml --tags "longhorn" ${CHECK}

cert-manager: tangle
	${ANSIBLE} -i ${HOSTS} provision-k3s.yml --tags "cert-manager" ${CHECK}

docker-registry: tangle
	${ANSIBLE} -i ${HOSTS} provision-k3s.yml --tags "docker-registry" ${CHECK}

clean:
	${ANSIBLE} -i ${HOSTS} clean.yml
