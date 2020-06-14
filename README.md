## Automated ELK Stack Deployment

This document contains the following details:
- Description of the Topologu
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly functional, in addition to restricting DOS Attacks to the network.
- What aspect of security do load balancers protect?
Load balancers provide flexibility by rerouting live traffic between servers in the event a server becomes unavailable due to a DDoS attack. Theyre also ntegral part when layered within a security model as it distributes workloads across multipule servers to prevent overloading, while optimizing productivity and maximizing uptime.
- What is the advantage of a jump box?
A jumpbox is a secure computer that is used to provide an additional layer of security. Admins connect to a jumpbox prior to launching any administrative tasks. They are viewed as lockdown secure workstations that can limit attacks from hackers to the network.

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the infrastructure and system logs.
- _ What does Filebeat watch for?
Filebeat monitors log files or locations that you specify, collects log events.
- : What does Metricbeat record?_
Metricbeat records metrics and statistics then sends the data to the output of our choice.



| Name     | Function | IP Address | Operating System |
|----------|----------|------------|------------------|
| Jumpbox  | Gateway  | 10.0.0.4   | Linux            |
| DVMA-VM1 |Web Server| 10.0.0.5   | Linux            |
| DVMA-VM2 |Web Server| 10.0.0.6   | Linux            |
| ElkServer|ElkServer | 10.0.0.7   | Linux            |

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the JumpBox machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:
- : 10.0.0.4
    10.0.0.5
    10.0.0.6
    10.0.0.7

Machines within the network can only be accessed by New Jump-Box-Provisionor.
- : DVMA-VM1 & DVMA-VM2 , 10.0.0.5 , 10.0.0.6

A summary of the access policies in place can be found in the table below.

| Name     | Publicly Accessible | Allowed IP Addresses |
|----------|---------------------|----------------------|
| Jump Box |      Yes            |whitelist IP addresses
|DVMA-VM1  |      Yes            |Any Ip Addresses.     |
|DVMA-VM2  |      Yes            |Any Ip Addresses.     |
|Elk-Server|      Yes            |10.0.0.4              |
                                  10.0.0.5
                                  10.0.0.6
                                  10.0.0.7
### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because...
- What is the main advantage of automating configuration with Ansible?_
Ansible provides many advantages such as its simplicity to run complex multi-tier IT application environments. When you use Ansible to configure these components, difficult manual tasks become repeatable and less vulnerable to error.

The playbook implements the following tasks:
- _TODO: In 3-5 bullets, explain the steps of the ELK installation play. E.g., install Docker; download image; etc._
- STEP 1:  Ssh into the New-Jump-Box-Provisioner from the local host machine
- STEP 2:  Start and Attach the ansible docker container  
- STEP 3:  Once In Root You Will  /etc/ansible/roles and create the ELK playbook (ELK_Playbook.yml)
- STEP 4:  Run the ELK_playbook.yml by typing “ansible-playbook ELK_playbook.yml” and then ssh into the ELK-VM to verify the configuration



### Target Machines & Beats
This ELK server is configured to monitor the following machines:
- : List the IP addresses of the machines you are monitoring_
    DVMA-VM1 & DVMA-VM2

We have installed the following Beats on these machines:
- : Filebeats & Metricbeats

These Beats allow us to collect the following information from each machine:
- _: Metricbeat collects the statistics from your web activity and ships it to either Elasticsearch or Logstash. Filebeat monitors the locations or log files that are specified by the user, and after it collects log events, the data is forwarded to either Elasticsearch or Logstash for indexing.

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the filebeat-configuration.yml file to  /etc/ansible/roles/files.
- Update the filebeat-congiguration file to include ELK private IP in lines 1106 and 1806. 
- Run the playbook, and navigate to http://75.60.200.122:5601

_: Answer the following questions to fill in the blanks:_
- _Which file is the playbook? Where do you copy it?
The playbook file is Filebeat-playbook.yml you copy it to /etc/ansible/roles
- _Which file do you update to make Ansible run the playbook on a specific machine? How do I specify which machine to install the ELK server on versus which to install Filebeat on?
The filepath to run the ansible playbook on a specific machine is /etc/ansible/hosts file  (IP of the Virtual Machines). 
- _Which URL do you navigate to in order to check that the ELK server is running?
 http://75.60.200.122:5601

_As a **Bonus**, provide the specific commands the user will need to run to download the playbook, update the files, etc._
  - name: installing and launching filebeat
    hosts: webservers
    become: true
    tasks:
    - name: download filebeat deb
      command: curl -L -O https://artifacts.elastic.co/downloads/beats/filebeat/filebeat-7.7.1-amd64.deb
    - name: install filebeat deb
      command: dpkg -i filebeat-7.7.1-amd64.deb
    - name: drop in filebeat.yml
      copy:
       src: ./files/filebeat-configuration.yml
       dest: /etc/filebeat/filebeat.yml
    - name: enable and configure system module
      command: filebeat modules enable system
    - name: setup filebeat
      command: filebeat setup
    - name: start filebeat service
      command: service filebeat start
To run the playbook: ansible-playbook filebeat-playbook.yml 



