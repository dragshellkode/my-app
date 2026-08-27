# My App — CI/CD Pipeline Project

A hands-on project built to learn the full CI/CD lifecycle: from Git basics
to an automated pipeline deploying a containerized app to both ECS and EKS.
Built as part of the Cloud & DevOps training task sheet.

## Overview

This repo tracks a single static web app (`index.html`) as it moves through
four stages of increasing pipeline maturity — version control, automated
builds, container deployment on ECS, and container deployment on EKS.

## Tasks Covered

### 1. Git Fundamentals
- Local repo init, staging, and commits
- Branching, merging via Pull Request
- Full history tracked in `git log`

### 2. AWS CodePipeline & CodeBuild
- `buildspec.yaml` defines the build phases for AWS CodeBuild
- CodeBuild project connected to this GitHub repo
- CodePipeline wired for Source → Build, auto-triggered on every push to `main`

### 3. ECS Deployment Pipeline
- `Dockerfile` containerizes the app (nginx serving `index.html`)
- Image built and pushed to Amazon ECR
- Deployed as a Fargate service on Amazon ECS
- Pipeline extended with a Deploy stage (Amazon ECS provider)

### 4. EKS CodePipeline Deployment
- `deployment.yaml` and `service.yaml` define the Kubernetes Deployment and
  LoadBalancer Service
- App deployed to an existing EKS cluster
- CodeBuild updated to build, push, and roll out the new image via `kubectl`
  on every pipeline run (rolling update, zero downtime)

## Repo Structure

| File | Purpose |
|---|---|
| `index.html` | The app itself |
| `Dockerfile` | Container image definition |
| `buildspec.yaml` | CodeBuild build/deploy instructions |
| `deployment.yaml` | Kubernetes Deployment spec (EKS) |
| `service.yaml` | Kubernetes Service spec (EKS, LoadBalancer) |

## Pipeline Flow
