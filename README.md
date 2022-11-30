# bento-almalinux9-arm-only
A basic version of a [Bento](https://github.com/chef/bento) packer template for building almalinux 9 arm only. 

Using this to test the SSH key insertion step.

Steps to test

```
packer build -debug almalinux-9.0-aarch64.json
vagrant box add -f builds/almalinux-9.0.parallels.box builds/almalinux-9.0.parallels.box
vagrant up
```
