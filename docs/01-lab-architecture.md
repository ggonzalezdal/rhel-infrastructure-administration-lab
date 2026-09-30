# Lab Architecture

## Objective

Build a small enterprise-style RHEL environment for practising deployment, administration, security, automation, and troubleshooting.

## Host Platform

The lab runs on a Windows 11 workstation using VMware Workstation.

## Initial Topology

```text
                    Windows 11 Host
                  VMware Workstation
                         |
                  RHEL Lab Network
                  10.30.30.0/24
                     (planned)
                         |
          +--------------+--------------+
          |              |              |
     RHEL-ADM01      RHEL-SRV01     RHEL-SRV02
     10.30.30.10     10.30.30.20    10.30.30.30
```

## Systems

### RHEL-ADM01

Primary administration system.

Planned responsibilities:

- SSH administration
- Administrative tooling
- Git
- Ansible control node
- Troubleshooting and management tasks

Initial proposed resources:

- 2 vCPU
- 4 GB RAM
- 60 GB virtual disk
- UEFI firmware
- RHEL 10.2 x86_64

### RHEL-SRV01

General-purpose managed server.

Planned uses include:

- systemd services
- storage and LVM
- web services
- SELinux
- firewalld
- logging
- scheduled tasks
- Podman
- Ansible management

### RHEL-SRV02

Infrastructure and service server.

Planned uses include:

- NFS
- additional storage
- multi-host administration
- backup and recovery exercises
- patch management
- service-to-service networking

## Naming Convention

VM display names:

- RHEL-ADM01
- RHEL-SRV01
- RHEL-SRV02

Linux hostnames:

- rhel-adm01.lab.internal
- rhel-srv01.lab.internal
- rhel-srv02.lab.internal

## Addressing Plan

Planned network:

`10.30.30.0/24`

Initial static addresses:

- RHEL-ADM01 — `10.30.30.10`
- RHEL-SRV01 — `10.30.30.20`
- RHEL-SRV02 — `10.30.30.30`

The final VMware network, gateway, DNS, DHCP policy, and NAT configuration will be documented after the VMware virtual network design is completed.

## Design Principle

New virtual machines and services are introduced only when there is an administrative reason for them.

The lab prioritizes operating systems as infrastructure: configuration must be verified, failures investigated, changes documented, and repetitive administration automated where appropriate.
