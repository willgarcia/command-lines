ssh - restart ssh-agent
-----------------------

```shell
eval `ssh-agent -s` 
ssh-add ~/.ssh/*_rsa
```

ssh - rebounce from an host to an other
---------------------------------------

```shell
ssh -t remoteUser1@server1 ssh remoteUser2@server2
```

ssh - tunneling
---------------

```shell
# -f: Background the ssh process
# -N: Tell ssh to not run any commands, just set up a tunnel
# -L0.0.0.0:[local-redirected-port]: used for port forwarding 
ssh -f -L0.0.0.0:[local-redirected-port]:[local-host]:[remote-port] [remote-user]@[remote-host] -N
```

