See [Chef server / workstation installation](INSTALLATION.md)

Chef - Cookbook upload
----------------------

Upload the cookbook(s) specified in the `Berksfile` to the Chef Server

```shell
$ berks install
$ berks upload
```

Chef - Node deployment
----------------------

```shell
$ knife bootstrap 10.29.1.13
```

Chef - Node deployment with role(s)
-----------------------------------

```shell
knife bootstrap chef-server -r "role[base]"
```

Chef - server config versionning / update
-----------------------------------------

```shell
$ knife download/upload .
```

Chef - kitchen test
-------------------

```
kitchen test
kitchen converge
```

Chef - foodcritic linter
------------------------

```
foodcritic . --epic-fail any
```
