# On-Premise GitLab Instances - High Availability and Robust Storage Solutions with Keycloak SSO


## Purpose

This [Ansible](https://www.ansible.com/) playbook automates the deployment of a High Availability GitLab instance with Keycloak Single Sign-On (SSO). The setup includes multiple GitLab nodes for improved reliability and scalability. It uses Ansible roles and variables to make the deployment process modular and customizable. The Keycloak instance runs in a Docker container (see [the container images used](docs/container-images.md)), while GitLab is deployed directly. Additionally, a reverse proxy is configured to manage the traffic. 
This setup allows for seamless automation of infrastructure deployment while ensuring secure access through Keycloak.
The setup also includes Data Replication with DRBD and distributed storage with Ceph on de.NBI cloud.


## Prerequisites
- Ansible is installed on your control machine where you plan to run the playbook.
- Remote machines provisioned with a compatible OS.
- A domain name pointing to the IP address of the reverse proxy.
- SSH access to all target servers with sudo privileges.
- A basic understanding of GitLab and its architecture.
- The inventory file is configured with the target server details.


## Configuration
- Inventory File: Modify the inventory file with the target server details.
- In the `roles` repository, there are sub-repositories for GitLab, Keycloak, and nginix-proxy. Edit Variables, yml files, and config files located in each sub-repository to match your environment.

## Notes

Basically, this playbook aims to get you up-and-running with all the necessities around GitLab, without you having to do anything else.
- Ensure that your servers meet the hardware and software requirements for GitLab, Keycloak, DRBD, and Ceph.
- This playbook assumes a fresh installation. Ensure there is no conflicting software on the target servers.

## Post-Deployment Steps

1. **Access GitLab:**
	- URL: http://gitlab_instance_ip
	- Initial login credentials: admin / your_chosen_password

2. **Access Keycloak:**
	- URL: http://keycloak_instance_ip:8080
	- Initial login credentials: admin / admin

3. **DRBD and Ceph:**
	- Verify the status and health of DRBD and Ceph after the deployment.

## **Maintenance**
Regularly update the inventory files, yml files, and variables for any changes in the environment.
Check for updates to GitLab, Keycloak, DRBD, and Ceph. Update variables accordingly.

## Infrastructure Overview

Our GitLab DataHub installation utilizes the following components:

- **Denbi OpenStack:** An open-source cloud computing platform, providing scalable and flexible virtualized resources.
- **Ceph Storage:** A distributed object storage and file system designed to provide excellent performance, reliability, and scalability.


## Changes
This playbook evolves over time, sometimes with backward-incompatible changes.

When updating the playbook, refer to [the changelog](CHANGELOG.md) to catch up with what's new.

