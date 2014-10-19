sys - change the default /tmp dir (symlink)
-------------------------------------------

```shell
mkdir /home/tmp
ln -s /home/tmp /tmp
chmod +t /home/tmp
chmod a+w /home/tmp
```

sys - kill a process by name
----------------------------

```shell
kill `pidof httpd`
```

sys - get top 10 processes eating memory
-------------------------------------

```shell
ps aux | sort -nr -k 4 | head -10'
```

sys - get top 10 processes eating cpu
-------------------------------------

```shell
ps auxf | sort -nr -k 3 | head -10'
```

sys - add a user
----------------

```shell
useradd -m -s /bin/bash myuser
passwd myuser
```

sys - who is online
-------------------

```shell
w
```

sys - find in-use binary path
-----------------------------

```shell
which myapp
whereis myapp
```

sys - re initialize terminal
----------------------------

```shell
reset
```

sys - count lines
-----------------

```shell
cat myfile | wc -l
```
