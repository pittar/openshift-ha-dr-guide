# Platform Configuration as Code

> [!CAUTION]
> This are is still under construction :)

## Introduction

Kubernetes, by nature, is a declarative platform.  This means that as an administrator/operator/developer/etc, you tell Kubernetes the state that you want things to be in, then the platform will act on configuration.  A simple example of this is when you create a `Deployment` object and apply it to your cluster (for example, with `oc/kubectl apply -f deployment.yaml`).  Once this configuration is applied, the Kubernetes scheduler will not only try to satisfy the configuration (for example, deploy a particular container image with the specified number of replicas), but also make sure that this configuration is actively maintained (if the deployment specifies two replicas and one pod crashes, the Kubernetes scheduler will attempt to fix this by launching another pod to bring the replica count back up to two).

OpenShift takes the pardigm of a declarative platform even further by introducting the concept of Operators.  A deeper dive into Operators is beyond the scope of this guide, but the important takeaway is that all aspects of OpenShift are managed by Operators.  These operators, like Kubernetest itself, take configuration in the form of **YAML** files and automatically apply (and remidiate) this configuration in the cluster.

The combination of Operators on this declarative platform means that the configuration of the platform can almost entirely be defined "as code" and stored/versioned/audited in a source control management tool - specifically Git repositories.

## Configuration as Code

Configuration as Code is the most important aspect of a DR strategy.  Having the configuration of your platform stored in a git repository has many important benefits:

1. Recreating the base platform is much easier, since the configuration of the platform is stored and versioned in a git repository.
2. "Snowflake" environments are eliminated, as all configuration changes go through source control.
3. Creating new clusters that match the specifications of existing clusteres is trivially easy.
4. Moving configuration from "low" to "high" environments is easier and more consistent, as the configuration can be easily exported from the low environment and imported into a git repository on the "high" side.

