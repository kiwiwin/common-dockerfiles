#Common-Dockerfiles

Ubuntu16.04 is required, optimized for China using aliyun based ubuntu source

## Ansible

2.1.1

## Provision Docker Engine with Host

    cd ansible
    ansible-playbook -i playbooks/hosts/docker playbooks/docker.yml

## Provision Zookeeper

    cd ansible
    ansible-playbook -i playbooks/hosts/docker playbooks/docker.yml

### configure hosts
   
    <host_name or host_ip> myid=<zookeeper_myid> ansible_ssh_user=<user> ansible_ssh_pass=<password>

### playbook: docker.yml

    - hosts: zookeeper
      sudo: yes
      roles:
        - zookeeper
      vars:
        servers: node-1,node-2,node-3
                           
### configure zookeeper ports(temp)
                           
    tasks/main.yml: deploy zookeeper                           