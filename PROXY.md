Proxy setting - `/etc/profile.d/proxy.sh`
------------------

```
HTTP_PROXY_URL='http://mon.proxy:port/'   
export http_proxy=$HTTP_PROXY_URL
HTTPS_PROXY_URL='https://mon.proxy:port/'   
export https_proxy=$HTTPS_PROXY_URL
```

Validate a proxy setting - traceroute
------------------

```
traceroute host
```

Validate a proxy setting - env
------------------

```
env | grep -i proxy
wget -q -O - checkip.dyndns.org | sed -e 's/.*Current IP Address: //' -e 's/<.*$//'
```
