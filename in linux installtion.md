in master & worker node

```
#to install ansible
amazon-linux-extras install ansible -y

useradd ansibleuser
passwd ansibleuser

visudo -> add this line -> ansibleuser ALL=(ALL)   NOPASSWD: ALL


```

in worker nodes

```
vim /etc/ssh/sshd_config  -> set password authendication yes
service sshd restart

```

in master node

```
sudo su - ansibleuser
ssh-keygen
ssh-copy-id "key.pem" ansibleuser@worker1-publicip
ssh-copy-id "key.pem" ansibleuser@worker2-publicip

cd /etc/ansible
vim hosts  -> add the node server details

node1-ip
node2-ip

[web]
node1-ip

[db]
node2-ip

```

```
ansible all -m ping
ansible db -m ping
ansible web -m ping

```
