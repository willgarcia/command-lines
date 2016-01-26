salt - centos installation
--------------------------

```
yum install salt-api -y
openssl genrsa -out /etc/ssl/private/key.pem 4096
openssl req -new -x509 -key /etc/ssl/private/key.pem -out /etc/ssl/private/cert.pem -days 1826
mkdir -p /etc/ssl/private/
mkdir -p /etc/salt/master.d/
mkdir /salt/reactor/services/ -p

# conf

salt-master -l debug # or service salt-master restart 
service salt-api start
```

salt - versions-report
----------------------

```
salt-master --versions-report
```

salt - command (all minions)
--------------

```
salt '*' test.ping
salt "*" disk.usage
salt "*" cmd.run "ls /var/log -la"
```

salt - grains
-------------

```
salt "*" grains.items
salt -G 'os:Ubunt*' test.ping
salt -G 'biosversion:Virtua*' test.ping
```

salt - reactor
--------------

```
wget https://raw.github.com/saltstack/salt/develop/tests/eventlisten.py
python  eventlisten.py #master
curl -skv -H "Accept: application/json" -d tgt='*' -d service="httpd" -d  -k https://127.0.0.1:8080/hook/services/restart
```
