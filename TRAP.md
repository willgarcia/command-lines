trap signals
------------

```
trap command signal [INT|TERM|EXIT|...]
```

trap signals - example 1
------------------------

```
function before_exit () {
  info "Before exit. Done"
}
trap before_exit EXIT
```

trap signals - example 2
------------------------

```
if [ ! -e $lockfile ]; then
   trap "rm -f $lockfile; exit" INT TERM EXIT
   touch $lockfile
   critical-section
   rm $lockfile
   trap - INT TERM EXIT
else
   echo "critical-section is already running"
fi
```
