# WORKSTATION

> 20.20.20.254
> 
> workstation.lab.example.com

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

> RHEL ISO as repository (first you have to mount it). We are going to share it with apache to all machines in the environment
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

## Install Vbox Guest Additions
````bash
sudo yum groupinstall "Development Tools"

sudo yum install kernel-devel elfutils-libelf-devel
````

> Then mount and execute Vbox GA disk

<br>

## Network

#### Network interface configuration

> Interface enp0s3 (NAT, DHCP, default interface)
````bash
nmcli connection down enp0s3

nmcli connection modify "enp0s3" ipv4.method auto connection.autoconnect yes

nmcli connection up enp0s3

ip a
````

> Interface enp0s8 (INTERNAL NET, STATIC, added interface)

````bash
cd /etc/sysconfig/network-scripts

cp ifcfg-enp0s3 ifcfg-enp0s8

vim ifcfg-enp0s8

**HERE YOU HAVE CHANGE NAME AND UUID BY GENERATING A NEW ONE**

uuidgen
````

````bash
nmcli connection down enp0s8

nmcli connection modify enp0s8 ipv4.method manual ipv4.addresses 20.20.20.254/24 ipv4.dns 1.1.1.1 +ipv4.dns 1.0.0.1 connection.autoconnect yes

nmcli connection up enp0s8

ip a
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

#### Firewall configuration
````bash
sudo firewall-cmd --add-service=http --permanent && sudo firewall-cmd --reload
````

<br>

## Apache

> Install httpd service

````bash
yum update

yum install httpd
````

> Add this to /var/fstab/ to automount RHEL ISO in /var/www/html

````bash
**/var/fstab/**

### RHEL8 disk mounted as repo to serve it with apache

/dev/sr0 /var/www/html/ iso9660 defaults,nofail 0 0

````

> You changed the mount route of the ISO, so you will have to configure again the repo in local
> 
````bash
**/etc/yum.repos.d/RHELdisc.repo**

[rhel83-BaseOS]
name=RHRL 8.3 Local server repository BaseOS
baseurl=file:///var/www/html/BaseOS
enabled=1
gpgcheck=0

[rhel83-AppStream]
name=RHEL 8.3 Local server repository AppStream
baseurl=file:///var/www/html/AppStream
enabled=1
gpgcheck=0
````

<br>

## Ansible

> Install ansible
````bash
yum install ansible
````
<br>
<a href="https://github.com/zkr-development/ansible-environment#installation-">Back to the home of the project</a>
