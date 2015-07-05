See [Max RPM documentation](http://www.rpm.org/max-rpm-snapshot/) for details.
Section: [Max RPM documentation - Chapter 5. Getting Information About Packages](http://www.rpm.org/max-rpm/ch-rpm-query.html).

rpm - list files inside an rpm
------------------------------

```shell
rpm -ql packageName
```

```shell
rpm -qpl file.rpm
```

rpm - list dependencies (not installed)
---------------------------------------

```shell
rpm -Uvh --test <package.rpm>
```

rpm - list dependencies (installed)
-----------------------------------

```shell
$ rpm  rpm -qR <package.rpm>
```
