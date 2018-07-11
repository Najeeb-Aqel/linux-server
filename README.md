# Linux-Server

My Bookshelf is my personal library of books I read with my own reflections and notes.

# Prerequisites

Python 2.7 or hiher: You can download it from the official site - [Python Software Foundation](https://www.python.org)

The site need to be opened at http://localhost:5000/

# Installation 


1. start a new ubuntu linux server and ssh into your server:

      * [creating your server on lightsail](https://aws.amazon.com/getting-started/tutorials/launch-a-virtual-machine/?trk=gs_card)
      
      * ssh into your server: `ssh -i ~/.ssh/project_key.rsa ubuntu@Public IP address `
      

2. Update all currently installed packages: 
      * `sudo apt-get update`
      * `sudo apt-get upgrade`

3.  Change the SSH port from 22 to 2200:
      * edit file `/etc/ssh/sshd_config` and change port 20 to 2200.
      * restart ssh service after editting: `sudo service ssh restart`
      
4. Configure the Uncomplicated Firewall (UFW):
      * deafult deny of all incoming requests: `sudo ufw default deny incoming`
      * default allow of all outgoing traffic: `sudo ufw default allow outgoing`
      * allow incoming connections for SSH (port 2200): `sudo ufw default allow 2200/tcp`
      * allow incoming connections for HTTP (port 80):  `sudo ufw default allow 80/tcp`
      * allow incoming connections for NTP (port 123):  `sudo ufw default allow 123/udp`
      
5. Create a new user account named grader:
      * `sudo adduser grader`

6. Give grader the permission to sudo:
      * `usermod -aG sudo grader` or adding grader to the sudoers file by adding `grader  ALL=(ALL:ALL) ALL`
      
7. Create an SSH key pair for grader using the ssh-keygen tool:
      * `ssh-keygen` to create a key on your local machine.
      * save the content of the `.pub` file in `~/.ssh/authorized_keys` in the server machine.
      
8. Configure the local timezone to UTC:
      * configure time by running `sudo dpkg-reconfigure tzdata`


# Built With

* [Bootstrap](http://getbootstrap.com/).
* [Vagrant](https://www.virtualbox.org/wiki/Downloads)
* [Virtualbox](https://www.vagrantup.com/)

