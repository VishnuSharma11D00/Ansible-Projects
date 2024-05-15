Building a simple LAMP stack and deploying Application using Ansible Playbooks.
-------------------------------------------

These playbooks require Ansible 1.2.

The project aims to automating the setup of a LAMP stack with Ansible. The web server serves PHP pages that 
interact with a MySQL database hosted on separate database servers. It involves the setup and 
configuration of these components for deployment.

This Projects requires to launch one master/ansible server, one web-server, and a db-server. 
Connecting ansible server to remote servers using SSH protocol.

These playbooks are meant to be a reference and starter's guide to building
Ansible Playbooks. These playbooks were tested on CentOS 6.x so I recommend
that you use CentOS or RHEL to test these modules.

This LAMP stack can be on a single node or multiple nodes. The inventory file
'hosts' defines the nodes in which the stacks should be configured.

        [webservers]
        localhost

        [dbservers]
        bensible

Here the webserver would be configured on the local host and the dbserver on a
server called `bensible`. The stack can be deployed using the following
command:

        ansible-playbook -i hosts site.yml

Once done, you can check the results by browsing to http://localhost/index.php.
You should see a simple test page and a list of databases retrieved from the
database server.
