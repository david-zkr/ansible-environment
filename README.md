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

_Menciona las herramientas que utilizaste para crear tu proyecto_

* [Dropwizard](http://www.dropwizard.io/1.0.2/docs/) - El framework web usado
* [Maven](https://maven.apache.org/) - Manejador de dependencias
* [ROME](https://rometools.github.io/rome/) - Usado para generar RSS


## Authors ✒️

_Menciona a todos aquellos que ayudaron a levantar el proyecto desde sus inicios_

* **Andrés Villanueva** - *Trabajo Inicial* - [villanuevand](https://github.com/villanuevand)
* **Fulanito Detal** - *Documentación* - [fulanitodetal](#fulanito-de-tal)

También puedes mirar la lista de todos los [contribuyentes](https://github.com/your/project/contributors) quíenes han participado en este proyecto. 


## Thanks to 🎁

* Comenta a otros sobre este proyecto 📢
* Invita una cerveza 🍺 o un café ☕ a alguien del equipo. 
* Da las gracias públicamente 🤓.
* etc.



---

