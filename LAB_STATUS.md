# Lab Status

## Current Phase

Phase 1 --- Core RHEL Administration

The initial RHEL platform foundation is complete. The lab is ready to
move into day-to-day enterprise administration tasks before expanding to
additional managed systems and automation.

## Completed

### Project Foundation

-   Created the RHEL Infrastructure Administration Lab project.
-   Selected VMware Workstation as the hypervisor.
-   Selected RHEL 10.2 x86_64 as the primary platform.
-   Downloaded the official RHEL 10.2 x86_64 DVD ISO.
-   Verified the installation ISO using SHA-256.
-   Defined the initial VM roles and naming convention.
-   Defined the 10.30.30.0/24 lab addressing scheme.
-   Created the GitHub repository structure.

### Virtualization and Networking

-   Configured VMware VMnet8 as the lab NAT network.
-   Configured the host-side VMnet8 interface as 10.30.30.1/24.
-   Verified the NAT gateway at 10.30.30.2.
-   Verified guest connectivity to the lab gateway and the Internet.

### RHEL-ADM01

-   Created and installed RHEL-ADM01 with RHEL 10.2 x86_64.
-   Configured hostname `rhel-adm01`.
-   Configured the Europe/Paris timezone.
-   Created the administrative user `admin`.
-   Verified SSH connectivity.
-   Verified `open-vm-tools` installation and the `vmtoolsd` service.
-   Registered the system with Red Hat Subscription Management.
-   Verified the RHEL 10 BaseOS and AppStream repositories.
-   Updated the system using DNF.
-   Installed and booted kernel `6.12.0-211.61.1.el10_2.x86_64`.
-   Verified zero failed systemd units after the update and reboot.
-   Created the VMware snapshot `01-rhel-foundation-registered-updated`.

## Current Infrastructure

  ------------------------------------------------------------------------
  System                  Role                     Current network state
  ----------------------- ------------------------ -----------------------
  RHEL-ADM01              Administration / future  VMnet8 NAT, DHCP
                          Ansible control node     (`10.30.30.128/24`)

  RHEL-SRV01              General-purpose managed  Not yet deployed
                          server                   

  RHEL-SRV02              Infrastructure/service   Not yet deployed
                          server                   
  ------------------------------------------------------------------------

The planned static address for RHEL-ADM01 is `10.30.30.10`. Static
addressing will be configured as part of the networking administration
work rather than treated as already complete.

## Next Steps

1.  Begin core RHEL administration.
2.  Practise users, groups, permissions, and sudo administration.
3.  Develop package-management skills with DNF and RPM.
4.  Administer services and processes with systemd.
5.  Inspect and troubleshoot system logs.
6.  Configure persistent networking with NetworkManager and `nmcli`.
7.  Introduce storage and LVM administration.
8.  Configure and validate firewalld and SELinux.
9.  Harden and practise SSH-based remote administration.
10. Deploy additional RHEL systems when required for multi-server
    administration and Ansible automation.
