# Automated CI/CD Pipeline with Jenkins

## Summary
This project sets up an automated Continuous Integration/Continuous Deployment (CI/CD) pipeline for an e-commerce portal using Jenkins. It automates:
- Code integration and testing.
- Building Docker images after successful tests.
- Deploying the containerized application to a test environment via Kubernetes and Ansible.

## Workflow
1. **Push Dockerfile to GitHub Repository**:
   - Set up GitHub webhooks to automatically send updates to Jenkins.
2. **Code Integration**:
   - Jenkins pulls updated files from the repository when developers push or modify code.
3. **Deployment**:
   - Jenkins sends the files to Kubernetes and Ansible servers for containerized deployment.
4. **Website Access**:
   - The deployed application is accessible via a public IP from the Kubernetes cluster.

## Architecture
- **Three Instances Required**:
  - `Jenkins` (t2.micro)
  - `Docker & Ansible` (t2.micro)
  - `Kubernetes` (t2/t3.medium)

## Pre-Requisites
- Git
- Linux System
- Docker Hub Account
- Ansible
- Kubernetes

## Required Files
1. `Dockerfile`
2. `deployment.yml`
3. `service.yml`
4. `ansible.yml`

---

## Setup and Installation

### Jenkins Server
```bash
sudo apt update
sudo apt install fontconfig openjdk-17-jre
java -version
sudo wget -O /usr/share/keyrings/jenkins-keyring.asc \
https://pkg.jenkins.io/debian/jenkins.io-2023.key
echo "deb [signed-by=/usr/share/keyrings/jenkins-keyring.asc]" \
https://pkg.jenkins.io/debian binary/ | sudo tee \
/etc/apt/sources.list.d/jenkins.list > /dev/null
sudo apt-get update
sudo apt-get install jenkins
```

## Ansible & Docker Server Installation

### Install Ansible
To install Ansible, follow these steps:

```bash
sudo apt update
sudo apt install software-properties-common
sudo add-apt-repository --yes --update ppa:ansible/ansible
sudo apt install ansible
```

### Install Docker
To install Docker, follow these steps:

```bash
sudo apt install docker.io -y
docker --version
sudo usermod -aG docker ubuntu
cat /etc/group
newgrp docker
docker images
sudo systemctl status docker
```

## Result
After deployment, access your application by copying the Kubernetes public IP along with the port (e.g., `http://<public-ip>:31200`) in your browser.

