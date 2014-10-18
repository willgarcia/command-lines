See [Wget official documentation](https://www.gnu.org/software/wget/) for details.

wget - recursive mode from an http folder
----------------------------------

```shell
wget -r --no-parent --user=user --password=pass --reject "index.*" http://hello.com
```

wget - continue getting a partially-downloaded file
---------------------------------------------------

```shell
wget --continue http://mysite.com/big.file
```
