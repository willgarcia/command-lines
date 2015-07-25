strace/dtruss - summary
-----------------------

```
strace -c <cmd>
```

strace/dtruss - selective operations
------------------------------------

```
strace -e read,open <cmd>
```

strace/dtruss - relative time
-----------------------------

```
strace -r <cmd>
```

strace/dtruss - running process
-------------------------------

```
sudo strace -p <PID> -o <OUTFILE>
```
