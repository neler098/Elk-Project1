# Elk-Project1
files for my project
## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

![image](https://user-images.githubusercontent.com/80600966/122856756-faf60f80-d2dc-11eb-9f23-a4180fc678d3.png)


These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the .yml file may be used to install only certain pieces of it, such as Filebeat.

  - ansible-playbook elk.yml & filebeat-playbook.yml

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
- Load balancers protect the Availability aspect of the CIA Triad. The advantage of having a jumpbox is that it can luach administative task
Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the jumpbox and system network.
- The filebeat watches for file changes on the machine
- The metric beat collects metrics from the operating system 

The configuration details of each machine may be found below.
_Note: Use the [Markdown Table Generator](http://www.tablesgenerator.com/markdown_tables) to add/remove values from the table_.

| Name     | Function | IP Address | Operating System |
|----------|----------|------------|------------------|
| Jump Box | Gateway  | 10.0.0.4   | Linux            |
| Web-1    | Webserver| 10.0.0.5   | Linux            |
| Web-2    | Webserver| 10.0.0.6   | Linux            |
| Elk      | Monitoring| 10.1.0.4  | Linux            |

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the Jumpbox machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:
- 40.77.106.217

Machines within the network can only be accessed by SSH.
- _JumpBoxProvisioner@10.0.0.4

A summary of the access policies in place can be found in the table below.

| Name     | Publicly Accessible | Allowed IP Addresses |
|----------|---------------------|----------------------|
| Jump Box | Yes                 | 40.77.106.217        |
| Web-1    | No                  |10.0.0.5              |
| Web-2    | No                  |10.0.0.6              |

### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because...
- Ansible is an open-source tool that can be very flexible.

The playbook implements the following tasks:
- Install docker.io
- Install python3_pip
- Install docker python module
- INcrease virtual memory
- Download and launch a docker

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

![image](https://user-images.githubusercontent.com/80600966/122857797-b53a4680-d2de-11eb-86f3-4b2077c01430.png)


### Target Machines & Beats
This ELK server is configured to monitor the following machines:
- Web-1(10.0.0.5) & Web-2(10.0.0.6)

We have installed the following Beats on these machines:
- Microbeats

These Beats allow us to collect the following information from each machine:
- Filebeat collects data about the file system & metricbeat which collects machine metrics, such as uptime.

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the playbook file to Ansible Control Nose.
- Update the host file to include webservers and elk
- Run the playbook, and navigate to Kibana(http://20.80.51.59:5601/app/kibana) to check that the installation worked as expected.

