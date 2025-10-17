# Red Hat OpenShift: High Availability and Disaster Recovery Considerations

> [!NOTE]
> This guide is not official and certainly not a complete HA/DR reference.
> This guide is meant to provide a basic understanding of HA/DR considerations, tools and processes with "out of the box" OpenShift capabilities.
> In many cases, ISV partners have complementary solutions for specific HA/DR capabilties that exceed the included capabilities provided by OpenShift.  Please consider all options when building out your own HA/DR strategy.

## Introduction

Red Hat OpenShift is an extremely capable and robust platform that makes the concept of a true "Open Hybrid Cloud" a reality.  Yes, that statement does sound like marketing material, but once you dive into the capabilities that OpenShift provides, you will quickly come to the conclusion that this is indeed true.

With this power comes a great deal of responsibility!  For a platform to be widely trusted and adopted, the end users of the platform (development teams, product teams, DevSecOps teams, etc...) have to know that the platform is rock solid.  This requires simple and transparent upgrades, fault tolerance, and tested/repeatable disaster recovery procedures.

Automation, "everything as code", and backup/restore procedures are all too often relegated to the "we'll get to it when we get to it" pile of work, which introduces a great deal of risk, configuration drift, technical debt, and added complexity.  The purpose of this guide is to highlight the fundamental best practices requried to effectively operate such a platform and instill trust in the users/customers/clientes of the platform.

## High Availability and Disaster Recover Concerns

1. Stable Underlying Compute/Network/Storage
2. Consistent OpenShift Installation Process
3. Platform Configuration as Code
4. Application Deployment / Configuration as Code
5. Etcd Backup for control plane recovery
6. OpenShift API for Data Protection (OADP) for Backup/Restore
7. Additional Considerations