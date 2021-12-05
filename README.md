# Elk-Stack-Project

## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

![Network Diagram] (/Diagrams/KVP_Cloud_Security_with_ELK_Deployment_Diagram.png)

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the _____ file may be used to install only certain pieces of it, such as Filebeat.

  - _TODO: Enter the playbook file._

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
It ensures availability to the web server

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the logs and system traffic.
* Filebeat watches for log files/locations and collect log events. (Filebeat: Lightweight Log Analysis &amp; Elasticsearch)
* Metricbeat records metrics and statistical data from the operating system and from services running on the server (Metircbeat: Lightweight Shipper for Metrics)

The configuration details of each machine may be found below.
_Note: Use the [Markdown Table Generator](http://www.tablesgenerator.com/markdown_tables) to add/remove values from the table_.

| Name     | Function  | IP Address | Operating System |
|----------|-----------|------------|------------------|
| Jump Box | Gateway   | 10.0.0.4   | Linux            |
| Web 1    | Web Server| 10.0.0.5   | Linux            |
| Web 2    | Web Server| 10.0.0.6   | Linux            |
| Elk      | ELK Stack | 10.1.0.4   | Linux            |

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the Jump Box machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:
* 73.127.24.254 (Personal IP)

Machines within the network can only be accessed by SSH.
* Web and Elk Servers

A summary of the access policies in place can be found in the table below.

| Name     | Publicly Accessible | Allowed IP Addresses     |
|----------|---------------------|--------------------------|
| Jump Box | Yes                 | Personal IP Address      |
| Web-1    | No                  | Jumpbox SSH via 10.0.0.5 |
| Web-2    | No                  | Jumpbox SSH via 10.0.0.6 |

### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because...
* Automating the install procces lets you deploy multiple servers easily and quickly

The playbook implements the following tasks:
1. Installs Docker.io and pip3
2. Increases the VM Memory
3 Download and Configure ELK Docker Container
4. Sets Published Ports

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

![TODO: Update the path with the name of your screenshot of docker ps output](Images/docker_ps_output.png)

### Target Machines & Beats
This ELK server is configured to monitor the following machines:
* Web-1 10.0.0.5
* Web-2 10.0.0.6

We have installed the following Beats on these machines:
* Filebeat
* Metricbeat

These Beats allow us to collect the following information from each machine:
* Filebeat watches for log files/locations and collect log events. 
* Metricbeat records metrics and statistical data from the operating system and from services running on the server

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the filebeat-config.yml and metricbeat-config.yml file to /etc/ansible/files.
- Update the config file to include the Private IP of the ELK Server to the Elasticsearch and Kibana Sections of the Config File
- Run the playbook, and navigate to http://20.121.19.240:5601/app/kibana to check that the installation worked as expected.

- _Which file is the playbook? Where do you copy it?_
* install-elk.yml, filebeat-playbook.yml, metricbeat-playbook.yml
* /etc/ansible
- _Which file do you update to make Ansible run the playbook on a specific machine? How do I specify which machine to install the ELK server on versus which to install Filebeat on?_

* /etc/ansible/hosts.cfg
* In /etc/ansible/hosts you tell it where you want it installed
* 
- _Which URL do you navigate to in order to check that the ELK server is running?

* http://20.121.19.240:5601/app/kibana

