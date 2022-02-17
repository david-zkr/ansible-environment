# ansible-environment

_Instructions and scripts to create an virtualized ansible test environment._<br>
_Here you can see the architecture:_

<p align="center">
  <img src="https://github.com/zkr-development/ansible-environment/blob/main/images/infra.png?raw=true">
</p>

## Starting 🚀
### Pre-requirements 📋

_You will need:_
````
A virtualization program (VirtualBox, VMWare, ...).
````
````
An RHEL8 ISO. You can download it from Red Hat official website.
````
````
At least 8GB RAM in your computer.
````

### Installation 🔧

_Create "workstation" VM. Use RHEL8 with GUI. 2GB RAM are enough._

_Create "server0" VM and clone it until you have server{0,1,2,3,4}. This servers don't need to have GUI, so 1GB RAM is enough._

<p align="center">
  <img src="https://github.com/zkr-development/ansible-environment/blob/main/images/vbox-allmachines.png?raw=true">
</p>

_Follow this guides to configure each server. I am working to make it as a script :)._

<ul>
  <li>
    <a href="https://github.com/zkr-development/ansible-environment/blob/main/machines-config/workstation-20.20.20.254.md">Workstation guide</a>
  </li>
  <li>
    <a href="https://github.com/zkr-development/ansible-environment/blob/main/machines-config/server0-20.20.20.20.md">Server0 guide</a><br>
  </li>
  <li>
    <a href="https://github.com/zkr-development/ansible-environment/blob/main/machines-config/server1-20.20.20.21.md">Server1 guide</a><br>
  </li>
  <li>
    <a href="https://github.com/zkr-development/ansible-environment/blob/main/machines-config/server2-20.20.20.22.md">Server2 guide</a><br>
  </li>
  <li>
    <a href="https://github.com/zkr-development/ansible-environment/blob/main/machines-config/server3-20.20.20.23.md">Server3 guide</a><br>
  </li>
  <li>
    <a href="https://github.com/zkr-development/ansible-environment/blob/main/machines-config/server4-20.20.20.24.md">Server4 guide</a><br>
  </li>
</ul>





## Built in 🛠️

* [VirtualBox](https://www.virtualbox.org/) - Virtualization
* [Red Hat Enterprise Edition 8](https://developers.redhat.com/rhel8) - Operating System
* [Ansible](https://docs.ansible.com/) - Orchestation


## Authors ✒️

* **Walter Castro** - *Concept* - [waltercastro90](https://github.com/waltercastro90)
* **David Bernet** - *Documentation* - [david-zkr](https://github.com/david-zkr)

---

