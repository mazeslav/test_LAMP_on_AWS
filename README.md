# test_LAMP_on_AWS
This repository contains test task to automate deployment of the standard LAMP stack for application into Amazon AWS.

The stack can be deployed using the following command:

ansible-playbook site.yml --tags=provision ansible-playbook site.yml --tags=configure

The deployment can be tested by following command (endpoint returns http response 200 with phpinfo data):

ansible-playbook site.yml --tags=test

For destroing infrastukture use next command):

ansible-playbook site.yml --tags=destroy

ansible-playbook site.yml --tags=provision ansible-playbook site.yml --tags=configure

The deployment can be tested by following command (endpoint returns http response 200 with phpinfo data):

ansible-playbook site.yml --tags=test

For destroing infrastukture use next command):

ansible-playbook site.yml --tags=destroy
