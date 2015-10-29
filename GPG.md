gpg - error list
--------------

```
gpg-error --list
```


gpg - search
--------------

```
gpg --search-keys [username]
```

gpg - gen-key
--------------

```
gpg --gen-key
```

gpg - export key
------------

```
gpg --export-secret-keys --armor [email] > ~/willg.gpg
```
 
gpg - sign key
------------

```
gpg --sign-key [KEY-NUMBER]
```

gpg - encrypt
------------

```
gpg --encrypt /my/message
```

gpg - register key
-------------

```
gpg --keyserver pgp.mit.edu --send-keys [KEY-NUMBER]
```
