# Lapawa Dockerfile vsphere-perl-sdk
Packaging [VMware Perl SDK](http://developercenter.vmware.com/web/sdk/60/vsphere-perl) and vSphere CLI in a
docker container.


Dependencies
------------------------
The container is build from the official Ubuntu 16.04LTS image.


Building the container
------------------------

 * Download your copy of VMware Perl SDK from
   [my VMware Portal](https://my.vmware.com/group/vmware/get-download?downloadGroup=PERLSDK60U2)
   ( Registration necessary )
 * Place VMware-vSphere-Perl-SDK-6.0.0-3561779.x86_64.tar.gz in build directory.
 * Build container with:
```bash
docker build --tag perl-vsphere-sdk:6.0.2 .
```

Usage
------------------------

Get an interactive shell with:
```bash
docker run --interactive --tty --rm perl-vsphere-sdk:6.0.2 
```

