## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

![network topology](https://github.com/facoffey/Project-1-/raw/main/network.PNG)

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the hosts file may be used to install only certain pieces of it, such as Filebeat.

  [sample playbook file](https://github.com/facoffey/Project-1-/blob/main/ELKconfig/filebeat-playbook.yml)

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
-The way that the network is built allows for only the jumpbox to be able to connect to all servers on the network.  By using SSH keys and firewalls we can ensure that the network is highly protected from intrusion.

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the server and system files.
- What does Filebeat watch for? Changes to files, which files changed and when. Filebeat is used to collect log files from very specific files. 
- Metricbeat allows monitoring. 

The configuration details of each machine may be found below.


| Name     | Function | IP Address | Operating System |
|----------|----------|------------|------------------|
| Jump Box | Gateway  | 10.0.0.4   | Linux            |
| VM 1     |webserver | 10.0.0.5   | Linux            |
| VM 2     |webserver | 10.0.0.6   | Linux            |
| VM 3     |webserver | 10.0.0.8   | Linux            |
|ELk Server Elk stack  10.1.0.4


### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the Jumpbox machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses: 40.121.136.24
-Designated command computer with private key.

Machines within the network can only be accessed by jumpbox. Only the Jumpbox can accept direct SSH connections from the internet. 
- _
VM 1 10.0.0.5  VM 2  10.0.0.6 /Elk 10.1.0.4 Jumpbox Provisioner 40.121.136.24
A summary of the access policies in place can be found in the table below.

| Name     | Publicly Accessible | Allowed IP Addresses |
|----------|---------------------|----------------------|
| Jump Box | No                  | Designated control   |
| Web VM's | Yes                 | ANY                  |
|          |                     |                      |

### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because...
- _What is the main advantage of automating configuration with Ansible? _The primary benefit of Ansible is it allows IT administrators to automate away the drudgery from their daily tasks. That frees them to focus on efforts that help deliver more value to the business by spending time on more important tasks

The playbook implements the following tasks:
- _TODO: In 3-5 bullets, explain the steps of the ELK installation play. E.g., install Docker; download image; etc._
- ...Install docker i.o and python3-pip
- ...Install Elk
-    Configure the Server programs
-    Enable docker to run on start.
    
The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

![TODO: Update the path with the name of your screenshot of docker ps output](Images/docker_ps_output.png)

### Target Machines & Beats
This ELK server is configured to monitor the following machines:
-10.0.0.4 10.0.0.5 10.0.0.6
We have installed the following Beats on these machines:
- _Filebeat
- Metricbeat 
These Beats allow us to collect the following information from each machine:
Filebeat monitors the log files or locations that you specify, collects log events, and forwards them either to Elasticsearch or Logstash for indexing. 
Metricbeat is a lightweight shipper that you can install on your servers to periodically collect metrics from the operating system and from services running on the server. You can see this in Elasticsearch or Logstash. 

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the _Playbook.yml file to the ansible container in the JumpBox.
- Update the ansible.cfg file to include the IP's of the three machines Web 1 10.0.0.5 Web 2 10.0.0.6  Web 3 10.0.0.8
- Run the playbook, and navigate to ansible container to check that the installation worked as expected. http://40.83.134.116/app/kibana

_TODO: Answer the following questions to fill in the blanks:_
- _Which file is the playbook? Filebeat and Metricbeat.  Where do you copy it? In the Ansible container.
- _Which file do you update to make Ansible run the playbook on a specific machine? How do I specify which machine to install the ELK server on versus which to install Filebeat on?_ Add the Elk's IP address to the anisble.cfg file. 
- _Which URL do you navigate to in order to check that the ELK server is running?  http://40.83.134.116/app/kibana

_As a **Bonus**, provide the specific commands the user will need to run to download the playbook, update the files, etc._
