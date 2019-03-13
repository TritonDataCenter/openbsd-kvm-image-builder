# openbsd-kvm-image-builder

**WARNING**: This is a work in progress and is more than likely not fully functional.

This repo creates a custom OpenBSD install ISO and a KVM image for use in SmartOS and Triton.

## Requirements

This must be run on a OpenBSD machine or VirtualMachine.

## Setup

The following packages are required:

```
pkg_add bash cdrtools git rsync
```

## Usage

To build a custom ISO, run the `create-iso` script:


```
./create-iso -r <RELEASE> -m <MIRROR> -p <MIRROR_PATH> -i <ISO> -c <ISO_CHECKSUM> -d <ISO_DIR> -M <MOUNT_POINT> -l <ISO_LAYOUT> -f <ISO_FILENAME>
```

see `./create-iso -h` for usage

This will download an ISO, created a customized layout with installerconfig, install the Triton guesttools then build the custom ISO.

To build the OpenBSD KVM image run the `create-image` script:

```
./create-image -i <ISO> -n <IMAGE_NAME> -d <DESC> -u <HOMEPAGE> -o <OWNER_UUID> -p <IP> -m NETMASK -g <GATEWAY> -v <VLAN_ID> -U <NETWORK_UUID>
```

see `./create-image -h` for usage

```
doas ./create-iso -r 6.4 -m cdn.openbsd.org -p /pub/OpenBSD -i cd64.iso -d $(pwd)/iso -M $(pwd)/iso -l $(pwd)/layout/ -f openbsd64.iso -c SHA256
```
