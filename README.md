Building a simple LAMP stack and deploying Application using Ansible Playbooks.
-------------------------------------------

The project aims to automating the setup of a LAMP stack with Ansible. The web server serves PHP pages that 
interact with a MySQL database hosted on separate database servers. It involves the setup and 
configuration of these components for deployment.

These playbooks were tested on CentOS 6.x so I recommend that you use CentOS or RHEL to test these modules.

This Projects requires to launch one master/ansible server, one web-server, and a db-server. 
Connecting ansible server to remote servers using SSH protocol.
- First, launch 3 EC2 instances, where one is master (Ansible) and other two are hosts.
- ssh into the instances and in the Ansible instance, run:
```sh
sudo yum install ansible
```
- After installation, generate keys in all three instances:
```sh
ssh-keygen
```
- Now copy the **copy id_rsa.pub (public keys) of ansible and paste in authorized_keys of host instances**. Repeat in both instances
  
- This LAMP stack can be on a single node or multiple nodes. The inventory file 'hosts' in the lamp_simple folder
  defines the nodes in which the stacks should be configured.

        [webservers]
        localhost

        [dbservers]
        bensible

Here the webserver would be configured on the local host and the dbserver on a server called `bensible`.

![screenshot](Screenshots/Screenshot(127).png)

The stack can be deployed using the following
command:
```sh
        ansible-playbook -i hosts site.yml
```
Once done, you can check the results by browsing to http://localhost/index.php.
You should see a simple test page and a list of databases retrieved from the
database server.
