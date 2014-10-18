See [ioreg official documentation](https://developer.apple.com/library/mac/documentation/Darwin/Reference/ManPages/man8/ioreg.8.html) for details.

osx - battery usage
-------------------

```bash
echo `ioreg -l | grep -i capacity | tr '\n' ' | ' | awk '{print int($10/$5*100)}'`
```

osx - battery cycle count
-------------------------

```bash
echo `ioreg -w0 -l | grep "Cycle Count" | awk 'BEGIN { FS = "=" } ; {print $8}' | awk 'BEGIN { FS = "}" } ; {print $1}'` 
```
