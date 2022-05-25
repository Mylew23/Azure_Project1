# Azure_Project1
## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

![Diagrams/Project%201%20Azure%20Diagram.png](Diagrams/Project%201%20Azure%20Diagram.png)

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the YML file may be used to install only certain pieces of it, such as Filebeat.

TODO: Enter the playbook file.
This document contains the following details:
Description of the Topologu
Access Policies
ELK Configuration
Beats in Use
Machines Being Monitored
How to Use the Ansible Build
### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly available and effiecient, in addition to restricting unwanted access to the network.

What aspect of security do load balancers protect? 


A Load balancer distributes incoming requests or application traffic over web servers. It ensures the availability aspect for the webservers 🔺 (CIA Triad) 🔺. Load balancer will mitigate or reduce Distributed Denial of service 🛑 (DDoS) ⚠️ attack on one of the servers making it unavailable, which protects the system from any attacking traffic or penetrations by hackers. 

What is the advantage of a jump box?


The JumpBox is a secure computer that admins can connect to before giving out administrative tasks. An advantage of the Jump box is allowing a  🖥 Secure Admin Workstation 🖥  (SAW). Only specific IP addresses and port 22 (SSH) will be allowed to access the JumpBox being secured and monitored. To give out any administrative task admins must connect to the JumpBox.

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the logs and system metrics.
What does Filebeat watch for?

Filebeat watches for log files or locations and collect log events. After capturing logs and data it is then sent to the ELK Server. The filebeat watches for any informational changes in the system.

What does Metricbeat record?

Metricbeat records metric and statistical data from the server then ships them to the output that you specify such as Elasticsearch or Logstash on ELK server. Metricbeat also help monitor metrics on the system and services running on the server.


The configuration details of each machine may be found below.
_Note: Use the [Markdown Table Generator](http://www.tablesgenerator.com/markdown_tables) to add/remove values from the table_.

| Name     | Function | IP Address | Operating System |
|----------|----------|------------|------------------|
| Jump Box | Gateway  | 10.1.0.4   |Linux             |
| WEB1     | Webserver| 10.1.0.6   |Linux             |
| WEB2     | Webserver| 10.1.0.7   |Linux             |
| ELKVM    |ELK Server| 10.2.0.4   |Linux             |

### Access Policies

The machines on the internal network are not exposed to the public Internet.

Only the JumpBox machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:

Add whitelisted IP addresses


- Personal IP address shared with the Jumpbox through SSH port 22

Machines within the network can only be accessed by the JumpBox through SSH.

Which machine did you allow to access your ELK VM? 


- Jumpbox

What was its IP address?

📪10.1.0.4📪


A summary of the access policies in place can be found in the table below.

| Name     | Publicly Accessible | Allowed IP Addresses |
|----------|---------------------|----------------------|
| Jump Box | Yes                 | SSH Admin personal IP|
| Web1     | No                  | 10.1.0.6             |
| Web2     | No                  | 10.1.0.7             |
| ELKVM    | No                  | 10.2.0.4             |

### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because...
 What is the main advantage of automating configuration with Ansible?
 
- The installation could deploy multiple servers without having to touch each server using a single playbook

The playbook implements the following tasks:


  -	Install Docker.io and pip3
  
	-	Increases VM memory module
	
	-	Download and Configure ELK Docker container with port 5601, 9200, 5044 

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

![images/Sudo%20docker%20ps.png](images/Sudo%20docker%20ps.png)

### Target Machines & Beats
This ELK server is configured to monitor the following machines:


🖥WEB1 - 10.1.0.6🖥
🖥WEB2 - 10.1.0.7🖥

We have installed the following Beats on these machines:

![Ansible/Metricbeat-playbook.txt](Ansible/Metricbeat-playbook.txt)


![images/metricbeat%20docker%20complete%20.png](images/metricbeat%20docker%20complete%20.png)


![Ansible/Filebeat-playbook.yml.txt](Ansible/Filebeat-playbook.yml.txt)


![images/%20filebeat%20status%20start.png](images/%20filebeat%20status%20start.png)

TODO: Specify which Beats you successfully installed
These Beats allow us to collect the following information from each machine:
TODO: In 1-2 sentences, explain what kind of data each beat collects, and provide 1 example of what you expect to see. E.g., `Winlogbeat` collects Windows logs, which we use to track user logon events, etc.
### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned:

SSH into the control node and follow the steps below:
Copy the configuration file to the ansible.
Update the configuration file to include the Private IP address of the ELK-server [10.2.0.4]
Run the playbook, and navigate to ____ to check that the installation worked as expected.
TODO: Answer the following questions to fill in the blanks:
Which file is the playbook? Where do you copy it?
Which file do you update to make Ansible run the playbook on a specific machine? How do I specify which machine to install the ELK server on versus which to install Filebeat on?
_Which URL do you navigate to in order to check that the ELK server is running?
As a **Bonus**, provide the specific commands the user will need to run to download the playbook, update the files, etc.
