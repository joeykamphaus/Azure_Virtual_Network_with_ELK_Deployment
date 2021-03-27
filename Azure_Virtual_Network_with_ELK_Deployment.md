# Azure_Virtual_Network_with_ELK_Deployment
## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

![TODO: Update the path with the name of your diagram](Images/diagram_filename.png)

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the filebeat-playbook.yml file may be used to install only certain pieces of it, such as Filebeat.

  - _TODO: Enter the playbook file._

This document contains the following details:
- Description of the Topologu
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

- The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.
Load balancing ensures that the application will be highly available, in addition to restricting IP's to the network.
 
- What aspect of security do load balancers protect? What is the advantage of a jump box?
Protects availability of the web servers from being haveing to much traffic. To connect securely to the webservers and run applications.

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the data and system logs.
- What does Filebeat watch for?
Log files with in the deployed applicaiton. 

- What does Metricbeat record?
System and application metrics on the usage


The configuration details of each machine may be found below.

| Name     | Function | IP Address | Operating System |
|----------|----------|------------|------------------|
| Jump Box | Gateway  | 10.0.0.4   | Linux            |
| Web-1    |Web Server| 10.0.0.5   | Linux            |
| Web-2    |Web Server| 10.0.0.6   | Linux            |
| Elk      |Elk Stack | 10.1.0.4   | Linux            |

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the Jump Box machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:
- 
 Person IP (173.172.91.251)

Machines within the network can only be accessed by Jump Box.
- Which machine did you allow to access your ELK VM? What was its IP address?

Jump Box 10.0.0.4

A summary of the access policies in place can be found in the table below.

| Name          | Publicly Accessible | Allowed IP Addresses                 |  
|---------------|---------------------|--------------------------------------|
| Jump Box      |     No              | Workstation Public IP on SSH 22      |
| Web-1         |     No              | 10.0.0.4 on SSH 22                   |
| Web-2         |     No              | 10.0.0.4 on SSH 22                   |
| ELK           |     No              | Workstation Public IP using TCP 5601 |
| Load Balancer |     No              | Workstation Public IP on HTTP 80     |

### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because...

You can repeat the process of installing and updating on all servers easily.

- What is the main advantage of automating configuration with Ansible?_

Eliminate human error

The playbook implements the following tasks:
- In 3-5 bullets, explain the steps of the ELK installation play. E.g., install Docker; download image; etc._

Install docker, create ansible container, install required program, install filebeat and metricbeat,  

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

![TODO: Update the path with the name of your screenshot of docker ps output](Images/docker_ps_output.png)

### Target Machines & Beats
This ELK server is configured to monitor the following machines:
-List the IP addresses of the machines you are monitoring

10.0.0.5 Web-1
10.0.0.6 Web-2

We have installed the following Beats on these machines:
- Specify which Beats you successfully installed
Filebeat and Metricbeat

These Beats allow us to collect the following information from each machine:
- In 1-2 sentences, explain what kind of data each beat collects, and provide 1 example of what you expect to see. E.g., `Winlogbeat` collects Windows logs, which we use to track user logon events, etc.

Filebeat - Is a log manager for elastic search files, sends data to a refernce monitor called Kibana. Is installed on the servers for collecting log files on DVWA servers to send that data to the ELK server for analysis.

Metricbeat - Is another aplication installed on ELK and DVWA servers to moniter virtual componets within the resources group. Logging files on performence during network traffic and is usage of resources.

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the public key file to vm's users key.
- Update the hosts file to include webservers IP address and the Elkservers IP address
- Run the playbook, and navigate to Kibana to check that the installation worked as expected.

- Answer the following questions to fill in the blanks:
- _Which file is the playbook? Where do you copy it?
 
The playbook .yml files are filebeat, metricbeat, docker, and elk on /etc copied over to the servers.

- _Which file do you update to make Ansible run the playbook on a specific machine? How do I specify which machine to install the ELK server on versus which to install Filebeat on?

You can change the information on the config files. Specify the IP addresses in the host file for which server they belong to, so when you run the playbook you can choose where it goes to. 

- _Which URL do you navigate to in order to check that the ELK server is running? 
 
http://server_ip:5601/ap/kibana
