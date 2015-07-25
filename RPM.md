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

rpm - dependencies treeview (installed)
---------------------------------------

```
yum install rpmreaper
rpmreaper
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

rpm - which package does a file belongs to
------------------------------------------

```shell
$ yum whatprovides '/etc/environment'
```

rpm - show scripts
------------------

```shell
rpm -ql --scripts my.rpm
````
