Chef - server installation
--------------------------

```shell
$ yum install https://web-dl.packagecloud.io/chef/stable/packages/el/6/chef-server-11.1.6-1.el6.x86_64.rpm
$ sudo chef-server-ctl reconfigure
```

See `http://docs.chef.io/open_source/install_server.html`

Chef - server configuration
---------------------------

```shell
$ mkdir /root/.chef
```

`/root/.chef/knife.rb`:

```shell
log_level                :info
log_location             STDOUT
node_name                'admin'
validation_client_name   'chef-validator'
chef_server_url          'https://chef-server.pub'
# see WebUI: User / Admin / Edit (/!\ do not regenerate any existing key)
client_key               '/root/.chef/chef.pem'
validation_key           '/root/.chef/chef_validator.pem'
```

Knife - installation
--------------------

```shell
$ curl -L https://www.chef.io/chef/install.sh | bash
$ knife --version
$ knife ssl fetch
```

Knife - controls
----------------

```shell
$ knife ssl verify
$ knife ssl check
$ knife cookbook list
$ knife role list
```

Remove `/etc/chef/*` to regenerate the Chef-client SSL certificates if expired.

Chef - workstation install
--------------------------

See `http://docs.chef.io/open_source/install_workstation.html`

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
