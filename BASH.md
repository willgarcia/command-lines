See [BASH official documentation](http://www.gnu.org/software/bash/) for details.


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
```

bash - syntax checks
--------------------

```shell
bash -n 
```
