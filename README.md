# CI/CD Pipeline with Docker and GitHub Actions

Automated pipeline for building, versioning, and deploying containerized web applications using Docker, GitHub Actions, and AWS.

## Overview

This project implements a complete CI/CD workflow:
- **Containerization:** Angular application packaged in Docker
- **Continuous Integration:** GitHub Actions builds and pushes images to DockerHub on every push
- **Semantic Versioning:** Git tags trigger versioned releases for rollback capability
- **Continuous Deployment:** Webhooks automatically deploy new images to AWS EC2 instance

## Architecture

### CI Pipeline
- Dockerfile containerizes Angular app with Node.js runtime
- GitHub Actions workflow builds image on push
- Semantic version tags (e.g., `v1.0.0`) create versioned releases
- Images pushed to DockerHub with authentication via GitHub secrets

### CD Pipeline
- DockerHub webhook triggers deployment on new image push
- AWS EC2 instance runs webhook listener (adnanh/webhook)
- Bash script pulls new image and restarts container
- Systemd service ensures webhook runs on startup

## Key Features

- **Automated Builds:** Every push triggers new Docker image build
- **Version Control:** Semantic versioning enables easy rollbacks
- **Zero-Downtime Deployment:** Automated container swap on AWS
- **Secure Credentials:** DockerHub auth stored as encrypted GitHub secrets

## Tech Stack

- **Containerization:** Docker
- **CI/CD:** GitHub Actions
- **Deployment:** AWS EC2 (Ubuntu 20.04), webhook
- **Application:** Angular, Node.js
- **Registry:** DockerHub
