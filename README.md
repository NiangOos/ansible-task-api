# ansible-task-api

Ansible playbook for deploying [task-api](https://github.com/NiangOos/task-api) on an Ubuntu VM.

## Files

- `inventory.ini` - Target host configuration
- `playbook.yml` - Deployment playbook

## What the Playbook Does

1. Updates system packages
2. Installs Docker and MySQL
3. Creates the `taskdb` MySQL database
4. Pulls `niangoos/task-api:latest` from Docker Hub
5. Runs the container on port 8085 (restart: always)
6. Verifies the application is responding

## Setup

Edit `inventory.ini` with your VM's IP address:

```ini
[servers]
ubuntu-vm ansible_host=YOUR_VM_IP ansible_user=ubuntu ansible_ssh_private_key_file=~/.ssh/id_rsa
```

## Run

```bash
ansible-playbook -i inventory.ini playbook.yml
```

## Requirements

- Ansible installed on the control machine
- SSH access to the target Ubuntu VM
- Target VM with internet access (to pull Docker image and install packages)
