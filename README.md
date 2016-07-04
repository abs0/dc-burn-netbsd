dc-burn-netbsd
==============

Script to create a bootable NetBSD/dreamcast CD

Expected to be run as part of the dc-tools pkgsrc package

Requirements:
- cdrtools (for mkisofs & cdrecord)
- Marcus Comstedt's makeip & scramble as dc-makeip & dc-scramble respectively

```
Usage: dc-burn-netbsd [opts]
 -C      : Clean work directory before starting
 -b      : Burn generated image to CD using cdrecord
 -c opts : Set cdrecord opts (driveropts=burnfree gracetime=3)
 -d dist : Take kernel/ & sets/ under dist dir - will not try to download
 -e      : Boot resultant image under an emulator (requires gxemul)
 -h      : This help
 -k type : Set kernel type (GENERIC_MD) eg: GENERIC or GENERIC_MD
 -l      : Setup live cd - implies '-s base -K GENERIC' unless otherwise set
 -s type : Include NetBSD release, type is base, std, x or list of sets
 -t tmpd : Set temporary work directory to tmpd
 -v vers : Set NetBSD version (7.0.1) use '?' for list
```

dc-burn will create a temporary work directory dc-burn-netbsd-files which will
need to have sufficient space to store the downloaded & generated files.

if -d is used the directory is expected to match the layout on ftp.netbsd.org:
 - kernel/netbsd-$type.bin.gz
 - sets/base.tgz ... etc (if -s given)

