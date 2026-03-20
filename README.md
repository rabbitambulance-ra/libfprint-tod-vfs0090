## Validity `138a:0090` and `138a:0097` libfprint driver

This repository exists for the `vfs0090` driver itself.

It is the narrower, driver-side companion to the parent repository's broader Linux runtime workflow for Validity `138a:0090` and `138a:0097` devices.

## Who This Helps

This repo is useful if you:

* need the `vfs0090` `libfprint` driver code on its own
* are maintaining or packaging the driver separately from the rest of the Linux fingerprint stack
* need the pairing-identity override support for `138a:0090`

## Why This Fork Exists

The key addition in this fork is support for overriding the `138a:0090` pairing identity through environment variables:

```bash
VFS0090_PRODUCT_NAME=...
VFS0090_PRODUCT_SERIAL=...
```

That matters for sensors whose paired state was created against a host identity Linux cannot infer from local DMI data alone, for example a VM-paired Windows state.

## Scope

This repository covers the driver side only.

It does not provide the full end-to-end `138a:0090` runtime workaround by itself. The broader workflow still depends on:

* `python-validity`
* `open-fprintd`
* `fprintd`
* local pairing-identity and SID configuration

If you need the full replayable Linux-side workflow, use the parent repository.

## Devices

* `138a:0090`
* `138a:0097`

For `138a:0097`, Linux-side match-on-sensor enrollment is the normal path.

For `138a:0090`, this driver can be one part of a working setup, but the paired-state runtime behavior lives outside this repository.

## Packaging

This repository still carries the original Debian packaging metadata for the TOD-style driver packaging flow.

If you are packaging for another distro, treat that metadata as an example rather than a universal installation path.

## Provenance

This work builds on earlier reverse engineering and prototype work from [nmikhailov](https://github.com/nmikhailov/Validity90/) and [uunicorn](https://github.com/uunicorn/python-validity).
