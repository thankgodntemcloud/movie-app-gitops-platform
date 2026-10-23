
# Movie App GitOps Platform

## 1. Project Overview

This project rebuilds the deployment platform for an existing movie application using Docker, GitHub Actions, Terraform, Kubernetes, and Argo CD.

The objective is to automate application image builds, provision AWS infrastructure as code, and deploy the frontend and backend using GitOps.

This is a hands-on cloud and DevOps learning project. Implementation and validation will be documented as the work progresses.

## 2. Project Objectives

- Reuse the existing movie application source code.
- Build and publish frontend and backend Docker images to Docker Hub.
- Automate image building and validation using GitHub Actions.
- Provision AWS infrastructure using Terraform.
- Deploy the application to Kubernetes.
- Implement GitOps continuous delivery with Argo CD.
- Securely configure database connectivity and application secrets.
- Document deployment, troubleshooting, security, and cleanup procedures.

## 3. Existing Application Repositories

The application source code remains in separate repositories:

- Frontend: https://github.com/thankgodntemcloud/netflix_frontend
- Backend: https://github.com/thankgodntemcloud/netflix_backend

This repository is dedicated to the new deployment platform. It will contain Terraform configuration, CI workflows, Kubernetes manifests, Argo CD configuration, and technical documentation.

The original application repositories will remain unchanged unless a specific modification is necessary.

## 4. Planned Architecture

The planned workflow is:

1. **Source code:** Existing frontend and backend GitHub repositories.
2. **Continuous integration:** GitHub Actions builds and validates application images.
3. **Container registry:** Docker Hub stores versioned container images.
4. **Infrastructure:** Terraform provisions the required AWS resources.
5. **Container orchestration:** Kubernetes runs the frontend and backend.
6. **GitOps delivery:** Argo CD monitors deployment configuration in GitHub and reconciles the target cluster.
7. **Database:** MongoDB Atlas will be reused if the existing database is still available and suitable.

The Kubernetes topology, EC2 instance sizes, network configuration, ingress, and TLS approach will be finalized before infrastructure is provisioned.

## 5. Repository Structure

```text
movie-app-gitops-platform/
├── .github/
│   └── workflows/
├── argocd/
├── kubernetes/
│   ├── base/
│   └── overlays/
│       └── dev/
├── terraform/
│   ├── environments/
│   │   └── dev/
│   └── modules/
├── docs/
└── README.md
```

## 6. Implementation Roadmap

### Phase 1 — Application Preparation

- [ ] Inspect frontend and backend source code and Dockerfiles.
- [ ] Review application configuration and database connectivity.
- [ ] Review the existing GitHub Actions workflows.
- [ ] Create Docker Hub repositories and configure required secrets.

### Phase 2 — Continuous Integration

- [ ] Build and validate the frontend image.
- [ ] Build and validate the backend image.
- [ ] Test the images locally where practical.
- [ ] Publish versioned images to Docker Hub using GitHub Actions.

### Phase 3 — Infrastructure as Code

- [ ] Configure the AWS provider, region, and networking.
- [ ] Define the required compute resources using Terraform.
- [ ] Configure Terraform state management.
- [ ] Run Terraform formatting and validation.
- [ ] Review the execution plan before applying changes.
- [ ] Verify network connectivity and security settings.

### Phase 4 — Kubernetes Deployment

- [ ] Establish the Kubernetes environment.
- [ ] Create frontend and backend Deployments and Services.
- [ ] Configure image references and environment variables.
- [ ] Configure secure database connectivity.
- [ ] Verify application communication and access.

### Phase 5 — GitOps with Argo CD

- [ ] Install and configure Argo CD.
- [ ] Connect Argo CD to this GitHub repository.
- [ ] Define the application deployment configuration.
- [ ] Configure synchronization with the development cluster.
- [ ] Test deployment reconciliation after a Git change.
- [ ] Document the process for releasing updated application images.

### Phase 6 — Testing and Documentation

- [ ] Verify frontend and backend operation.
- [ ] Test database connectivity.
- [ ] Document troubleshooting procedures.
- [ ] Record security controls and estimated AWS costs.
- [ ] Document how to clean up lab resources safely.

## 7. Security Practices

- Never commit AWS credentials, database passwords, registry credentials, or private keys.
- Store CI credentials in GitHub Actions secrets.
- Provide runtime secrets through an appropriate secret-management mechanism.
- Do not embed sensitive configuration in Docker images.
- Exclude `.env` files and Terraform state files from Git.
- Review Terraform plans before applying infrastructure changes.
- Restrict network access to the ports and sources required by the application.
- Remove unused AWS resources to prevent unnecessary charges.

## 8. Current Project Status

The GitHub repository has been created, cloned locally, and organized with the initial directory structure.

The Docker Hub images, GitHub Actions workflows, Terraform infrastructure, Kubernetes deployment, and Argo CD integration remain to be implemented and tested.

This document will be updated as each milestone is completed.
