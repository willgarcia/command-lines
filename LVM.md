Inspired by my team mate: http://monblog.system-linux.net/blog/2014/02/27/ajout-dun-disque-a-chaud-vmwa-lvm/

Disk - information about logical/physical volumes

```
pvs 
```

Disk - list partitions

```
fdisk -L
dmesg
```

Disk - partitionning

```
fdisk /dev/sdc
```

LVM - partition initialization

```
pvcreate /dev/sdc1
```

LVM - volume extension by group / partition

```
vgextend VolGroup01 /dev/sdc1
```

LVM - volumes information

```
vgdisplay
```

LVM - logical volume extension

```
lvextend -l +6398 /dev/VolGroup01/LogVol00
```

Disk - physical extension ext2/ext3/ext4

```
resize2fs /dev/VolGroup01/LogVol00
```
