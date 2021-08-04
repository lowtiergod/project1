## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

![TODO: Update the path with the name of your diagram](Images/diagram_filename.png)

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the _____ file may be used to install only certain pieces of it, such as Filebeat.

  - _TODO: fresh-elk.yml._

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
- _TODO: What aspect of security do load balancers protect? System availability. What is the advantage of a jump box? A secure computer that an admin
can access before they do any administrative tasks on the network or act as a origin point to connect to other networks or untrusted environments 

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the network and system files.
- _TODO: What does Filebeat watch for? log files and log events
- _TODO: What does Metricbeat record? metrics and statistics

The configuration details of each machine may be found below.
_Note: Use the [Markdown Table Generator](http://www.tablesgenerator.com/markdown_tables) to add/remove values from the table_.

| Name          | Function                             | IP Address              | Operating System     | 
|---------------|--------------------------------------|-------------------------|----------------------|
| Jump Box      | Docker/Ansible                       | 20.85.230.121           | Linux (ubuntu 20.04) |
| Web-1         | DVWA                                 | 20.106.157.237 10.0.0.7 | Linux (ubuntu 20.04) |
| Web-2         | DVWA                                 | 20.106.157.237 10.0.0.8 | Linux (ubuntu 20.04) |
| ELK VM        | ELK STACK                            | 13.68.87.15 10.1.0.7    | Linux (ubuntu 20.04) |
| Load Balancer | Filter traffic between Web-1 & Web-2 | 20.106.157.237          |                      |

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the jumpbox machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses: 
- _TODO: 154.3.250.186

Machines within the network can only be accessed by SSH.
- _TODO: Which machine did you allow to access your ELK VM? Ansible container. What was its IP address? 20.85.230.121

A summary of the access policies in place can be found in the table below.

| Name    | Publicly Accessible | Allowed IP Addresses |
|---------|---------------------|----------------------|
| Jumpbox | Yes                 | 154.3.251.23         |
| Web-1   | Yes                 | 154.3.251.23         |
| Web-2   | Yes                 | 154.2.251.23         |
| Elk VM  | Yes                 | 154.3.251.23         |

### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because...
- _TODO: What is the main advantage of automating configuration with Ansible? You can create the script once and deploy it to many machines.

The playbook implements the following tasks:
- _TODO: In 3-5 bullets, explain the steps of the ELK installation play. E.g., install Docker; download image; etc._
- install docker
- install python & pip
- increase virtual memory on the vm
- download and launch a docker container with elk

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

![TODO: Update the path with the name of your screenshot of docker ps output](Images/docker_ps_output.png)

### Target Machines & Beats
This ELK server is configured to monitor the following machines:
- _TODO: List the IP addresses of the machines you are monitoring 10.0.0.7 & 10.0.0.8

We have installed the following Beats on these machines:
- _TODO: Specify which Beats you successfully installed. Filebeat & Metricbeat

These Beats allow us to collect the following information from each machine:
- _TODO: In 1-2 sentences, explain what kind of data each beat collects, and provide 1 example of what you expect to see. E.g., `Winlogbeat` collects Windows logs, which we use to track user logon events, etc._
Filebeat collects log events and monitors the log files, which we use to monitor system logs, wifi logs, error logs etc.

Metricbeat periodically collect metrics from the operating systems and from services running on the server. Metrics we get to collect and monitor for 
example are cpu, load, memory, network, process, etc.
### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the public key of the ansible container to virtual machine.
- Update the hosts file to include ip address of the system.
- Run the playbook, and navigate to docker to check that the installation worked as expected.

_TODO: Answer the following questions to fill in the blanks:_
- _Which file is the playbook? fresh-elk.yml Where do you copy it? /etc/ansible
- _Which file do you update to make Ansible run the playbook on a specific machine? /etc/ansible/hosts. How do I specify which machine to install the ELK server on versus which to install Filebeat on? under the "[webservers]"
section, create "[elk]" with the ip addresses of the machine.
- _Which URL do you navigate to in order to check that the ELK server is running? http://[IP]/app/kibana#/home

_As a **Bonus**, provide the specific commands the user will need to run to download the playbook, update the files, etc._

