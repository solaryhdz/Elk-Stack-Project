# Elk-Stack-Project
Elk Stack project documentation 

## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

![Network Diagram](https://user-images.githubusercontent.com/20096362/166097677-bef8dd9b-e2a3-4dd8-a698-adf05dda7f51.png)

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the .yml file may be used to install only certain pieces of it, such as Filebeat.

  install-elk.yml
  filebeat-playbook.yml
  metricbeatplaybook.yml

This document contains the following details:
- Description of the Topologu
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly redundant, in addition to restricting access to the network.
- Load balancers help prevent DDoS attacks by spreading the traffic over multiple machines. 
	Using a jump box helps make managing access control easier along with applying other controls. 

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the enviornment and system configs.
- Filebeat watches for log files and forwards them to elasticsearch. 
- Metricbeat records metrics from the OS and other services runing on the machine. 


The configuration details of each machine may be found below.
_Note: Use the [Markdown Table Generator](http://www.tablesgenerator.com/markdown_tables) to add/remove values from the table_.

| Name                 | Function   | IP Address     | Operating System |
|----------------------|------------|----------------|------------------|
| Jump-Box-Provisioner | Gateway    | 20.24.217.68   | Ubuntu           |
| Web-1                | DVWA       | 20.239.141.203 | Ubuntu           |
| Web-2                | DVWA       | 20.239.141.203 | Ubuntu           |
| ELK-Server           | Elk Server | 52.187.238.84  | Ubuntu           |

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the Jumpbox machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:
- 67.170.172.228

Machines within the network can only be accessed by Jump-Box-Provisioner.
- Jump-Box-Provisioner 20.24.217.68

A summary of the access policies in place can be found in the table below.

| Name                 | Publicly Accessable | Allowed IP Addresses |
|----------------------|---------------------|----------------------|
| Jump-Box-Provisioner | Yes                 | 67.170.172.228       |
| Web-1                | No                  | 20.239.141.203       |
| Web-2                | No                  | 20.239.141.203       |
| ELK-Server           | Yes                 | 67.170.172.228       |

### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because...
- Having configuration done via ansible allows changes to be made on all managed machines at once and it reduces the likelyhood of human error. 

The playbook implements the following tasks:
- Install Docker
- Install pip3
- install docker python module
- increase memory usage
- download and launch docker elk container

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

![docker_ps_output](https://user-images.githubusercontent.com/20096362/166097683-91a0400f-f733-4427-a1dd-b4404286bf1c.png)

### Target Machines & Beats
This ELK server is configured to monitor the following machines:
- Web-1 : 10.0.0.5
- Web-2 : 10.0.0.6

We have installed the following Beats on these machines:
- Metricbeat
- Filebeat

These Beats allow us to collect the following information from each machine:
- MetricBeat : Records metrics from the OS and services running on the machine. 
- Filebeat : Collects specified log files and forwards them to Elasticsearch. 

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the playbook.yml file to Jump-Box-Provisioner.
- Update the config.yml file to include the private IP of the Elk-Server.
- Run the playbook, and navigate to "http://[your.VM.IP]:5601/app/kibana" to check that the installation worked as expected.


_As a **Bonus**, provide the specific commands the user will need to run to download the playbook, update the files, etc._
