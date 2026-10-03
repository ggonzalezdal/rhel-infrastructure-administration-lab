# Changelog

## 2026-10-03

### Added

-   Configured VMware VMnet8 as the `10.30.30.0/24` NAT lab network.
-   Created and installed `RHEL-ADM01` with RHEL 10.2 x86_64.
-   Configured the `rhel-adm01` hostname and Europe/Paris timezone.
-   Created the `admin` administrative account.
-   Enabled and verified SSH remote access.
-   Verified VMware guest integration with `open-vm-tools` and
    `vmtoolsd`.
-   Registered `RHEL-ADM01` with Red Hat Subscription Management.
-   Enabled and verified the RHEL 10 BaseOS and AppStream repositories.
-   Created the VMware snapshot `01-rhel-foundation-registered-updated`.

### Changed

-   Updated all installed RHEL packages using DNF.
-   Updated the system kernel to `6.12.0-211.61.1.el10_2.x86_64`.
-   Advanced the lab from the foundation phase to core RHEL
    administration.

### Verified

-   Verified connectivity to the VMware NAT gateway and the Internet.
-   Verified repository availability through DNF.
-   Verified successful boot using the updated kernel.
-   Verified zero failed systemd units after the update and reboot.

## 2026-09-30

### Added

-   Created the RHEL Infrastructure Administration Lab.
-   Selected RHEL 10.2 x86_64 as the initial operating system.
-   Established initial VM naming and addressing conventions.
-   Created the initial documentation structure.
-   Added lab status tracking.
