# ElkProject1
The files in this repository were generated to configure the network depicted in the diagram ElkProject1
These files have been tested an used to generate an active ELK deployment in an Azure Lab environment.
The lab can be used to recreate the deployment
Select portion of the playbook file may be used to install component - such as Filebeat
Network topology is a visual display of the connections within the network
The Topology depicts the goal to successfully run DVWA
Load balancing ensure the application will be highly available, in addition to restricting access to the network
Load balancers add additional layers of security to the website; without having to make changes to the application.  
Load balancers protect application from emerging threats
The firewall protect from website hackers and virus scanners
Advantages of a jumpbox:  Protects a critical system; it is a simple system typically with a single operating system;
      easy to upgrade; reliable and customization is not difficult
Integrating an ELK server allows users to easily monitor the vulnerable VM's for changes to the log file and system metrics
Filebeat watches Log Files
Metricbeat records Metrics
Markdown Table shows the details of each machine
Access Policies:  NO expose to the public internet
    Only the JumpBox allows connection from the internet.  IP specific to the Jumpbox Provisioner 
    Granting network access only to certain IP address: is the purpose of IP whitelisting
    1st IP addresses can change often:  2nd IP can be spoofed which cause the network to become less secure
    Machines within the network can only be accessed by SSH to Jumpbox - current IP
Access allowed for ELK VM are Filebeat and Metricbeat
The IP would be the stationary (aka homeIP)
Access Policies - all are not Publicly Accessible:  
    JumpBox allows HomeIP - Web1 and Web2 .6 and .7 along with homeIP; ElkProject .4 and homeIP
    The network is set up with a load balance which monitored instance of DVWA, Vulnerable Web Application.
    Load balancing ensure that the application will be highly available, in addition to restricting access to the network
    Load balancing is effective at preventing DDos attacks
    Configurations:  Ansible was used to automate configuration of the ELK machine.  No configuration was performed manually
                     which is advantageous because automation is time consuming; it streamlines connectivity and 
                     eliminates setting errors.
Open-source automation and configuration - tool to manage which improves the scalability, reliability
and consistency of the IT environment:  main advantage of automating configuration with Ansible
Playbook:  installs and launches the docker module; enhances memory to max; launch occurs after download
DockerPS - ElkProject1docker ps command - file attached
Target machines and beats:  ELK server:  Web1 and Web2 (.6 and .7) ElkProject (.4)
Filebeat and Metricbeat have both been installed
  The beats collect data;
  Filebeat:  Collects and forwards centralized data logs
  Metricbeat:  Collects system and application metrics - and send to the analytical tool Elasticsearch
Playbook:  SSH into the control node:  copy the configuration to etc/ansible; update the host file; run playbook
           Navigate to Kibana - verify installation function as expected
etc/ansible directory - within the container:  playbook file
The host file in the directory etc/ansible;  where the playbook is copied
YAML: is the file which is updated is a funciton which makes Ansible run the playbook
Private IP; where to install EL:K server
myIP:5601/app/kibana; Navigate to ensure ELK server is running 
Run Playbook:
  in root of the container  /etc/ansible#
      sudo apt update
      sudo apt install ansible
      
      nano hosts
      nano playbook2.yml
      ansible-p[laybook playbook2.yml
           
  
                     
      
