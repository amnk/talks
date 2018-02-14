# Path to kubernetes

## 1000 mile overview

<span style="font-size:0.5em">By `github.com/amnk`</span>

<span style="font-size:0.5em">Disclaimer: everything here is a personal opinion, and is not necessary aligned with the view of my employer</span>
---
### Topics to be covered

* current issues in our deployment pipelines;
* good staff we do now and should continue doing;
* possible ways to combine good and bad and evolve;
* timeline for kubernetes adoption;
---
### Current issues in our deployment pipelines

<span style="font-size:0.7em">Not sorted in any particular order</span>

1. At least 3 different approaches to deployments.
+++
### Current issues in our deployment pipelines

<span style="font-size:0.7em">Not sorted in any particular order</span>

1. At least 3 different approaches to deployments.
2. DataDog monitoring does not cover everything.
+++
### Current issues in our deployment pipelines

<span style="font-size:0.7em">Not sorted in any particular order</span>

1. At least 3 different approaches to deployments.
2. DataDog monitoring does not cover everything.
3. Logging management is difficult because of #1.
+++
### Current issues in our deployment pipelines

<span style="font-size:0.7em">Not sorted in any particular order</span>

1. At least 3 different approaches to deployments.
2. DataDog monitoring does not cover everything.
3. Logging management is difficult because of #1.
4. A lot of different deployment pipelines.
+++
### Current issues in our deployment pipelines

<span style="font-size:0.7em">Not sorted in any particular order</span>

1. At least 3 different approaches to deployments.
2. DataDog monitoring does not cover everything.
3. Logging management is difficult because of #1.
4. A lot of different deployment pipelines.
5. Duplication of logic in provision/termination/deployment scripts
---
### Good staff we do now and should continue doing

<span style="font-size:0.7em">Not sorted in any particular order</span>

1. Infrastructure as a code
+++
### Good staff we do now and should continue doing

<span style="font-size:0.7em">Not sorted in any particular order</span>

1. Infrastructure as a code.
2. Initiative to unify of variables and secrets.
+++
### Good staff we do now and should continue doing

<span style="font-size:0.7em">Not sorted in any particular order</span>

1. Infrastructure as a code.
2. Initiative to unify variables and secrets.
3. CI/CD pipelines as a code (jobdsl).
---
### Current state of things

1. We have several good initiatives.
2. We do not have a unified platform.
---
### Possible ways to evolve

1. Unified platform
+++
### Possible ways to evolve

1. Unified platform.
2. Terraform everything and hope for the best.
---
### Terraform everything

* still does not provide unified way of doing deployments;
* Terraform as a language produces lots of Boilerplate code;
* putting entire company in dependency of one tool is a huge risk;
---
### Kubernetes 

* production-grade container orchestration platform;
* unified and **declarative** way of deployments;
* green/blue, autoscaling, logging, monitoring, recovery - out of the box;
* unified way to manage security updates;
+++
### Kubernetes 

* a complicated platform that requires additional knowledge;
* some applications are hard to containerize;
---
### Kubernetes - adoption timeline

* start with Amazon EKS (available in US only);
* acknoledge with declarative way of doing deployments;
* migrate first application;
* migrate all devops applications;
* migrate all ElasticBeanstalk applications;

