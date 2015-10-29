Identify a read only partition
---------------

```
grep ' ro ' /proc/mounts
```

Remount read only partition
---------------

```
mount -o remount,rw /
```

fsck - disk check (prevent Fsck on Mounted Filesystem)
------------

```
fsck -M /dev/sda7
```

fsck - disk repair
-------------

```
fsck [-y/-a] /dev/sda6
```
