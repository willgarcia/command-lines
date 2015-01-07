See [Git official documentation](http://git-scm.com/documentation) for details.

git - clone single branch
-------------------------

```shell
git clone <url> --branch <branch> --single-branch [<folder>]
```

git - edit old commit messages
------------------------------

```shell
git rebase -i HEAD~(count)
# edit message manually: pick 123456 bad message -> edit 123456 good message
git commit --amend
git rebase --continue
git push -f
```

git - squash
------------

```shell
git checkout branche-dest
git merge --squash branche-dev
git commit
git push
```

git - filter branch
-------------------

```shell
git filter-branch --tree-filter 'rm -rf tests/' --tag-name-filter cat --prune-empty -- --all 
git push -f
git push -f --tags
```


git - migrate a directory from a SRC repository to a DEST repository
--------------------------------------------------------------------

```shell
SRC_REPO=[URL SRC]
SRC_DIR=tests
OUTPUT_REPO=[URL DEST]
TMP_DIR=$(mktemp -d)
git clone $SRC_REPO $TMP_DIR;
git filter-branch --prune-empty --subdirectory-filter $SRC_DIR master
git push $OUTPUT_REPO master
```

git - is a tag
----------------

```shell
git describe --exact-match --tags $(git log -n1 --pretty='%h')
```

git - show the last git
-----------------------

```shell
git describe --tags `git rev-list --tags --max-count=1`
```

git - patch
-----------

```shell
git format-patch branch1..master
git ma *.patch
```

git - migrate a repository
--------------------------

```shell
git clone $SRC_REPO $PATH
cd $PATH
git fetch origin
git remote add dest-origin $DEST_REPO
git push dest-origin master:master -u
git push dest-origin --tags
git push dest-origin '+refs/remotes/origin/*:refs/heads/*'
cd -
```

git - Locally and remotely rename a branch
-------------------------------------------

```shell
git branch -m feature-1R feature-14
```

git - list unmerged branches
----------------------------

```shell
git branch -a --merged master
```

git - branch exists
-------------------

```shell
$BRANCH=mybranch
git --git-dir="$WORKSPACE/.git" branch -r | grep -P "^\s*(?:origin/)?$BRANCH" > /dev/null
```
