# Consistent OpenShift Installation Process

> [!CAUTION]
> This are is still under construction :)

## Introduction

Although this might be stating the obvious, it's extremely important to have a consistent and repeatable way to deploy the bare foundation of your OpenShift cluster.

There are many ways to [deploy OpenShift on many different platforms and in many different environments](https://docs.redhat.com/en/documentation/openshift_container_platform/4.19#Install), this includes (but is not limited to):
* [Red Hat OpenShift Service on AWS (ROSA)]() - A managed OpenShift Service on AWS
* [Azure Red Hat OpenShift]() - A managed OpenShift service on Azure
* Self-Managed OpenShift on [AWS](https://docs.redhat.com/en/documentation/openshift_container_platform/4.19/html/installing_on_aws), [Azure](https://docs.redhat.com/en/documentation/openshift_container_platform/4.19/html/installing_on_azure), [Google](https://docs.redhat.com/en/documentation/openshift_container_platform/4.19/html/installing_on_gcp), [Oracle Cloud](https://docs.redhat.com/en/documentation/openshift_container_platform/4.19/html/installing_on_oci) and [IBM Cloud](https://docs.redhat.com/en/documentation/openshift_container_platform/4.19/html/installing_on_ibm_cloud), among others.
* [OpenShift on Bare Metal](https://docs.redhat.com/en/documentation/openshift_container_platform/4.19/html/installing_on_bare_metal) - A great way to get the most out of OpenShift!
* [OpenShift on VMware](https://docs.redhat.com/en/documentation/openshift_container_platform/4.19/html/installing_on_vmware_vsphere) - Less popular these days...
* [OpenShift on Nutanix](https://docs.redhat.com/en/documentation/openshift_container_platform/4.19/html/installing_on_nutanix) - Another Hyperconverged Infrastructure Option
* [OpenShift on OpenStack](https://docs.redhat.com/en/documentation/openshift_container_platform/4.19/html/installing_on_openstack) - A good option for large Private Cloud deployments
* [OpenShift on OpenShift](https://docs.redhat.com/en/documentation/openshift_container_platform/4.19/html/hosted_control_planes) - Deploy virtual clusters on top of bare metal OpenShift!

All of the above options can be automated through the use of your automation tool of choice.  [Ansible Automation Platform](https://docs.redhat.com/en/documentation/red_hat_ansible_automation_platform/2.6) is of course a great option, but any automation tool or pipeline that can call a CLI should do the trick.

Be sure to automate as much of the installation process as possible in order to quickly build new clusters (or rebuild a failing cluster) with a high degree of consistency.

## Automation Of All Things

The most popular OpenShift installation options, IPI and Agent, are both highly automated and do a great job of consistently deploying a base OpenShift cluster.  However, there are many aspects "outside" of OpenShift that need to be configured as well.  It's not surprise that these aspects should also be automated (ahem... Ansible) when possible.  They include:
* DNS - Both the `*.apps` and `api` cluster domains require **A Record** DNS entries.
* Load Balancer - Unless you are deploying "Single Node OpenShift", you will need to configure VIPs for the "apps" and "api" domains, and configure your load balancer accordingly.
* Firewall - you may need to create or update firewall rules to allow traffic in/out of the cluster.
* Certificates - you may wish to generate trusted certificates for both the "apps" wildcard domain and the "api" cluster domain.

Additional configuration outside of OpenShift might be required (for example, access to a corporate secrets management tool such as Vault, Azure Key Vault, AWS Secrets Manager, etc...).

## Recommendation

As part of your DR plan, you should have as much foundational automation in place as possible.


[Next: Platform Configuration as Code](platform-as-code.md)