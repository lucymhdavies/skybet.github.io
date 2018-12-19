---
layout:     post
title:      Terraforming HashiCorp Vault
date:       2018-12-19
summary:    Reflecting on 7 months, and 800 Pull Requests, managing Vault configuration as code
author:     lucy_davinhart
image:      terraform-vault/slack-output.png
category:   Operations
tags:       hashicorp, vault, terraform, gitops, jenkins
---


We've recently hit pull request number 800[^1] in our Vault Terraform BitBucket repo!


Outline:

* Where we were (manually making changes to Vault, difficult to audit; goldfish; config backup jenkins job)
* First version (policies only. include how the Jenkins job works; it hasn’t changed much since then; mention initial feedback loop with backup job)
* Expanding to LDAP groups (using generic secret. note that the provider now supports ldap groups natively)
* Breaking the feedback loop - we modified our own policies so we can no longer manually edit these things
* Adding AppRoles (mention CIDR range variables)
* Kubernetes Roles, the first additional resource added entirely by a different team
* Future: use LDAP groups directly; terraform more things; go apps, rather than bash scripts, for bulk imports; enterprise features that could be terraformed: sentinel policies, namespaces


----

Footnotes:

[^1]: Of those 800, 234 are automatically generated "Merge release into master" pull requests, so they don't really count, but 566 (a [nontotient happy number](https://en.wikipedia.org/wiki/500_(number)#566)) didn't make for quite as great a headline
