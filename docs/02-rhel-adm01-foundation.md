# RHEL-ADM01 Foundation

## Objective

Deploy the first RHEL system in the lab and establish a clean, verified
baseline suitable for subsequent administration, security, service, and
automation exercises.

`RHEL-ADM01` is the primary administration system and is intended to
become the Ansible control node as the environment expands.

## Virtual Machine Configuration

  Setting               Value
  --------------------- --------------------------------------
  VMware display name   RHEL-ADM01
  Operating system      Red Hat Enterprise Linux 10.2 x86_64
  vCPU                  2
  Memory                4 GB
  Virtual disk          60 GB NVMe
  Network               VMware VMnet8 NAT
  Installation media    RHEL 10.2 x86_64 DVD ISO

The installation ISO was verified with SHA-256 before deployment.

## Operating System Installation

RHEL 10.2 was installed with the following initial system configuration:

  Setting               Value
  --------------------- --------------
  Hostname              rhel-adm01
  Timezone              Europe/Paris
  Administrative user   admin
  Network interface     ens160
  Initial addressing    DHCP

The system initially received `10.30.30.128/24` from the VMware DHCP
pool. The planned infrastructure address is `10.30.30.10`; persistent
static addressing will be configured during the networking
administration phase.

## Network Validation

The initial network configuration was validated before continuing with
system configuration.

Verified connectivity included:

-   VMware NAT gateway at `10.30.30.2`
-   External IP connectivity
-   Repository and Red Hat service access
-   SSH access to `RHEL-ADM01`

This established that the guest network, VMware NAT configuration, and
outbound connectivity were functioning correctly.

## VMware Guest Integration

VMware guest integration is provided by `open-vm-tools`.

Package installation was verified with:

``` bash
rpm -q open-vm-tools
```

Installed package:

``` text
open-vm-tools-13.0.10-1.el10.x86_64
```

The VMware Tools service was verified with:

``` bash
systemctl status vmtoolsd --no-pager
```

The `vmtoolsd` service was confirmed as enabled and active.

## Red Hat Registration

`RHEL-ADM01` was registered with Red Hat Subscription Management.

Registration state was verified with:

``` bash
sudo subscription-manager status
sudo subscription-manager identity
```

The system reported an overall status of `Registered`.

System-specific registration identifiers are intentionally not stored in
the repository.

## Software Repositories

Enabled Red Hat repositories were inspected with:

``` bash
sudo subscription-manager repos --list-enabled
```

The required RHEL 10 repositories were confirmed:

``` text
rhel-10-for-x86_64-baseos-rpms
rhel-10-for-x86_64-appstream-rpms
```

DNF repository visibility was independently verified with:

``` bash
sudo dnf repolist
```

Both BaseOS and AppStream were available to the package manager.

## System Update

Available updates were inspected before installation:

``` bash
sudo dnf check-update
```

The system was then updated with:

``` bash
sudo dnf upgrade
```

The update included normal userspace package updates and a newer RHEL
kernel. Package-signing keys presented by DNF were verified and accepted
as part of the trusted Red Hat package-management configuration.

The transaction completed successfully.

## Kernel Validation

Before rebooting, the running kernel and installed kernel packages were
compared:

``` bash
uname -r
rpm -q kernel
```

The system was still running:

``` text
6.12.0-211.7.3.el10_2.x86_64
```

while the newer kernel had been installed alongside it:

``` text
6.12.0-211.61.1.el10_2.x86_64
```

This demonstrated the normal Linux update model in which the running
kernel remains active until the next boot and the previous kernel is
retained as a fallback.

After a controlled reboot, the active kernel was verified again:

``` bash
uname -r
```

Result:

``` text
6.12.0-211.61.1.el10_2.x86_64
```

The updated kernel therefore booted successfully.

## Post-Update Health Check

Systemd was checked for failed units after the update and reboot:

``` bash
systemctl --failed
```

Result:

``` text
0 loaded units listed.
```

This confirmed that no systemd units were in a failed state at the
baseline checkpoint.

## Baseline Snapshot

After validation, the VM was shut down cleanly and a VMware snapshot was
created.

Snapshot name:

``` text
01-rhel-foundation-registered-updated
```

The snapshot represents a known-good RHEL 10.2 baseline with:

-   working VMware NAT networking
-   SSH access
-   VMware guest integration
-   Red Hat registration
-   BaseOS and AppStream repositories
-   current system updates
-   updated kernel successfully booted
-   zero failed systemd units

This snapshot provides a recovery point before beginning deeper
administrative configuration.

## Foundation Workflow

The work completed on `RHEL-ADM01` establishes the manual baseline
workflow for future RHEL systems:

1.  Provision the virtual machine.
2.  Install and identify the operating system.
3.  Establish and verify networking.
4.  Verify virtualization-platform integration.
5.  Register the system and validate software repositories.
6.  Inspect and apply system updates.
7.  Reboot when required and verify the active kernel.
8.  Perform post-change health checks.
9.  Establish a known-good baseline.

Additional standards such as persistent addressing, users and groups,
sudo policy, SSH configuration, firewall policy, SELinux configuration,
logging, monitoring, and storage will be incorporated as those areas are
implemented in the lab.

The workflow is intentionally performed manually first so that each
administrative task is understood and verified before repetitive
configuration is standardized and automated.

## Next Phase

With the initial platform baseline complete, the lab proceeds to core
RHEL administration, including:

-   users, groups, permissions, and sudo
-   DNF and RPM package administration
-   systemd and process management
-   logging and troubleshooting
-   persistent networking with NetworkManager and `nmcli`
-   storage and LVM
-   firewalld and SELinux
-   SSH administration

Additional RHEL systems will be deployed when multi-host administration
and automation scenarios require them.
