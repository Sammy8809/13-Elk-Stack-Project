# 13-Elk-Stack-Project

## Automated ELK Stack Deployment




These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the yml file may be used to install only certain pieces of it, such as Filebeat.



This document contains the following details:
- Description of the Topology
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly available, in addition to restricting inbound access to the network.
-_Having a jumpbox allows us to make sure that only authorized users have access to the other webservers._ 

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the file systems of the VMs and system metrics.
- __Filebeat monitors the log files, collects log events, and forwards the information to Elasticsearch.__ 
- __Metricbeat collects metrics from the operating system and from services running on the server.__ 

The configuration details of each machine may be found below.


| Name     | Function | IP Address | Operating System |
|----------|----------|------------|------------------|
| Jump Box | Gateway  | 10.0.0.4   | Linux            |
| Web-2    |Web Server| 10.0.0.5   | Linux            |
| Web-3    |Web Server| 10.0.0.7   | Linux            |
| Web-4    |Web Server| 10.0.0.5   | Linux            |
| Elk VM   |Monitoring| 10.1.0.4   | Linux            |

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the Jump Box machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:
- __173.21.141.4__

Machines within the network can only be accessed by each other.
- __Web 2, Web 3, Web 4 send traffic to the Elk Server__
- __Jump Box can connect to the Elk Server__
	-IP: 13.90.227.236

A summary of the access policies in place can be found in the table below.

| Name     | Publicly Accessible | Allowed IP Addresses |
|----------|---------------------|----------------------|
| Jump Box | Yes                 | 173.21.141.4         |
|   Web-2  | No                  | 10.0.0.0/16          |
|   Web-3  | No                  | 10.0.0.0/16          |
|   Web-4  | No                  | 10.0.0.0/16          |
|   Elk    | No                  | 10.0.0.0/16          |  
### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because...
- __Ansible allows us to automate commands and installation steps without having to do it one by one.__ 

The playbook implements the following tasks:
- __Installs docker.io__
- __Installs python3__
- __Installs the docker module__
- __Increase the virtual memory of the virtual machine and allows the VM to use more memory__
- __Download and lauch a docker elk container__




### Target Machines & Beats
This ELK server is configured to monitor the following machines:
- __10.0.0.6__
- __10.0.0.5__
- __10.0.0.7__

We have installed the following Beats on these machines:
- __Filebeat__
- __Metricbeat__

These Beats allow us to collect the following information from each machine:
- __Filebeat: Detects changes to the filesystem. Will use to keep Apache logs, which will create logs of the activity and performance of the webserver__
- __Metricbeat: Used to detect changes to the system metrics. i.e. SSH attempts and sudo esclations.__ 

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- __Copy the playbook file to Ansible Control Node.__
- __Update the host file to include the VMs you want to run playbooks on.__ 
- __Run the playbook, and navigate to ____ to check that the installation worked as expected.__

_TODO: Answer the following questions to fill in the blanks:_
- __The playbook files are filebeat-playbook.yml, metricbeat-playbook.yml, and elk-install.yml__
- __Update your config file and to change what machine the playbook runs on. In the yml file, change the "name" section to either webservers or elk__
- __http://10.1.0.4:5601__
