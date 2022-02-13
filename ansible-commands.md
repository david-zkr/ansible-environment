# Ansible Commands
### Initial config (creates "ansible" users)
<br>

> Creates user
````bash
ansible all -m user -a "state=present name=ansible password={{ 'init1234' | password_hash('sha512') }}" --user=root --ask-pass
````

> Checks if user exist
````bash
ansible all -m command -a "grep ansible /etc/passwd" --user=root --ask-pass
````

> Copies pubkey to machines
````bash
ansible all -m authorized_key -a "user=ansible key=\"{{ lookup('file', '/home/ansible/.ssh/id_rsa.pub') }}\" state=present" --user=root --ask-pass
````


### Most common commands
