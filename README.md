# PI Cluster - Kubernetes Homelab

## Overview

A production-grade Kubernetes homelab built on Raspberry Pi clusters, featuring automated deployment pipelines, monitoring, and infrastructure-as-code practices using Flux CD.

## Features

- **Kubernetes on ARM**: Running on Raspberry Pi hardware with k3s lightweight Kubernetes distribution
- **GitOps-based Deployment**: Flux CD for automated deployments and reconciliation
- **Infrastructure as Code**: YAML-based infrastructure definitions with automated dependency management
- **Multi-cluster Setup**: Staging and production cluster configurations
- **Automated Updates**: Renovate bot integration for continuous image updates
- **Monitoring & Observability**: Comprehensive monitoring stack setup
- **Container Orchestration**: Docker-based containerized workloads

## Project Structure

```
.
├── mise.toml
├── renovate.json
├── README.md
├── apps/
│   ├── base/
│   │   ├── homarr/
│   │   │   ├── deployment.yaml
│   │   │   ├── kustomization.yaml
│   │   │   └── service.yaml
│   │   └── linkding/
│   │       ├── deployment.yaml
│   │       └── kustomization.yaml
│   └── staging/
│       ├── homarr/
│       └── linkding/
├── clusters/
│   └── staging/
│       ├── apps.yaml
│   │       ├── infrastructure.yaml
│   │       └── flux-system/
├── infrastructure/
│   ├── cloudflare-tunnel/
│   └── controllers/
├── monitoring/
│   ├── configs/
│   └── controllers/
└── scripts/
  ├── setup
  └── setup_project
``` 

## Prerequisites

- Raspberry Pi cluster (ARM64 compatible)
- k3s Kubernetes distribution
- Git for version control
- Flux CLI for GitOps operations
- Docker for container management

## Quick Start

### 1. Bootstrap Cluster

Initialize your k3s cluster on Raspberry Pi nodes.

### 2. Install Flux CD

```bash
flux bootstrap github \
  --owner=aadil96 \
  --repository=pi-cluster \
  --branch=main
```

### 3. Deploy Applications

Flux will automatically reconcile and deploy applications defined in the `apps/` directory.

## Directory Details

### `/apps`
Application-level deployments and manifests. Each application includes:
- Service definitions
- Deployment configurations
- ConfigMaps and Secrets
- Ingress rules

### `/clusters/staging`
Staging cluster specific configurations:
- Cluster networking setup
- Node configurations
- Resource quotas and limits

### `/infrastructure`
Core infrastructure components:
- Storage provisioning (PVC/PV)
- Network policies
- RBAC configurations
- Service mesh (if configured)

### `/monitoring`
Monitoring stack setup:
- Prometheus configuration
- Grafana dashboards
- Alerting rules
- Log aggregation

### `/scripts`
Automation and utility scripts:
- Cluster initialization scripts
- Deployment helpers
- Backup and restore utilities

## Configuration

### Renovate
Automated dependency updates are managed through `renovate.json`. The bot automatically:
- Detects new image versions
- Creates pull requests for updates
- Follows semantic versioning

### Development Environment
Use the `.devcontainer` setup for consistent development environments:
- Pre-configured tools and dependencies
- VSCode dev container support

## Key Technologies

- **Kubernetes**: k3s (lightweight Kubernetes for ARM)
- **GitOps**: Flux CD for declarative deployments
- **Container Runtime**: Docker
- **Automation**: Shell scripts and YAML configurations
- **Infrastructure Management**: Mise for tool versioning

## Recent Updates

- Renovate integration for automated image updates
- Homarr application dashboard setup
- Cloudflare integration

## Authors

- **aadil96** - Project maintainer
- **Renovate Bot** - Automated dependency management


## Roadmap

- [ ] Multi-cluster networking improvements
- [ ] Enhanced security policies
- [ ] Advanced backup and disaster recovery
- [ ] Performance optimization
- [ ] Additional monitoring and alerting features

---

**Built with passion for Kubernetes learning and home infrastructure automation.**
