# Jesse-Fernandez
Project #1

Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

TODO: Update the path with the name of your diagram](Images/diagram_filename.png)

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the _.yml__ file may be used to install only certain pieces of it, such as Filebeat.

   The ansible-playbooks elk.yml and the filebeat-playbook.yml are needed to create and implement the Elk-Server.

This document contains the following details:
- Description of the Topology
- Access Policies
- ELK Configuration
- Beats in Use
- Machines Being Monitored
- How to Use the Ansible Build


Description of the Topology

- The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

- Load balancing ensures that the application will be highly __available__, in addition to restricting __access__ to the network.

 What aspect of security do load balancers protect?

Load Balancing contributes to the availability aspect of security in regards to the CIA Triad. 

What is the advantage of a jump box?

The advantage of a JumpBox is the origination point for launching administrative tasks, which sets the JumpBox as a SAW (Secure Admin Workstation). All administrators when conducting any administrative task will be required to connect to the JumpBox.

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the ___data__ and system __logs___.

 What does Filebeat watch for?

Filebeat watches for log files/locations and collects log events.

What does Metricbeat record?

Metricbeat records metric and statistical data from the operating system and from services running on the server.

The configuration details of each machine may be found below.

| Name       | IP Address | Usage        | OS  |
|---             |---              |---               |---        |
| JumpBox | 10.0.0.4   | Ansible      | Linux |
| WEB-1   | 10.0.0.7   | Docker-DVWA  | Linux |
| WEB-2   | 10.0.0.8  | Docker-DVWA  | Linux |
| WEB-3   | 10.0.0.9   | Docker-DVWA  | Linux |
| ELk-Server | 10.1.0.4  | Elk          | Linux I


Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the __JumpBox__ machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:

-Personal IP Address : 73.188.63.31

Machines within the network can only be accessed by SSH.

- The only machine that is able to connect to the Elk-Server is the JumpBox from private IP.

A summary of the access policies in place can be found in the table below.

| Name       | Publicly Accessible | Allowed IP Addresses   |
|----------           |--------------------|----------------------  |
|Jump Box       | No                  | Personal IP Only |
| WEB-1          | No                  | 10.0.0.4               |
| WEB-2          | No                  | 10.0.0.4               |
| WEB-3          | No                  | 10.0.0.4               |
| ELk-Server | No                    | 10.0.0.4 & Personal IP |

Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because…

The main advantages of automating configuration through ansible is the ease of use and an easy learning curve. Using playbooks you are able to configure multiple machines through the use of a single command after initial configuration.

The playbook implements the following tasks:

 Create a New VM (Elk-Server). You will need the Private IP to SSH into the VM and the Public IP to connect to the Kibana Portal.
Download and Configure the "elk-docker" container. You will need to add a new group [elkservers] and the private IP to the group. Then you need to create a new ansible-playbook that will download, install, configure the "Elk-Server" to map ports and start the container.
Launch and expose the container, you can verify that the container is up and running by SSHing into the container from your JumpBox. Once you are in the [Elk-Server] run the command [sudo docker ps]
Create new Inbound Security Rules to allow Ports: 5601 and 9200 "The Inbound Security Rules should allow access from your Personal Network"
Open a new browser and type in the [Public IP:5601] to access the Kibana Portal Site

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.


Target Machines & Beats

This ELK server is configured to monitor the following machines:

10.0.0.7, 10.0.0.8, 10.0.0.9

We have installed the following Beats on these machines:

Filebeat and Metricbeat

These Beats allow us to collect the following information from each machine:

 Filebeat forwards and centralizes log data. Filebeat monitors log files or locations you specify, collects log events, and forwards them.

Metricbeat collects metrics from the operating system and from services running on the server. Metricbeat then takes the metrics and statistics that it collects and ships them to the output that you specify.


Using the Playbook

In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:

- Copy the __filebeat.yml__ file to the __/etc/ansible/roles/files/ directory__.

- Update the __configuration file__ to include the Private IP of the Elk-Server to the ElasticSearch and Kibana sections of the configuration file.

- Run the playbook, and navigate to __ELk-Server__ to check that the installation worked as expected. [docker ps]

Answer the following questions to fill in the blanks:_

- _Which file is the playbook? Where do you copy it? 

The playbook is called [filebeat-playbook.yml] and you copy it to /etc/ansible/hosts

- _Which file do you update to make Ansible run the playbook on a specific machine? How do I specify which machine to install the ELK server on versus which to install Filebeat on? 
The file you need to update is the filebeat.yml file which is a configuration file that will be dropped into the Elk-Server during the run of the ansible-playbook. When you update the host.cfg file in the ansible directory you will need to create a new group called [elkservers] and add the Private IP of the Elk-Server to the group. Then when configuring the filebeat.yml file you need to designate the Private IP of the Elk-Server in two lines of the .yml file. Lines 1106 and 1806 are needed to be updated with the Private IP.

- _Which URL do you navigate to in order to check that the ELK server is running? 

The URL to use to verify the Elk-Server is running is the Public IP (73.188.63.31:5601)


![Project 1 Image #2](https://user-images.githubusercontent.com/74419149/112837430-e271b280-9069-11eb-8fae-cd5141c957af.PNG)

![Project 1 Image](https://user-images.githubusercontent.com/74419149/112837450-e7cefd00-9069-11eb-9061-ed956a5e0846.PNG)

![Project 1 Image #3](https://user-images.githubusercontent.com/74419149/112837459-e998c080-9069-11eb-9a77-ce08f5197392.PNG)




