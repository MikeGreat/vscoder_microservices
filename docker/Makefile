BIN_DIR?=~/bin
TEMP_DIR?=/tmp

# Environment name
ENV?=stage

# Application image version
IMAGE_VERSION?=1.0

# Docker-machine
DOCKER_MACHINE_VERSION?=v0.16.0
DOCKER_MACHINE_BASEURL=https://github.com/docker/machine/releases/download
DOCKER_MACHINE_OS?=$(shell uname -s)
DOCKER_MACHINE_ARCH?=$(shell uname -m)
DOCKER_MACHINE?=${BIN_DIR}/docker-machine
DOCKER_MACHINE_NAME?=docker-host
DOCKER_MACHINE_TYPE?=n1-standard-1
DOCKER_MACHINE_REGION?=europe-west1-b

# Packer-related variables
PACKER_VERSION?=1.4.4
PACKER_URL=https://releases.hashicorp.com/packer/${PACKER_VERSION}/packer_${PACKER_VERSION}_linux_amd64.zip
PACKER?=${BIN_DIR}/packer

# Ansible-related variables
## Relative to ./ansible subdir
ANSIBLE?=../../.venv/bin/ansible

# Terraform-related variables
TERRAFORM_VERSION?=0.12.12
TERRAFORM_URL=https://releases.hashicorp.com/terraform/${TERRAFORM_VERSION}/terraform_${TERRAFORM_VERSION}_linux_amd64.zip
TERRAFORM?=${BIN_DIR}/terraform

# Tflint-related variables
TFLINT_VERSION?=0.12.1
TFLINT_URL=https://github.com/wata727/tflint/releases/download/v${TFLINT_VERSION}/tflint_linux_amd64.zip
TFLINT?=${BIN_DIR}/tflint

# Hadolint-related variables
HADOLINT_VERSION?=1.17.2
HADOLINT_URL=https://github.com/hadolint/hadolint/releases/download/v${HADOLINT_VERSION}/hadolint-Linux-x86_64
HADOLINT?=${BIN_DIR}/hadolint

debug:
	echo BIN_DIR=${BIN_DIR}
	echo TEMP_DIR=${TEMP_DIR}
	echo DOCKER_MACHINE_VERSION=${DOCKER_MACHINE_VERSION}
	echo DOCKER_MACHINE_BASEURL=${DOCKER_MACHINE_BASEURL}
	echo DOCKER_MACHINE_OS=${DOCKER_MACHINE_OS}
	echo DOCKER_MACHINE_ARCH=${DOCKER_MACHINE_ARCH}
	echo DOCKER_MACHINE=${DOCKER_MACHINE}
	echo DOCKER_MACHINE_NAME=${DOCKER_MACHINE_NAME}
	echo DOCKER_MACHINE_TYPE=${DOCKER_MACHINE_TYPE}
	echo DOCKER_MACHINE_REGION=${DOCKER_MACHINE_REGION}

install_requirements:
	test -d ./.venv || python3 -m venv ./.venv
	./.venv/bin/pip install -r ../requirements.txt

install_requirements_dev: install_requirements
	./.venv/bin/pip install -r ../requirements-dev.txt

install_requirements_virtualenv:
	test -d ./.venv || virtualenv ./.venv
	./.venv/bin/pip install -r ../requirements.txt

install_docker_machine:
	curl -L ${DOCKER_MACHINE_BASEURL}/${DOCKER_MACHINE_VERSION}/docker-machine-${DOCKER_MACHINE_OS}-${DOCKER_MACHINE_ARCH} >${TEMP_DIR}/docker-machine && \
	mv ${TEMP_DIR}/docker-machine ${BIN_DIR}/docker-machine && \
	chmod +x ${BIN_DIR}/docker-machine

install_packer:
	wget ${PACKER_URL} -O ${TEMP_DIR}/packer-${PACKER_VERSION}.zip
	unzip -o ${TEMP_DIR}/packer-${PACKER_VERSION}.zip -d ${TEMP_DIR}/
	mv ${TEMP_DIR}/packer ${BIN_DIR}/packer-${PACKER_VERSION}
	ln -sf packer-${PACKER_VERSION} ${BIN_DIR}/packer
	${BIN_DIR}/packer --version && rm ${TEMP_DIR}/packer-${PACKER_VERSION}.zip

install_terraform:
	wget ${TERRAFORM_URL} -O ${TEMP_DIR}/terraform-${TERRAFORM_VERSION}.zip
	unzip -o ${TEMP_DIR}/terraform-${TERRAFORM_VERSION}.zip -d ${TEMP_DIR}/
	mv ${TEMP_DIR}/terraform ${BIN_DIR}/terraform-${TERRAFORM_VERSION}
	ln -sf terraform-${TERRAFORM_VERSION} ${BIN_DIR}/terraform
	${BIN_DIR}/terraform --version && rm ${TEMP_DIR}/terraform-${TERRAFORM_VERSION}.zip

install_tflint:
	wget ${TFLINT_URL} -O ${TEMP_DIR}/tflint-${TFLINT_VERSION}.zip
	unzip -o ${TEMP_DIR}/tflint-${TFLINT_VERSION}.zip -d ${TEMP_DIR}/
	mv ${TEMP_DIR}/tflint ${BIN_DIR}/tflint-${TFLINT_VERSION}
	ln -sf tflint-${TFLINT_VERSION} ${BIN_DIR}/tflint
	${BIN_DIR}/tflint --version && rm ${TEMP_DIR}/tflint-${TFLINT_VERSION}.zip

install_hadolint:
	wget ${HADOLINT_URL} -O ${TEMP_DIR}/hadolint-${HADOLINT_VERSION}
	mv ${TEMP_DIR}/hadolint-${HADOLINT_VERSION} ${BIN_DIR}/hadolint-${HADOLINT_VERSION}
	ln -sf hadolint-${HADOLINT_VERSION} ${BIN_DIR}/hadolint
	chmod +x ${BIN_DIR}/hadolint
	${BIN_DIR}/hadolint --version

docker_machine_create:
	. ./env && \
	${DOCKER_MACHINE} create --driver google \
		--google-machine-image https://www.googleapis.com/compute/v1/projects/ubuntu-os-cloud/global/images/family/ubuntu-1604-lts \
		--google-machine-type ${DOCKER_MACHINE_TYPE} \
		--google-zone ${DOCKER_MACHINE_REGION} \
		${DOCKER_MACHINE_NAME}
	${DOCKER_MACHINE} env ${DOCKER_MACHINE_NAME}

docker_machine_rm:
	${DOCKER_MACHINE} rm ${DOCKER_MACHINE_NAME}
	${DOCKER_MACHINE} env --unset


monolith_packer_build:
	${PACKER} build -var-file=docker-monolith/packer/variables.json docker-monolith/packer/docker.json

monolith_packer_validate:
	${PACKER} --version
	${PACKER} validate -var-file=docker-monolith/packer/variables.json docker-monolith/packer/docker.json


monolith_terraform_init:
	cd ./docker-monolith/terraform && ${TERRAFORM} init
	cd ./docker-monolith/terraform/${ENV} && ${TERRAFORM} init

monolith_terraform_init_nobackend:
	cd ./docker-monolith/terraform/${ENV} && ${TERRAFORM} init -backend=false

monolith_terraform_validate:
	${TERRAFORM} --version
	cd ./docker-monolith/terraform && ${TERRAFORM} validate
	cd ./docker-monolith/terraform/stage && ${TERRAFORM} validate
	# cd ./docker-monolith/terraform/prod && ${TERRAFORM} validate

monolith_terraform_tflint:
	cd ./docker-monolith/terraform && ${TFLINT}
	cd ./docker-monolith/terraform/stage && ${TFLINT}
	# cd ./docker-monolith/terraform/prod && ${TFLINT}

monolith_terraform_apply:
	cd ./docker-monolith/terraform/${ENV} && ${TERRAFORM} apply

monolith_terraform_destroy:
	cd ./docker-monolith/terraform/${ENV} && ${TERRAFORM} destroy


monolith_ansible_install_requirements:
	cd ./docker-monolith/ansible && ${ANSIBLE}-galaxy install -r environments/stage/requirements.yml

monolith_ansible_inventory_list:
	cd ./docker-monolith/ansible && ${ANSIBLE}-inventory --list

monolith_ansible_lint:
	cd ./docker-monolith/ansible && ${ANSIBLE}-lint --version
	cd ./docker-monolith/ansible && find playbooks -name "*.yml" -type f -print0 | xargs -0 -n1 ${ANSIBLE}-lint

monolith_ansible_syntax:
	cd ./docker-monolith/ansible && ${ANSIBLE}-playbook --version
	cd ./docker-monolith/ansible && find playbooks -name "*.yml" -type f -print0 | xargs -0 -n1 ${ANSIBLE}-playbook -i environments/stage/inventory.gcp.yml --syntax-check

monolith_ansible_reddit_app:
	cd ./docker-monolith/ansible && ${ANSIBLE}-playbook -i environments/${ENV}/inventory.gcp.yml playbooks/reddit-app.yml


monolith_docker_build:
	docker build -t reddit:latest -f docker-monolith/Dockerfile ./docker-monolith

monolith_docker_publish:
	echo Do not forget to login on docker hub `docker login`
	docker tag reddit:latest vscoder/otus-reddit:${IMAGE_VERSION}
	docker push vscoder/otus-reddit:${IMAGE_VERSION}
