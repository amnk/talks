# Kubernetes applicability

## 10000 ft overview
---
### Current issues in our deployment strategies

<span style="font-size:0.7em">Not sorted in any particular order</span>

1. At least 3 different approaches to deployments.
2. Monitoring (via Datadog) does not cover everything.
3. Logging management is difficult because of #1.
4. Duplication of logic in provision/termination/deployment scripts.
5. Leaky abstraction: our applications need to have knowledge about entire AWS configuration;
---
### Good things we do now and should continue doing

<span style="font-size:0.7em">Not sorted in any particular order</span>

1. Infrastructure as a code.
2. Initiative to unify variables and secrets.
3. CI/CD pipelines as a code (jobdsl).
---
### Current state of things

1. We have several good initiatives.
2. We have ad-hoc, informally-specified, bug-ridden and half-implemented platform (cf. Greenspuns tenth rule).
---
### Possible ways to evolve

1. Unified platform.
2. Terraform everything and hope for the best.
3. Maybe (Spinnaker|Rancher)+Packer, Nomad, highly customized ECS, ~~shell scripts~~...
+++
### Terraform everything

* deployments are still ad-hoc (local-exec, provisioners);
* Terraform is concerned about resources rather then deployments (provisioners are separate);
* Terraform is not really suitable for dynamic deployments (blue/green, canary);
* Terraform as a language produces lots of Boilerplate code;
---
### Spinnaker

* can provision AWS;
* can provision kubernetes clusters and pods;
* might be our missing PaaS;
+++
### Spinnaker

* complicated by itself;
* developed by Google (where is my NewsReader and Google Code?);
* ecosystem is smaller;
* more complicated than Rancher, without much visible benefit (additional research needed);
---
### Containers as packaging and init system

* instead of systemd/supervisord/upstart;
* instead of system-wide updates, outdated packages and Artifactory/S3;
* instead of Packer and custom logic to build, search and rotate images;
* more collaboration with developers (Dockerfile is easier than ansible playbooks and is scoped);
* reproducibility (!);
---
### Kubernetes as an orchestration system

* one orchestrator instead of Jenkins/init systems/ASGs/cloudwatch;
* unified and **declarative** way of doing deployments;
* unittests for deployments (!);
* green/blue, autoscaling, logging, monitoring, recovery - out of the box;
* unified way to manage security updates;
* proper abstraction: applications do not need to know about AWS config;
+++
### Kubernetes 

* a complex platform that requires additional knowledge;
* some applications need time to containerize;
---
### Kubernetes - adoption timeline

* start with Amazon EKS (managed Kubernetes);
* get familiar with declarative way of doing deployments;
* migrate first application — hypernova for USA (as part of existing M1E2-2592)
* migrate all devops applications (7 total);
* adopt kubeadm to provision k8s clusters in other regions;
* migrate all ElasticBeanstalk applications;
