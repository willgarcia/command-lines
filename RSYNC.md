See [Rsync official documentation](http://rsync.samba.org/) for details.

rsync - rsync over ssh with symlinks
------------------------------------

```shell
rsync -avz -e ssh /my/path/with/symlinks user@host:
```

rsync - delete-excluded
-----------------------

```shell
rsync -avz --recursive --delete --delete-excluded --exclude .git* -e ssh /my/path user@host:
```
