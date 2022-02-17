# SERVER0

> 20.20.20.20
> 
> server0.lab.example.com

<br>

## Repository
#### Config yum repositories

> EPEL repository
````bash
**/etc/yum.repos.d/EPEL.repo**
[EPEL]
name=Repo EPEL
baseurl=https://ftp.icm.edu.pl/pub/Linux/dist/epel/8/Everything/x86_64/
enabled=1
gpgcheck=0
````
> RHEL ISO from WORKSTATION as repository
````bash
**/etc/yum.repos.d/RHELdisc.repo**
[rhel83-BaseOS]
name=RHRL 8.3 Local server repository BaseOS
baseurl=file:///run/media/zkr/RHEL-8-3-0-BaseOS-x86_64/BaseOS
enabled=1
gpgcheck=0
[rhel83-AppStream]
name=RHEL 8.3 Local server repository AppStream
baseurl=file:///run/media/zkr/RHEL-8-3-0-BaseOS-x86_64/AppStream
enabled=1
gpgcheck=0
````

<br>

## Network
#### Network interface configuration

````bash
nmcli connection down "enp0s3"
nmcli connection modify "enp0s3" ipv4.method manual ipv4.addresses 20.20.20.20/24 ipv4.dns 1.1.1.1 +ipv4.dns 1.0.0.1 connection.autoconnect yes
nmcli connection up "enp0s3"
````

#### Hosts configuration

````bash
**/etc/hosts**
127.0.0.1   localhost localhost.localdomain localhost4 localhost4.localdomain4
::1         localhost localhost.localdomain localhost6 localhost6.localdomain6
#Ansible machines
20.20.20.254    workstation.lab.example.com    workstation
20.20.20.20     server0.lab.example.com        server0
20.20.20.21     server1.lab.example.com        server1
20.20.20.22     server2.lab.example.com        server2
20.20.20.23     server3.lab.example.com        server3
20.20.20.24     server4.lab.example.com        server4
````
<br>
<a href="https://github.com/zkr-development/ansible-environment#installation-">Back to the home of the project</a>
