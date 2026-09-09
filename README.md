# pkg-eva-dkms

This repository contains the Debian packaging rules and scripts for the EVA (Engine for Visual Analytics) kernel driver on Qualcomm Snapdragon targets. The upstream source lives in [qualcomm-linux/eva-driver](https://github.com/qualcomm-linux/eva-driver).

EVA driver is responsible for:

- EVA session and firmware management
- HFI (Host-Firmware Interface) command/message queue handling
- Buffer, memory, and IOVA management for EVA workloads
- Power, clock, and NOC (Network-on-Chip) management for the EVA subsystem
- Providing the userspace ioctl interface used by the EVA UMD

The driver is delivered as a DKMS module so it is rebuilt against the running kernel on the target.

## Branches

- **qli-ci**: The primary branch containing workflow logic in the `.github/` folder, along with boilerplate documentation files such as license, contribution guidelines, and this README.
- **qcom/debian/latest**: Qualcomm's tip of Debian packaging development for eva-dkms.
- **qcom/debian/trixie**: Qualcomm's Debian Trixie packaging branch for eva-dkms.
- **qcom/ubuntu/resolute**: Qualcomm's packaging branch targeting Ubuntu 26.04 (Resolute Raccoon).


## Typical Workflows

1. **Upstream promotion**: When the upstream `eva-driver` project tags a new release, the promote workflow merges it into the packaging branch and opens a PR.
2. **PR validation**: PRs in this repo are validated against the package build to catch breakages early.
3. **Release**: A manual dispatch finalizes the changelog, builds the package, uploads artifacts, and notifies [qcom-distro-images](https://github.com/qualcomm-linux/qcom-distro-images).

The workflows of this repo use the reusable workflows from [qcom-build-utils](https://github.com/qualcomm-linux/qcom-build-utils) in the background.

## Installation

```
sudo dpkg -i eva-dkms_<version>_arm64.deb
```

## Getting in Contact

- [Report an Issue on GitHub](/qualcomm-linux/pkg-eva-dkms/issues)
- [Open a Discussion on GitHub](/qualcomm-linux/pkg-eva-dkms/discussions)
- [E-mail us](mailto:Maintainers.pkg-eva-dkms@qualcomm.com) for general questions

## License

pkg-eva-dkms is licensed under the [BSD-3-Clause License](https://spdx.org/licenses/BSD-3-Clause.html). See [LICENSE.txt](LICENSE.txt) for the full license text.
