#Common-Dockerfiles

Ubuntu16.04 is required, optimized for China using aliyun based ubuntu source

## Provision Docker Engine with Host

    cd ansible
    ansible-playbook -i playbooks/hosts/docker playbooks/docker.yml

## Provision Rancher