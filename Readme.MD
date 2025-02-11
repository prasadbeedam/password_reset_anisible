SETUP:
===================================================================

ALL SERVERS: to communicate with all servers

hostnamectl set-hostname                                                       

sudo -i

passwd root

vim /etc/ssh/sshd_config

38: PermitRootLogin yes  # uncomment

63: PasswordAuthentication yes

systemctl restart sshd

systemctl status sshd
====================================================================
ANSIBLE SERVER:

====================================================================

amazon-linux-extras install ansible2 -y

yum install python python-pip python-level -y

vim /etc/ansible/hosts

[servers]

172.31.92.91 new_pass=Password8955

172.31.95.21 new_pass=Password8889

172.31.82.94 new_pass=Password8999

vim /etc/ansible/ansible.cfg (uncomment 14 & 22)

=================================================================


SSH CONNECTIONS: ANSIBLE SERVER

ssh-keygen  --- > 4 ENTERS

ssh-copy-id root@172.31.82.63 --- > yes --- > password

ssh 172.31.82.63

ctrl + d (logout)

Note: If you do not log out and try to connect to the new server it won't connect

Connect all the servers in this way

cd .ssh --- > cat known_hosts     >>>> To show list of worker node's 

ansible-playbook reset_password.yml        >>>>>>>>>>>>>>>>>> run >>>>>>>>>>>>>>>>>>>
