## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

![TODO: Update the path with the name of your diagram]()

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the _____ file may be used to install only certain pieces of it, such as Filebeat.

  - TODO: Enter the playbook file.
  /etc/ansible/install-elk.yml

This document contains the following details:
- Description of the Topology
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly _____, in addition to restricting _____ to the network.
- TODO: What aspect of security do load balancers protect? What is the advantage of a jump box?
- Load balancers protect the integrity of the servers that are connected to it.  Load balancers are used to prevent Denial of Service (DoS) attacks.

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the _____ and system _____.
- TODO: What does Filebeat watch for? 
- Filebeat watches for any changes that are made into the VMs and records when the changes were made.
- TODO: What does Metricbeat record? 
- Metricbeat records statistics regarding CPU and memory usage as well as how long the virtual machines have been active otherwise known as uptime.

The configuration details of each machine may be found below.
Note: Use the [Markdown Table Generator](http://www.tablesgenerator.com/markdown_tables) to add/remove values from the table.

| Name     | Function | IP Address | Operating System |
|----------|----------|------------|------------------|
| Jump Box | Gateway  | 10.0.0.4   | Linux            |
| Web-VM1  | Server   | 10.0.0.5   | Linux            |
| Web-VM2  | Server   | 10.0.0.6   | Linux            |
| Web-VM3  | Server   | 10.0.0.7   | Linux            |
| Elkserver| Server   | 10.1.0.4   | Linux            |

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the Jump Box machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:
- _TODO: Add whitelisted IP addresses_
- The IP address that is allowed to access the Jump Box CM is the local address of your host machine

Machines within the network can only be accessed by secure shell connection.
- TODO: Which machine did you allow to access your ELK VM? What was its IP address?
- The Jump-Box is the only machine that is allowed to access te ELK VM.  The IP address of the Jump-Box is 10.0.0.4.

A summary of the access policies in place can be found in the table below.

| Name     | Publicly Accessible | Allowed IP Addresses |
|----------|---------------------|----------------------|
| Jump Box | Yes                 | Home IP address      |
| Web-VM1  | No                  | 10.0.0.4             |
| Web-VM2  | No                  | 10.0.0.4             |
| Web-VM3  | No                  | 10.0.0.4             |
| Elk Server| No                 | 10.0.0.4             |

### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because...
- TODO: What is the main advantage of automating configuration with Ansible?

-The advantage of using an automated configuration with Ansible is that run multiple commands by inputting them in a playbook.

The playbook implements the following tasks:
- TODO: In 3-5 bullets, explain the steps of the ELK installation play. E.g., install Docker; download image; etc.

- First, docker.io has to be installed using an Ansible playbook.
- Second, python-pip interpreter needs to be installed.
- Third, the docker container needs to be installed
- In the Ansible playbook, the amount of memory needs to be increased for the ELK server to operate.  It can be done by inputting the command, “sysctl -w vm.max_map_count=262144”.
- Lastly, the Ansible playbook has to run by using the following command: “ansible-playbook install-elk.yml”.

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

![TODO: Update the path with the name of your screenshot of docker ps output](Images/docker_ps_output.png)

### Target Machines & Beats
This ELK server is configured to monitor the following machines:
- TODO: List the IP addresses of the machines you are monitoring
- Web-VM1 is 10.0.0.5 
- Web-VM2 is 10.0.0.6
- Web-VM3 is 10.0.0.7

We have installed the following Beats on these machines:
- TODO: Specify which Beats you successfully installed
- Filebeat and Metricbeat were installed

These Beats allow us to collect the following information from each machine:
- _TODO: In 1-2 sentences, explain what kind of data each beat collects, and provide 1 example of what you expect to see. E.g., `Winlogbeat` collects Windows logs, which we use to track user logon events, etc._
- Filebeat collects the changes that are done inside the system while Metricbeat collects data such as CPU usage, the percentage of memory that’s being used, as well as uptime.

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the filebeat.configuration.yml file to /etc/ansible/file.
- Update the hosts file to include the IP addresses of the web servers and elk server.
- Run the playbook, and navigate to www.publicip:5601 to check that the installation worked as expected.

TODO: Answer the following questions to fill in the blanks:
- Which file is the playbook? Where do you copy it?
- The file is named “filebeat-configuration.yml”.  It needs to be copied to the /etc/ansible/file folder.

- Which file do you update to make Ansible run the playbook on a specific machine? How do I specify which machine to install the ELK server on versus which to install Filebeat on?
- The file that needs to be updated is the “hosts” file that is located in the /etc/ansible directory.  The changes that need to be made are the addition of the webserver and elkserver ip addresses.

- Which URL do you navigate to in order to check that the ELK server is running?
- The url is www.publicip:5601 

_As a **Bonus**, provide the specific commands the user will need to run to download the playbook, update the files, etc._
