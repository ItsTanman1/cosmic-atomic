# cosmic-atomic &nbsp; [![bluebuild build badge](https://github.com/itstanman1/cosmic-atomic/actions/workflows/build.yml/badge.svg)](https://github.com/itstanman1/cosmic-atomic/actions/workflows/build.yml)

## Installation

> [!WARNING]  
> This is a personal image. Do not use!

To rebase an existing atomic Fedora installation to the latest build:

- First rebase to the unsigned image, to get the proper signing keys and policies installed:
  ```
  rpm-ostree rebase ostree-unverified-registry:ghcr.io/itstanman1/cosmic-atomic:latest
  ```
- Reboot to complete the rebase:
  ```
  systemctl reboot
  ```
- Then rebase to the signed image, like so:
  ```
  rpm-ostree rebase ostree-image-signed:docker://ghcr.io/itstanman1/cosmic-atomic:latest
  ```
- Reboot again to complete the installation
  ```
  systemctl reboot
  ```

## Verification

These images are signed with [Sigstore](https://www.sigstore.dev/)'s [cosign](https://github.com/sigstore/cosign). You can verify the signature by downloading the `cosign.pub` file from this repo and running the following command:

```bash
cosign verify --key cosign.pub ghcr.io/itstanman1/cosmic-atomic
```
