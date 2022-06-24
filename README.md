## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

![TODO: Update the path with the name of your diagram] https://github.com/jkleschick3/Project1_Elk_Stack/blob/main/Network%20Diagram/Project1_cloud_diagram_jk.drawio.png


These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the Ansible Playbook file may be used to install only certain pieces of it, such as Filebeat.

  - _ https://github.com/jkleschick3/Project1_Elk_Stack/blob/main/Ansible/ansible.cfg
https://github.com/jkleschick3/Project1_Elk_Stack/blob/main/Ansible/elk.yml
https://github.com/jkleschick3/Project1_Elk_Stack/blob/main/Ansible/hosts
https://github.com/jkleschick3/Project1_Elk_Stack/blob/main/Ansible/filebeat.yml
https://github.com/jkleschick3/Project1_Elk_Stack/blob/main/Ansible/filebeat-config.yml
https://github.com/jkleschick3/Project1_Elk_Stack/blob/main/Ansible/metricbeat.yml
https://github.com/jkleschick3/Project1_Elk_Stack/blob/main/Ansible/metricbeat-config.yml
https://github.com/jkleschick3/Project1_Elk_Stack/blob/main/Ansible/pentest.yml


This document contains the following details:
- Description of the Topologu
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly available, in addition to restricting access to the network.
-_A loadbalancer is meant to serve as a specific point of access for a service that is served by multiple machines. This enables high availability 

- _A jumpbox server acts as a gateway entry into a remote network.  Often requires ssh entry with ssh public key otherwise denied access.

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the log files and system resources.
- _Filebeat is meant primarily to watch for system logs and forward any changes to the Elasticsearch host.

- _MEtricbeat is used only for gathering metrics and system resources usage for display in the Elasticsearch host.

The configuration details of each machine may be found below.
_Note: Use the [Markdown Table Generator](http://www.tablesgenerator.com/markdown_tables) to add/remove values from the table_.

| Name     | Function | IP Address | Operating System |
|----------|----------|------------|------------------|
| Jump Box | Gateway  | 10.1.0.4   | Linux            |
| WEB1    | Web Application | 10.1.0.5   | Linux |
| WEB2    | Web Application | 10.1.0.6   | Linux |
| ELK     | Elasticsearch / log security | 10.2.0.4 | Linux|

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the Jumpbox machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:
- _71.162.179.144

Machines within the network can only be accessed by __SSH___.
- _TODO: Which machine did you allow to access your ELK VM? What was its IP address?_ - Jumpbox – 10.1.0.4

A summary of the access policies in place can be found in the table below.

| Name     | Publicly Accessible | Allowed IP Addresses |
|----------|---------------------|----------------------|
| Jump Box | Yes                 | 71.162.179.144    |
|  WEB 1 & 2|   No               | 10.1.0.4          |
|  Elk      |    No               | 10.1.0.4         |

### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because...
- _TODO: What is the main advantage of automating configuration with Ansible?_It allows for automated setup, reducing configuration errors

The playbook implements the following tasks:
* - Install Docker: Installs the core docker code to the remote server
* Install Python3_pip: Pip is an installation module that allows for additional docker modules to be installed easier
* Docker Module: Tells the previous PIP module to install the necessary docker component modules
* Increase Memory/Use More Memory: A common issue with the ELK Docker image is to little memory. This help fix the issue to allow the server to launch
* Download and Launch ELK Container: This downloads the ELK docker container and initializes it with the specified ports being published

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.



![TODO: Update the path with the name of your screenshot of docker ps output] https://github.com/jkleschick3/Project1_Elk_Stack/blob/main/Images/dockers_ps_output.png

### Target Machines & Beats
This ELK server is configured to monitor the following machines:
- _TODO: List the IP addresses of the machines you are monitoring_
10.1.0.4
10.1.0.5
10.1.0.6
10.2.0.4
We have installed the following Beats on these machines:
- _TODO: Specify which Beats you successfully installed_
Filebeats & Metricbeats on web1 web2 and Elk

These Beats allow us to collect the following information from each machine:
- _TODO: In 1-2 sentences, explain what kind of data each beat collects, and provide 1 example of what you expect to see. E.g., `Winlogbeat` collects Windows logs, which we use to track user logon events, etc._

File Beats collects system log events such as login to see who is logging on or has a connection.

MEtricbeats collects system metic data such as cpu usage and memory usage, which is useful in tracking system altering software. 

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the __Ansible_Playbook_ file to ___Docker__.
- Update the _Hosts____ file to include... Elk IP
- Run the playbook, and navigate to __Kibana__ to check that the installation worked as expected.

_TODO: Answer the following questions to fill in the blanks:_
- _Which file is the playbook? Where do you copy it?_Elk.yml
- _Which file do you update to make Ansible run the playbook on a specific machine? How do I specify which machine to install the ELK server on versus which to install Filebeat on?_Hosts / Ansible.cfg
- _Which URL do you navigate to in order to check that the ELK server is running? http://20.114.170.187:5601/app/kibana

_As a **Bonus**, provide the specific commands the user will need to run to download the playbook, update the files, etc._
