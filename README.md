# Ansible Server Configuration Automation

## Overview

This project demonstrates infrastructure automation using Ansible on AWS EC2. A dedicated Ansible Control Node was configured to manage three Ubuntu EC2 managed nodes through SSH key-based authentication.

Using Ansible playbooks, common server administration tasks such as package installation, service management, user creation, directory creation, timezone configuration, and file deployment were automated across multiple servers.

## Features

- Configure an Ansible Control Node
- Manage multiple AWS EC2 instances
- Passwordless SSH authentication
- Inventory-based server management
- Execute Ansible ad-hoc commands
- Install common software packages automatically
- Configure and manage Nginx service
- Configure and manage Docker service
- Create Linux users with sudo privileges
- Create directories automatically
- Configure server timezone
- Copy configuration files to managed nodes
- Automate repetitive server administration tasks


## Technologies and Tools

- Ansible
- Ubuntu Linux
- AWS EC2
- SSH


## Architecture


                 AWS Cloud

         +-----------------------+
         |   Control Node        |
         | Ubuntu + Ansible      |
         +----------+------------+
                    |
             SSH Key Authentication
      ┌─────────────┼─────────────┐
      │             │             │
      ▼             ▼             ▼
+------------+ +------------+ +------------+
| Managed-1  | | Managed-2  | | Managed-3  |
| Ubuntu EC2 | | Ubuntu EC2 | | Ubuntu EC2 |
+------------+ +------------+ +------------+


## Project Workflow

1. Launch one AWS EC2 instance as the Ansible Control Node.
2. Launch three Ubuntu EC2 instances as Managed Nodes.
3. Configure SSH key-based authentication.
4. Configure the Ansible inventory.
5. Verify connectivity using Ansible ping.
6. Execute Ansible playbooks.
7. Automatically configure all managed servers.

## Automated Tasks

The playbook performs the following operations:

- Gather server facts
- Update the APT package cache
- Install:
  - Git
  - Curl
  - Vim
  - Nginx
  - Docker
- Start and enable Nginx
- Start and enable Docker
- Create Linux users with sudo privileges
- Create application directories
- Configure server timezone
- Copy configuration files to managed nodes

## Project Structure


  ansible-server
  ├── ansible.cfg
  ├── inventory
  │   └── hosts.ini  (was hidden as it contains instance's public IP)
  |-- key.pem
  ├── playbooks
  │   ├── setup.yml
  │   └── enhanced-server-setup.yml
  ├── files
  │   └── sample.conf
  └── README.md


---

## Screenshots

### AWS EC2 Instances

### SSH Connectivity

### Inventory Configuration

### Successful Ansible Ping

### Playbook Execution

### Nginx Installed on Managed Nodes

### Docker Installed on Managed Nodes

### Created Users

### Directory Structure

### Git Repository

---

## Design Principle

### Infrastructure as Code (IaC)

The project follows the Infrastructure as Code (IaC) approach by defining server configuration as Ansible playbooks instead of performing manual configuration. This ensures consistent, repeatable, and automated infrastructure provisioning across multiple servers.

---

## Future Enhancements

- Implement Ansible Roles for modular playbooks.
- Use Ansible Galaxy roles.
- Automate application deployment.
- Configure load balancers.
- Integrate Ansible with Jenkins CI/CD.
- Manage larger server clusters.

---

## Deployment Environment

The project was implemented using AWS EC2 Ubuntu Linux instances. One EC2 instance acted as the Ansible Control Node, while three EC2 instances were configured as Managed Nodes. Communication between nodes was established securely using SSH key-based authentication.
