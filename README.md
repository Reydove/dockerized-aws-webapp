# dockerized-aws-webapp
A secure Dockerized web application deployed on AWS EC2 using Ubuntu, Docker, NGINX, and basic cloud security practices
# Dockerized AWS Web Application

## Project Overview

This project demonstrates how to deploy a Dockerized web application on an AWS EC2 instance using Docker and NGINX.

The application was containerized using Docker, deployed on an Amazon EC2 cloud server, and made publicly accessible through AWS Security Group configuration.

This project was built to strengthen practical skills in:

* Cloud Engineering
* DevOps Fundamentals
* Docker Containerization
* Linux Server Administration
* AWS Infrastructure
* Networking & Security

---

# Architecture

```text
GitHub Repository
        ↓
AWS EC2 Instance
        ↓
Docker Engine
        ↓
NGINX Container
        ↓
Public Web Access
```

---

# Technologies Used

* AWS EC2
* Amazon Linux 2023
* Docker
* NGINX
* Git & GitHub
* Linux CLI
* SSH

---

# Project Files

## index.html

Contains the custom web page served by NGINX.

## Dockerfile

Defines the Docker image build instructions.

## README.md

Project documentation and deployment process.

---

# Dockerfile Used

```dockerfile
FROM nginx:alpine

COPY index.html /usr/share/nginx/html/index.html

EXPOSE 80
```

---

# Key Concepts Learned

## Docker Images

A Docker image acts as a reusable blueprint/template for containers.

## Docker Containers

A running instance of a Docker image.

## Port Mapping

Mapped EC2 port 80 to container port 80:

```bash
docker run -d -p 80:80 --name webapp dockerized-aws-webapp
```

## Security Groups

Configured AWS inbound rules to allow HTTP traffic on port 80.

## SSH Access

Connected securely to the EC2 instance using a `.pem` key pair.

---

# Deployment Steps

## 1. Launch EC2 Instance

* Created AWS EC2 instance
* Configured Security Group
* Allowed:

  * SSH (22)
  * HTTP (80)

---

## 2. SSH Into Server

```bash
ssh -i "docker-aws-key.pem" ec2-user@<PUBLIC-IP>
```

---

## 3. Install Docker

```bash
sudo dnf install docker -y
sudo systemctl start docker
sudo systemctl enable docker
```

---

## 4. Clone Repository

```bash
git clone https://github.com/Reydove/dockerized-aws-webapp.git
```

---

## 5. Build Docker Image

```bash
docker build -t dockerized-aws-webapp .
```

---

## 6. Run Docker Container

```bash
docker run -d -p 80:80 --name webapp dockerized-aws-webapp
```

---

## 7. Verify Running Container

```bash
docker ps
```

---

## 8. Test Application

```bash
curl localhost
```

Opened application publicly using:

```text
http://<EC2-PUBLIC-IP>
```

---

# Challenges Faced & Troubleshooting

## GitHub Authentication Issues

* Switched from HTTPS authentication to SSH authentication.

## Docker Permission Issues

* Resolved Docker daemon permission errors using Linux group permissions.

## Security Group Networking

* Fixed public access issue by allowing inbound HTTP traffic on port 80.

## Linux Package Management

* Learned the difference between:

  * `apt` (Ubuntu/Debian)
  * `dnf` (Amazon Linux/Red Hat)

---

# What I Learned

Through this project I learned:

* How cloud servers work
* How Docker containerization works
* How to deploy applications on AWS
* How networking and port exposure work
* How Linux permissions and services operate
* How to troubleshoot real infrastructure issues
* The difference between Docker images and containers
* How GitHub integrates into deployment workflows

---

# Future Improvements

* Add CI/CD using GitHub Actions
* Add HTTPS with SSL/TLS
* Add custom domain using Route53
* Deploy multi-container applications
* Learn Kubernetes orchestration
* Implement Infrastructure as Code using Terraform

---

# Author

Mobolaji Habib

GitHub:
https://github.com/Reydove
.
