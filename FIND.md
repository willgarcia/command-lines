See [Find official documentation](http://www.gnu.org/software/findutils/manual/find.html) and [AG official documentation](https://github.com/ggreer/the_silver_searcher) for details.

find - find and delete all files except those matching a pattern
----------------------------------------------------------------

```shell
find /my/path -type f ! -name 'fr*.dat' -delete
```

locate - find all instances of file
-----------------------------------

```shell
updatedb
locate myfile
```

ag - find in files
------------------

```shell
ag /regexp/ /my/path
```

