# RHEL Infrastructure Administration Lab

Enterprise-focused Red Hat Enterprise Linux systems administration lab
built with VMware Workstation.

The goal of this project is not simply to learn Linux commands, but to
practise how RHEL systems are deployed, administered, secured,
automated, monitored, and troubleshot in an organizational environment.

## Platform

-   Host OS: Windows 11
-   Hypervisor: VMware Workstation
-   Primary OS: Red Hat Enterprise Linux 10.2 x86_64
-   Installation media: RHEL 10.2 x86_64 DVD ISO
-   Lab network: 10.30.30.0/24

## Planned Infrastructure

  System       Role                                    IP address
  ------------ --------------------------------------- -------------
  RHEL-ADM01   Administration / Ansible control node   10.30.30.10
  RHEL-SRV01   General-purpose managed server          10.30.30.20
  RHEL-SRV02   Infrastructure/service server           10.30.30.30

Additional systems will be introduced only when required by an
administrative scenario.

## Learning Areas

-   RHEL installation and lifecycle management
-   Users, groups, permissions, and sudo
-   Package management with DNF/RPM
-   systemd and process administration
-   Logging and troubleshooting
-   Storage, filesystems, and LVM
-   NetworkManager and nmcli
-   firewalld and SELinux
-   SSH and remote administration
-   Enterprise services
-   Ansible automation
-   Podman and containers
-   Backup, recovery, patching, and operational troubleshooting

## Administrative Approach

The lab follows an operations-oriented workflow:

1.  Configure
2.  Verify
3.  Inspect
4.  Troubleshoot
5.  Document
6.  Automate where appropriate

The environment is intentionally designed to evolve into a multi-server
RHEL estate rather than a collection of independent virtual machines.

## Documentation

Detailed implementation notes are maintained in the `docs/` directory.

Current project progress is tracked in `LAB_STATUS.md`.
