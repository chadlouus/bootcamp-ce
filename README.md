# Bootcamp for IBM Code Engine
## Prerequisite
### Create a VM (Skip if you already are given SSH host and password)
 - Login to IBM Cloud
 - Create a new resource of Virtual Machine Classic
 - Accept the hourly plan
 - Optionally add your public ssh key by pasting the `content` of your `~/.ssh/id_rsa.pub`
 - Choose Ubuntu as operating system
 - Click Create
 - After the VM is provisioned, note down the public IP address and password
### Login to VM
Open a Terminal
```sh
ssh user@IP_address
```
Enter the password from above
### Install Docker
```sh
snap install docker
```
