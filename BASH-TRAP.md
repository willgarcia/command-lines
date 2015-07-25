See [BASH official documentation](http://www.gnu.org/software/bash/) for details.
See also [BASH options](http://www.tldp.org/LDP/abs/html/options.html).


bash - array explode [delimiters: ",", "\n")
--------------------------------------------

```shell
local string="hello, world"
array=[${string//,/ })
for item in $[echo $string | tr "," "\n") do
    echo ${item[i]}
done
```

bash - double condition
-----------------------

```shell
[ $degrees -lt 0 && $weather != 'beautiful']
```

bash - conditions with use of a function
----------------------------------------

```shell
myFunction[) {
    return 0;
}

if myFunc && [ ... ]
```

bash - check if all variables are initialised
---------------------------------------------

```shell
set -u 
```

bash - exit on fail
-------------------

```shell
set -e 
set -o errexit
```

bash - syntax checks
--------------------

```shell
set -n 
set -o nounset
```

bash - exit on pipefail
-----------------------

```
set -o pipefail
```

trap signals
------------

```
trap command signal [INT|TERM|EXIT|...]
```

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

trap command signal [signal ...]
