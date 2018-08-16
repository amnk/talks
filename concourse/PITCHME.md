# Councourse CI

## or how to manage large scale pipelines

@size[0.7em](by https://github.com/amnk)
---
### What is a pipeline?

![Simple Pipeline](concourse/assets/simple_pipeline.png)

@size[0.3em](drawing is my weak point...)
+++
### ... But it might become more complicated

![Complicated Pipeline](concourse/assets/complicated_pipeline.png)
---
### Elevator pitch

Concourse allows managing large scale pipelines as a code, avoids any implicit state and scales with your project

![Pipeline](concourse/assets/pipeline.png)
---
### Architecture and general concepts

* Everything runs in ephemeral, reproducible containers;
* Everything-as-Code;
* Everything is combined with resources, tasks and jobs;
+++
### Resources

anything one can publish to or pull from and anything that can be versioned (e.g., GitHub, AWS S3 buckets, Docker images, Slack messages/threads, etc.)

![resource](concourse/assets/background_resources.png)
+++
### Resources #2

Each resource implements **in**, **out** and **check** commands

```yaml
- name: code
  type: git
  source:
    uri: https://github.com/concourse/concourse
```
+++
### Tasks

instructions on how something should be run

```yaml
platform: linux

image: busybox

inputs:
- name: code

outputs:
- name: binaries

run:
  path: ci/build.sh
```
+++
### Jobs

these combine resources and tasks, which results in something being done.

```yaml
jobs:
- name: build
  serial: true
  plan:
  - get: code
    trigger: true
  - task: build
    file: ci/build.yml
  - task: create-context
    file: ci/tasks/create-context.yml
  - put: image
    params:
      build: context
  - put: artifacts

```
---
### Pipelines as a first class citizen

![Pipeline](concourse/assets/pipeline.png)

* not a repository;
* not a release or binary;
* not a job;
+++
### Pipelines as a code

This concept allows expressing entire business logic of CI/CD in a code

```yaml
jobs:
- name: build
  serial: true
  plan:
  - get: code
    trigger: true
  - task: build
    file: ci/build.yml
  - task: create-context
    file: ci/tasks/create-context.yml
  - put: image
    params:
      build: context
  - put: swarm
```
---
### Concourse vs Jenkins

* declarative and stateless;
* build around pipelines;
* no Groovy/JobDSL;

@size[0.8em](https://www.infoq.com/presentations/Simple-Made-Easy)

@size[0.6em](by Rich Hickey - creator of Clojure)
---
### Questions and answers
