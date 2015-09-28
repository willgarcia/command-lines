* See [smartctl official documentation](https://www.smartmontools.org/wiki/TocDoc). Smartctl can be used as daemon and send alerts by email..
* See [mount options](http://linux.die.net/man/8/mount)

smartctl disk tests capabilities
--------------------------------

```
smartctl -c /dev/sda
```

smartctl list tests
-------------------

```
smartctl -d cciss,0  -a /dev/cciss/c0d1
```

smartctl short test
-------------------

```
smartctl -d cciss,0 --test=short /dev/cciss/c0d1
```

partition identifer
-------------------

```
mount -v | grep "^/" | awk '{print "\nPartition identifier: " $1  "\n Mountpoint: "  $3}'
```

partition remount
-----------------

```
mount -o remount,rw /partition/identifier /mount/point
```
