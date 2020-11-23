## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

![https://drive.google.com/file/d/1i7NE5QSpCS6kardECQVdzIbsskhxsdvj/view?usp=sharing](Images/AzureELK.drawio)

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the playbook file may be used to install only certain pieces of it, such as Filebeat.

  - install-elk.yml

This document contains the following details:
- Description of the Topology
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly STABLE, in addition to restricting ACCESS to the network.

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the data and system metrics.

The configuration details of each machine may be found below.
| Name               | Function     | IP Address    | Operating System     |
|--------------------|--------------|---------------|----------------------|
| ELK-VM             | IDS          | 10.1.0.4      | Linux (Ubuntu 18.04) |
| Web1               | Webserver    | 10.0.0.7      | Linux (Ubuntu 18.04) |
| Web2               | Webserver    | 10.0.0.9      | Linux (Ubuntu 18.04) |
| Web3               | Webserver    | 10.0.0.11     | Linux (Ubuntu 18.04) |
| JumpBoxProvisioner | JumpBox      | 10.0.0.4      | Linux (Ubuntu 18.04) |
| RedTeamLB          | LoadBalancer | 52.229.63.130 | Linux (Ubuntu 18.04) |

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the JumpBoxProvisioner machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses: 108.70.152.104

Machines within the network can only be accessed by JumpBoxProvisioner.

A summary of the access policies in place can be found in the table below.

| Name               | Publicly Accessible | Allowed IP Addresses |
|--------------------|---------------------|----------------------|
| ELK-VM             | No                  | 108.70.152.104       |
| Web1               | No                  | 108.70.152.104       |
| Web2               | No                  | 108.70.152.104       |
| Web3               | No                  | 108.70.152.104       |
| JumpBoxProvisioner | Yes                 | Any                  |
| RedTeamLB          | Yes                 | Any                  |

### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because...
-Replication and rebuild tasks will be fully automated in case of expansion needs or attack.

The playbook implements the following tasks:
- Installs Docker
- Installs Pip
- Increases virtual memory
- Downloads Container image
- Launches Container


The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

![Screenshot 2020-10-12 210055](https://drive.google.com/file/d/1dmITyX42l_kimMlwqiKQfmpIur9AtuB0/view?usp=sharing)

### Target Machines & Beats
This ELK server is configured to monitor the following machines:
10.0.0.7, 10.0.0.9, 10.0.0.11

We have installed the following Beats on these machines:
Filebeat, Metricbeat

These Beats allow us to collect the following information from each machine:
Filebeat collects data about the file system.
Metricbeat collects machine metrics, such as uptime.

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the install-elk.yml file to control node (JumpBoxProvisioner).
- Update the ansible configuration file to include new ELK stack IP
- Run the playbook, and navigate to http://52.152.132.111:5601/ to check that the installation worked as expected.

- _Which file is the playbook? 
install-elk.yml 

Where do you copy it?_
...to the ansible control node (JumpBoxProvisioner)

- _Which file do you update to make Ansible run the playbook on a specific machine? 
edit /etc/andible/hosts

How do I specify which machine to install the ELK server on versus which to install Filebeat on?_ 
elk-install.yml vs filebeat-config.yml


- _Which URL do you navigate to in order to check that the ELK server is running?
http://52.152.132.111:5601/


The specific commands the user will need to run to...
 Download the playbook: git pull
 update the files, etc._