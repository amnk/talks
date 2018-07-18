# Gerrit/Zuul alternatives for mortals

Comparison of code review tools & helper bot for bitbucket

<span style="font-size:0.5em">By `github.com/amnk`</span>

<span style="font-size:0.5em">Disclaimer: everything here is a personal opinion, and is not necessary aligned with the view of my employer</span>
---
### Topics to be covered

* why code review systems exist;
* current most popular approaches to code review;
* ... and why they are less then ideal;
* better <span style="font-size:0.4em">citation needed</span> way to do code review using Gerrit;
* gating system for Gerrit: Zuul;
* ... and why Gerrit/Zuul are better than currently existing solution;
* ... and why a lot of people keep away from Gerrit;
---
### why code review systems exist

<span style="font-size:0.7em">Not sorted in any particular order</span>

* detect logical errors;
* improve collective code ownership;
* ensure compatibility with other parts of the system;
* gather best practises and improve your coding;
---
### current most popular approaches to code review

Github, Phabricator, Bitbucket, Gerrit

<span style="font-size:0.7em">... and why they are less then ideal</span>
---
### Github

<span style="font-size:0.7em">Which currently seems to be the most popular place to maintain your open source project</span>

1. Code everything you need and create PR
2. Ask for reviews
3. Receive feedback -> Fix -> Commit
4. Do 3 till all reviewers approved
5. Merge
+++
### Github review - sides of the force

* <span style="font-size:0.5em; color:green">[good]</span> allows viewing changes since your last review;
* <span style="font-size:0.5em; color:green">[good]</span> user-friendly interface;
* <span style="font-size:0.5em; color:green">[good]</span> a lot of separate projects that integrate with Github and enhance the experience;
* <span style="font-size:0.5em; color:red">[bad]</span> hard dependency on Github;
* <span style="font-size:0.5em; color:red">[bad]</span> approve is a boolean - no states in-between;
* <span style="font-size:0.5em; color:red">[bad]</span> no review-queue;
* <span style="font-size:0.5em; color:red">[bad]</span> CI/CD is hard even with 3rd party systems (and expensive);

https://ghc.haskell.org/trac/ghc/wiki/WhyNotGitHub 
+++
### 3rd party projects for Github

* from Kubernetes community:
  * https://github.com/kubernetes/test-infra

* Golang community:
  * https://github.com/golang/go/wiki/GerritBot

* Rust community:
  * https://github.com/graydon/bors

* https://reviewable.io/

* TravisCI and others;
---
### Phabricator

* <span style="font-size:0.6em; color:green">[good]</span> selfhosted;
* <span style="font-size:0.6em; color:green">[good]</span> set of tools covers all needs of the project;
* <span style="font-size:0.6em; color:red">[bad]</span> need to install PHP locally;
* <span style="font-size:0.6em; color:red">[bad]</span> consists of several command line tools with opinionated behaviors;

https://ghc.haskell.org/trac/ghc/wiki/WhyNotPhabricator
---
### Bitbucket - the dark side of the force

* <span style="font-size:0.5em; color:green">[good]</span> integrates with Jira;
* <span style="font-size:0.5em; color:green">[good]</span> user-friendly interface;
* <span style="font-size:0.5em; color:green">[good]</span> has build-in pipelines;
* <span style="font-size:0.6em; color:red">[bad]</span> author can change PR after it is approved;
* <span style="font-size:0.6em; color:red">[bad]</span> no way to check changes since your review;
* <span style="font-size:0.6em; color:red">[bad]</span> no way to revert declined pull-request action;
* <span style="font-size:0.6em; color:red">[bad]</span> approve is a boolean - no states in-between;
+++
### Bitbucket - integration bot

from us (@amnk, @kgadek):

https://github.com/blancmanges/gatekeeper

* <span style="font-size:0.6em; color:red">[bad]</span> <strike>author can change PR after it is approved</strike>;
* <span style="font-size:0.6em; color:red">[bad]</span> <strike>no way to check changes since your review</strike>;
* <span style="font-size:0.6em; color:red">[bad]</span> <strike>no way to revert declined pull-request action</strike>;
* <span style="font-size:0.6em; color:red">[bad]</span> <strike>approve is a boolean - no states in-between</strike>;
---
### Gerrit

* developed by Google;
* self hosted;
* highly configurable;
* ... and with very opinionated UI;
+++
### Gerrit

Used in many projects:

* OpenStack - https://www.openstack.org/
* Android – https://android-review.googlesource.com/
* LibreOffice – https://gerrit.libreoffice.org/
* Wikimedia – https://gerrit.wikimedia.org/
* Golang – https://go-review.googlesource.com/
* Tuleap – https://gerrit.tuleap.net/
* Star Wars Galaxies Emulator – http://review.swgemu.com/
+++
### Gerrit, details

* each commit is a separate PR;
  <span style="font-size:0.6em">https://www.kernel.org/doc/html/v4.12/process/submitting-patches.html</span>
* Gerrit keeps track of files you reviewed;
* offline reviews (!), because Gerrit exposes API for all actions;
* console based review;
* review queues;
* highly configurable;
+++
### Gerrit, highly configurable review system

* create different review scores and different rules for merging based on those scores;
* create review groups with different permissions;
* integrate custom pipelines for commit flow;
* custom per-user dashboards to follow developmnets in projects you are interested in;
+++
### Gerrit, the pitfalls

* arguably worth UI experience that others;
* might be hard for newcomers from Github;
* requires infrastructure and some one to support it;
---
### Why gating system?

* ensure code quality;
* protect developers (developers always start from working code);
* protect tree (bad code does not land);

<span style="color:green">Essentially, gating system is a glue between code review and CI</span>
+++
### Zuul as a gating system

<span style="font-size:0.8em">Do not mix up Zuul from Netflix and Zuul from OpenStack</span>

* https://github.com/openstack-ci/zuul
* developed by OpenStack community to handle huge project code base;
* flexible configuration;
* parallet testing of serializable changes;
---
### Summary

* we do have community platforms in place, but they require changes;
* there are better tools, which embrace better code review;
* we (as a community) need better code review;
---
### Questions?
