# Migration from VMware to Linux

This proposes one of the possible methods to migrate VMware to Linux KVM with EXPRESSCLUSTER.

1. Existing VMware runs VMs in it.

   ![Phase1](Phase1.png)

2. Build SDS (Software Defined Storage) which is ECX iSCSI Target Cluster.
   Export VMs from VMware to SDS by V2V utility, that's V2V from VMware to KVM.
   VMs images are replicated to DR site by ECX.

   ![Phase2](Phase2.png)

3. ztC#1 as a Linux box mounts SDS and runs VMs.
   All the WRITE operations issued on a VM are reflected in the VM image in SDS, and the changes are replicated on the DR site.
   VMs on ztC#1 failover to #2 for HA and #3 for DR.

   ![Phase3](Phase3.png)
