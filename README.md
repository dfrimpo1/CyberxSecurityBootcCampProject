# CyberxSecurityBootcCampProject
GT Cybersecurity Project 1

## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

**Note**: The following image link needs to be updated. Replace `diagram_filename.png` with the name of your diagram image file.  

![TODO: Update the path with the name of your diagram](Images/diagram_filename.png)

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the beats-playbook.yml file may be used to install only certain pieces of it, such as Filebeat.

  - _TODO: Enter the playbook file._

This document contains the following details:
- Description of the Topology
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly available, in addition to restricting access to the network.

- _TODO: What aspect of security do load balancers protect? 
Load balancers defend against denial of service attacks. 

What is the advantage of a jump box? Jump boxes improve a company’s network security by having a secure central location that must be connected to first before launching any tasks.
 
Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the files and system metrics.
- _TODO: What does Filebeat watch for?_Filebeat monitors specific log files to collect log events. Information is then forwarded to either Logstash or Elasticsearch to be indexed. This doesn’t take up much memory.

- _TODO: What does Metricbeat record?_Metricbeat records metrics from the server and operating system.



The configuration details of each machine may be found below.

| Name     | Function | IP Address | Operating System |
|----------|----------|------------|------------------|
| Jump Box | Gateway  | 10.0.0.4   | Linux            |
| ELKServer| ELKServer| 10.2.0.4   | Linux            |
| Web1     | Webserver| 10.0.0.10   | Linux           |
| Web2     | Webserver| 10.0.0.11   | Linux           | 

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the jumpbox machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses: My personal IP

Machines within the network can only be accessed by Jumpbox IP 10.0.0.4.


A summary of the access policies in place can be found in the table below.

| Name     | Publicly Accessible | Allowed IP Addresses |
|----------|---------------------|----------------------|
| Jump Box | No                  | My personal IP       |
| ElkServer| Yes(port 5601 only) | Internet             |
| Web1     | Yes                 | Via LoadBalancer 52.255.155.119|

### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because it ensures that the scripts run identically and do the same thing each time they run. 

- What is the main advantage of automating configuration with Ansible? This helps to eliminate variablirty between confirgurations.

The playbook implements the following tasks:
- _Installs Docker_
- _Installs Python-pip_
- _Install Docker python module_
- _Increases virtual memory_
- _Downloads and launches a docker ELK container with the following published ports: `5601` `9200` `5044`



### Target Machines & Beats
This ELK server is configured to monitor the following machines:
- Web1 10.0.0.10; Web2 10.0.11; Web3 10.0.0.12 
USE YOUR IP’s
We have installed the following Beats on these machines:
- Filebeat
- Metricbeat

These Beats allow us to collect the following information from each machine:
- - `Filebeat` generates and organizes log files to send to Elasticsearch on the ELK Server. The logs contain information about the file system such as which files have changed and when.

- `Metricbeat` collects metrics from systems and services to send to Elasticsearch on the ELK Server. The logs contain information such as CPU usage, memory, disk IO, and network IO statistics.


### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the install-elk.yml file to Ansbile container folder /etc/ansible/files/.

- Update the hosts file to include the Elk Server IP address of 10.2.0.4 under elkservers

- Run the playbook, ansible-playbook /etc/ansible/40.112.219.26:5601 to check that Kibana is running. 


Answer the following questions to fill in the blanks:_
-Which file is the playbook in? Where do you copy it?
- _The YAML file is the playbook. You copy it to the directory. 

- _Which file do you update to make Ansible run the playbook on a specific machine? You update the hosts file. How do I specify which machine to install the ELK server on versus which to install Filebeat on? Add the private IP under “servers”

- _Which URL do you navigate to in order to check that the ELK server is running? 40.112.219.26:5601


