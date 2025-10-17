# Stable Underlying Compute/Network/Storage

Just like building a house, you need to build your platorm on a stable foundation.  In this case, that foundation is stable underlying hardware and/or virtualization platform.

This aspect is outside the scope of this guide, but some examples of underlying foundation issues that could disrupt the stability of OpenShift includes (but is not limited to):

**Hardware**

* Unscheduled power outtages.  If your physical data centre is prone to unscheduled power outtages on a regular basis, this will have a negative effect on OpenShift stability and recoverability.
* Unscheduled network outtages.  If the network in your data centre is interruped regularly (including unsecheduled / manual firewall changes that could impact the platform), this will have a negative effect on OpenShift Stability.
* Slow response times to replace failing hardware and storage.  If it takes days or weeks to replace failing hardware in the data centre (if there is not any spare capacity to use in the meantime), this can negatively affect the performance and available capacity of OpenShift.

**Virtualization**

If you are deploying OpenShift on a hypervisor such as VMware, Nutanix or OpenStack:

* Unscheduled or uncoordinated upgrades of the underlying hypervisor.  Standard hypervisor upgrades should not affect OpenShift stability, but should be coordinated between the virtualization team and OpenShift team to understand the potential impact of an upgrade.
* "VMotion" of OpenShift nodes and storage.  VMotion of compute is supported, VMotion of storage is generally not.  It's always a good idea to understand the impact the hypervisor has on OpenShift in terms of compute, network and storage.
* "Traditional Backups".  It's common for teams that are familiar with traditional vm workloads to consider simply backing up the VM nodes (e.g snapshots) as a form of "DR" for OpenShift.  This is **NOT** an effective or supported way to manage DR for OpenShift!  The following sections of this guide will set you up for success when it comes to DR.

As you can see, having a solid foundation is a prerequisite to providing a solid platform.  In some situations, this might be impossible (for example, deployed in the field, in a small edge data centre with flaky network access, or in a homelab where you push the "power" button on your machine to turn your cluster off over the weekend).  If you anticipate this is situation that you are in, that's fine!  This just means that you will need to document a few extra procedures to quickly debug and fix issues that might arise from these process.

More on that when time permits...

[Next: Consistent OpenShift Installation Process](consistent-install.md)