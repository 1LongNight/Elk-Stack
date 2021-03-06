# Elk-Stack
## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

![image](Diagrams/Network.png)

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the included YAML files may be used to install only certain pieces of it, such as Filebeat.


This document contains the following details:
- Description of the Topology
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitore
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly redundant, in addition to restricting unauthorized access to the network.
  - Balancers route or balance traffic across an environment which prevents DDoS attacks.
  - Advantage of a Jump Box is to be able to allow monitored access to an environment from a remote work station.

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the _____ and system _____.
- _Monitors log files activities 
- _Gather's metrics from the environment i.e. services running on a server

The configuration details of each machine may be found below.
_Note: Use the [Markdown Table Generator](http://www.tablesgenerator.com/markdown_tables) to add/remove values from the table_.

| Name     | Function | IP Address | Operating System |
|----------|----------|------------|------------------|
| Jump Box | Gateway  | 10.0.0.4   | Linux            |
| Web1     | VM       | 10.0.0.5   | Linux            |
| Web2     | VM       | 10.0.0.6   | Linux            |
| Elk      | VM       | 10.1.0.5   | Linux            |

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the _____ machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:
-_52.151.15.73

Machines within the network can only be accessed by _____.
_Red-Team Jump Box Pub IP 52.151.15.73 Private IP 10.0.0.4
A summary of the access policies in place can be found in the table below.

| Name     | Publicly Accessible | Allowed IP Addresses |
|----------|---------------------|----------------------|
| Jump Box | Yes                 | 52.151.15.73         |
| Web1     | No                  | 10.0.0.5             |
| Web2     | No                  | 10.0.0.6             |

### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because...
- _Automation makes tasks less time consuming

The playbook implements the following tasks:
- _Install: docker.io
- _Install: python-pip
- _Install: docker
- _Command: sysctl -w vm.max_map_count=262144
- _Launch docker container: Elk

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

![image](Diagrams/Elk.png)

### Target Machines & Beats
This ELK server is configured to monitor the following machines:
- _0.0.0.0:5044->5044/tcp, 0.0.0.0:9200->9200/tcp, 0.0.0.0:5601->5601/tcp
We have installed the following Beats on these machines:
- _Filebeat and Metricbeat
These Beats allow us to collect the following information from each machine:
_Filebeat monitors log files for changes. Metricbeat gathers metrics on servers.
### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the _____ file to _____.
- Update the _____ file to include...
- Run the playbook, and navigate to ____ to check that the installation worked as expected.
- _Which file is the playbook? Where do you copy it?_/etc/ansible/roles/filebeat-playbook.yml
- _Which file do you update to make Ansible run the playbook on a specific machine? How do I specify which machine to install the ELK server on versus which to install Filebeat on?_hosts, elk 10.1.0.5, webservers is where filebeat is
- _Which URL do you navigate to in order to check that the ELK server is running?_http://20.106.92.26:5601/app/kibana

_As a **Bonus**, provide the specific commands the user will need to run to download the playbook, update the files, etc._ansible-playbook filebeat-playbook.yml

![image](Diagrams/Lynis.png)
