# bento-almalinux9-arm-only
These scripts are a basic version of a [Bento's](https://github.com/chef/bento) packer template for building an almalinux 9 box for m1/m2 arm Macs.

It fixes the SSH key insertion in `vagrant.sh` which otherwise fails as a result of the reboot happening in `update.sh`. Presumably this is because the network is not ready when it tries to download the vagrant key.

The solution was to move the `update.sh` script to it's own provisioner block and add a `"pause_after": "30s"` setting. 

Steps to test

```
packer build -debug almalinux-9.0-aarch64.json
vagrant box add -f builds/almalinux-9.0.parallels.box builds/almalinux-9.0.parallels.box
vagrant up
```
