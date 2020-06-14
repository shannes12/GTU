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
- What is the advantage of a jump box?_

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the infrastructure and system logs.
- _TODO: What does Filebeat watch for?_
- _TODO: What does Metricbeat record?_



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
|Elk-Server|      Yes            |10.0.0.4                      |
                                  10.0.0.5
                                  10.0.0.6
                                  10.0.0.7
### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because...
- What is the main advantage of automating configuration with Ansible?_

The playbook implements the following tasks:
- _TODO: In 3-5 bullets, explain the steps of the ELK installation play. E.g., install Docker; download image; etc._
- ...
- ...


### Target Machines & Beats
This ELK server is configured to monitor the following machines:
- : List the IP addresses of the machines you are monitoring_
    DVMA-VM1 & DVMA-VM2

We have installed the following Beats on these machines:
- : Filebeats & Metricbeats

These Beats allow us to collect the following information from each machine:
- _TODO: In 1-2 sentences, explain what kind of data each beat collects, and provide 1 example of what you expect to see. E.g., `Winlogbeat` collects Windows logs, which we use to track user logon events, etc._

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the _____ file to _____.
- Update the _____ file to include...
- Run the playbook, and navigate to ____ to check that the installation worked as expected.

_TODO: Answer the following questions to fill in the blanks:_
- _Which file is the playbook? Where do you copy it?_
- _Which file do you update to make Ansible run the playbook on a specific machine? How do I specify which machine to install the ELK server on versus which to install Filebeat on?_
- _Which URL do you navigate to in order to check that the ELK server is running?

_As a **Bonus**, provide the specific commands the user will need to run to download the playbook, update the files, etc._



