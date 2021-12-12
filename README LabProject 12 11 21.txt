NW wk13 creation of Lab repo## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below. These files have been tested and used to generate a live ELK deployment on Azure.
They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the playbook file may be used to install only certain pieces of it, such as Filebeat.

![MTK2021CyberNW Lab Dec ElkProject1] (Cloud and Elk diagram 12.11.21.png)

Network topology is a visual display of the connections of the computer network, specifically for the project of ElkStackCybersecurity-Northwestern University

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above.
Alternatively, select portions of the playbook file may be used to install only certain pieces of it, such as Filebeat.

This document contains the following details:
![MTK2021CyberNW Lab Dec] (ElkProject1/topology.svg)
- Description of the Topology
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly available, in addition to restricting access to the network.
-What aspect of security do load balancers protect? threats
  The Firewall – in the load balancer – protects from website hackers and virus scanners.
  Load balancers add additional layers of security to website – without having to make changes to the application.  They protect applications from emerging threats.
What is the advantage of a jump box?
- Protects a critical system
- A jump box is simply a system, usually a single operating system
- Easy to upgrade
- Reliability and ease of customization

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the log files and system metrics.
- What does Filebeat watch for? Log Files
- What does Metricbeat record? Metrics

The configuration details of each machine may be found below.
_Note: Use the [Markdown Table Generator](http://www.tablesgenerator.com/markdown_tables) to add/remove values from the table_.

| Name        | Function            | IP Address | Operating System |Windows...
|----------   |----------           |------------|------------------|
| Jump Box    | Gateway             | 10.0.0.7   | Linux  Ubuntu    |
| Web1        | VM                  | 10.0.0.6   | Linux  Ubuntu    |
| Web2        | VM                  | 10.0.0.10  | Linux  Ubuntu    |
| ElkProject  | VM                  | 10.1.0.4   | Linux  Ubuntu    |

### Access Policies

The machines on the internal network are not exposed to the public Internet.

Only the Jump Box machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:
 Add whitelisted IP addresses: JumpBoxProvisioner

Machines within the network can only be accessed by SSH to the JumpBox.
- 10.0.0.7

A summary of the access policies in place can be found in the table below.

| Name      | Publicly Accessible        | Allowed IP Addresses |
|---------- |--------------------        |----------------------|
| Jump Box  | No (yes during execution)  | HomeIP               |
| Web1 VM   | No (yes during execution)  | 10.0.0.7 & Home      |
| Web2 VM   | No (yes during execution)  | 10.0.0.7 & Home      |
|ElkProject | No (yes during execution)  | 10.0.0.7 & Home      |

### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because...
-The network is set up with a load-balance which monitored instances of DVWA, Vulnerable Web Application. Load balancing ensures that the application will be
highly available, in addition to restricting access to the network. Load balancing is effective at preventing DDoS attacks.

The playbook implements the following tasks:
- _In 3-5 bullets, explain the steps of the ELK installation play. E.g., install Docker; download image; etc._
- #3 Installs docker python module
- #4 Installs memory to max
- #5 Launches the docker Elk container after download

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

![onedrive/desktop](photos/docker.png)

### Target Machines & Beats
This ELK server is configured to monitor the following machines:
- Web1 10.0.0.7
- Web2 10.0.0.6
- ElkProject 10.0.0.4

We have installed the following Beats on these machines:
- Filebeat
- Metricbeat

These Beats allow us to collect the following information from each machine:
- Filebeat:
- Tool to collect, forward and centralize data logs
- Defined parameters – collects log events – forwards to Elasticsearch or Logstash for indexing
- Metricbeat
- Tool to collect system and application metrics – send the data to
- Elasticsearch:  examples of system metrics:  CPU, Memory, Disk and Network Stats (IOPS)

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned:

SSH into the control node and follow the steps below:
- Copy the configuration file to etc/ansible.
- Update the host file to include the private IP address of the Elk machine.
- Run the playbook, and navigate to Kibana to check that the installation worked as expected.

_TODO: Answer the following questions to fill in the blanks:_
- Which file is the playbook? YAML Where do you copy it? etc/ansible directory - within the container.
- Which file do you update to make Ansible run the playbook on a specific machine? Host file in directory etc/ansible:
- How do I specify which machine to install the ELK server on versus which to install Filebeat on? use the private IP address
- Which URL do you navigate to in order to check that the ELK server is running?  myIP/kibana/home

_As a **Bonus**, provide the specific commands the user will need to run to download the playbook, update the files, etc._
  - in root of the container /etc/ansible#
      sudo apt update
      sudo apt install ansible

      nano hosts
      nano playbook2.yml
      ansible-playbook playbook2.yml
