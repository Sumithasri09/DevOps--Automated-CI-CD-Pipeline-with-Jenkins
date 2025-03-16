Automated CI/CD Pipeline with Jenkins
Summary
This project implements a Continuous Integration/Continuous Deployment (CI/CD) pipeline for an e-commerce portal using Jenkins. The pipeline automates code testing, builds Docker images after successful tests, and deploys the containerized application to a test environment.

Features
Automated Code Integration: Leveraging Git webhooks to trigger Jenkins pipelines automatically upon code changes.

Docker Integration: Builds Docker images and pushes them to Docker Hub for containerized deployment.

Kubernetes Deployment: Deploys the application in Kubernetes clusters with two replica pods for high availability.

Ansible Automation: Manages Kubernetes deployments using Ansible playbooks.

Scalable Architecture: Utilizes three instances for Jenkins, Docker+Ansible, and Kubernetes for efficient pipeline execution.

Pre-Requisites
Git

Linux operating system

Docker Hub account

Ansible

Kubernetes

Setup and Installation
Jenkins Server
Update the package list:

bash
sudo apt update
Install Java:

bash
sudo apt install fontconfig openjdk-17-jre
java -version
Add Jenkins keyring and repository:

bash
sudo wget -O /usr/share/keyrings/jenkins-keyring.asc \
https://pkg.jenkins.io/debian/jenkins.io-2023.key
echo "deb [signed-by=/usr/share/keyrings/jenkins-keyring.asc]" \
https://pkg.jenkins.io/debian binary/ | sudo tee \
/etc/apt/sources.list.d/jenkins.list > /dev/null
Install Jenkins:

bash
sudo apt-get update
sudo apt-get install jenkins
Ansible and Docker Server
Ansible:

bash
sudo apt update
sudo apt install software-properties-common
sudo add-apt-repository --yes --update ppa:ansible/ansible
sudo apt install ansible
Docker:

bash
sudo apt install docker.io -y
docker --version
sudo usermod -aG docker ubuntu
Files Required
Dockerfile

deployment.yml

service.yml

ansible.yml

Workflow
Push the Dockerfile to a GitHub repository and set up webhooks to trigger Jenkins.

Jenkins pulls the code, builds Docker images, and pushes them to Docker Hub.

Ansible playbooks deploy the application to Kubernetes using YAML files (deployment.yml and service.yml).

Access the deployed application through a browser using Kubernetes' public IP and port configuration.

Contributions
Contributions are welcome! Please create an issue or a pull request for any enhancements.

License
This project is open-source. Feel free to use and modify as needed.
