#Common-Dockerfiles

Ubuntu16.04 is required, optimized for China using aliyun based ubuntu source

## Ansible

2.1.1

## Provision DCOS

### references
* https://docs.mesosphere.com/1.7/administration/installing/custom/cli/    
* http://docs.ansible.com/ansible/faq.html#how-do-i-loop-over-a-list-of-hosts-in-a-group-inside-of-a-template

## Provision Docker Engine with Host

    cd ansible
    ansible-playbook -i playbooks/hosts/docker playbooks/docker.yml

## Provision Zookeeper

### usage

    cd ansible
    ansible-playbook -i playbooks/hosts/docker playbooks/docker.yml

### playbook: docker.yml

    - hosts: zookeeper
      sudo: yes
      roles:
        - zookeeper

### configure zookeeper hosts
    
    [zookeeper]
    <host_ip01> zookeeper_myid=1 zookeeper_servers=0.0.0.0,<host_ip02>,<host_ip03> ansible_ssh_user=<user> ansible_ssh_pass=<password>
    <host_ip02> zookeeper_myid=2 zookeeper_servers=<host_ip01>,0.0.0.0,<host_ip03> ansible_ssh_user=<user> ansible_ssh_pass=<password>
    <host_ip03> zookeeper_myid=3 zookeeper_servers=<host_ip01>,<host_ip02>,0.0.0.0 ansible_ssh_user=<user> ansible_ssh_pass=<password>
    
                           
### configure zookeeper ports(temp)
                           
    tasks/main.yml: deploy zookeeper       
                        
### references 
* http://docs.ansible.com/ansible/docker_module.html
* http://stackoverflow.com/questions/30940981/zookeeper-error-cannot-open-channel-to-x-at-election-address

## Trouble Shooting
* fix the prompt ssh key dialog: http://stackoverflow.com/questions/37690054/python-and-openssl-version-reference-issue-on-osx
                        