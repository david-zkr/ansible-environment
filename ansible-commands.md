# Ansible Commands

<br>

## Initial config (create "ansible" users, generate sshkeys and export to all machines)
### Users
> Creates user
````bash
ansible all -m user -a "state=present name=ansible password={{ 'init1234' | password_hash('sha512') }}" --user=root --ask-pass
````

> Checks if user exist
````bash
ansible all -m command -a "grep ansible /etc/passwd" --user=root --ask-pass
````

> Add 'ansible' users to sudoers
````bash
ansible all -m copy -a 'dest=/etc/sudoers.d/automation content="automation ALL=(ALL) NOPASSWD: ALL\n"' -u root --ask-pass
````

<br>

### SSHkey
> Generates sshkeys
````bash
ssh-keygen
````

> Copies pubkey to machines
````bash
ansible all -m authorized_key -a "user=ansible key=\"{{ lookup('file', '/home/ansible/.ssh/id_rsa.pub') }}\" state=present" --user=root --ask-pass
````

<br>

## Basic commands
> Execute a module in all machines
````bash
ansible all -m *module name* -a *arguments*
````

> Send an ICMP message to all machines
````bash
ansible all -m ping
````

<br>

## Most common modules
### Command
> Execute a command in 'webserver' group
````bash
ansible webserver -m command -a "cat /etc/passwd | grep -i ansible"
````

### Copy
> Create a file in 'dbserver' group
````bash
ansible dbserver -m copy -a 'dest=/home/ansible/hola.txt content="hola que tal"'
````

<br>

## Playbooks
### Commands
> Execute a playbook (verbose and test-mode)
````bash
ansible-playbook -vvv -C *playbook name*
````

> Executes a playbook
````bash
ansible-playbook *playbook name*
````

### Example of playbook
> Configure RHEL8disk repo
````yml
---
- name: Configure RHEL8 disk repo and hosts file
  hosts: all
  tasks:

  - name: Add hosts in /etc/hosts
    copy:
      src: /etc/hosts
      dest: /etc/hosts
      owner: root
      group: root
      mode: 0644

  - name: Add RHEL8 BaseOS disk as repository
    yum_repository:
      name: RHEL8diskBaseOS.repo
      baseurl: http://workstation.lab.example.com/BaseOS
      enabled: yes
      gpgcheck: no
      description: RHEL 8.3 Remote server repository BaseOS

  - name: Add RHEL8 AppStream disk as repository
    yum_repository:
      name: RHEL8diskAppStream.repo
      baseurl: http://workstation.lab.example.com/AppStream
      enabled: yes
      gpgcheck: no
      description: RHEL 8.3 Remote server repository AppStream
...

````
