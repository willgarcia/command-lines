* See [BASH official documentation](http://www.gnu.org/software/bash/) for details.
* See also [BASH options](http://www.tldp.org/LDP/abs/html/options.html).
* See also [Logger in BASH](http://krypted.com/mac-os-x/logger-in-bash-2/).
* See also [BASH Google Guidelines](https://google-styleguide.googlecode.com/svn/trunk/shell.xml)

bash - current dir/file
-----------------------

```
WORK_DIR="$(cd "$(dirname "${BASH_SOURCE[0]}")" && pwd)"
ROOT_DIR="$(cd "$(dirname "${WORK_DIR}")" && pwd)"
WORK_SCRIPT="${WORK_DIR}/$(basename "${BASH_SOURCE[0]}")"
BASE_SCRIPT="$(basename ${WORK_SCRIPT} .sh)"
```

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
set -o nounset
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
```

bash - exit on pipefail
-----------------------

```
set -o pipefail
```

bash - allow a command to fail
------------------------------

```
<CMD> || true
<CMD> || :
```

bash - debug mode
-----------------

```
set -x 
set -o xtrace 
```

bash - readonly variable

```
readonly var="ro"
```
