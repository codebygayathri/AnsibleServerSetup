# Ansible Server Configuration Automation

## Overview

This project demonstrates infrastructure automation using Ansible on AWS EC2. A dedicated Ansible Control Node was configured to manage three Ubuntu EC2 managed nodes through SSH key-based authentication.

Using Ansible playbooks, common server administration tasks such as package installation, service management, user creation, directory creation, and timezone configuration were automated across multiple servers.

## Features

- Manage multiple AWS EC2 instances using one control node
- Passwordless SSH authentication
- Inventory-based server management
- Install common software packages automatically
- Configure and manage Nginx service
- Configure and manage Docker service
- Create Linux users with sudo privileges
- Create directories automatically
- Configure server timezone
- Automate repetitive server administration tasks


## Technologies and Tools

- Ansible
- Ubuntu Linux
- AWS EC2
- SSH

## Architecture

```text
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
```

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

## Project Structure


```text
ansible-server-setup
├── README.md
├── ansible.cfg
├── inventory
│   └── hosts.ini
├── playbooks
│   └── server-setup.yml

```

## Screenshots

### AWS EC2 Instances

<img width="1065" height="238" alt="important3" src="https://github.com/user-attachments/assets/1e4e7c24-0360-4ca8-bdbf-a1c3f84b8bcd" />

### Successful Ansible Ping

<img width="932" height="606" alt="important1" src="https://github.com/user-attachments/assets/bd8664e9-a4f5-487d-aa18-c644265357d0" />

## Design Principle

### Infrastructure as Code (IaC)

The project follows the Infrastructure as Code (IaC) approach by defining server configuration as Ansible playbooks instead of performing manual configuration. This ensures consistent, repeatable, and automated infrastructure provisioning across multiple servers.


## Future Enhancements


- Use Ansible Galaxy roles.
- Automate application deployment.
- Configure load balancers.
- Manage larger server clusters.


## Deployment Environment

The project was implemented using AWS EC2 Ubuntu Linux instances. One EC2 instance acted as the Ansible Control Node, while three EC2 instances were configured as Managed Nodes. Communication between nodes was established securely using SSH key-based authentication.
