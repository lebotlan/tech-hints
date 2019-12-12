# Linux encryption

## Steps to encrypt a directory in linux.

### 1 - Install packages
`sudo apt-get install libpam-fscrypt`

These are probably already done by the package:
```
sudo pam-auth-update
sudo fscrypt setup
```

### 2 - Prepare device and parent directories for encryption
```
sudo tune2fs -O encrypt /dev/device
fscrypt status

sudo fscrypt setup /
sudo fscrypt setup /home
fscrypt status
```

I don't know if you need to fscrypt setup all the parent dirs.

### 3 - Encrypt a file or a directory
`fscrypt encrypt file-or-dir`

Beware, it creates a new 'policy' for each new encrypted dir (and asks for a password). 

 - Solution 1 : see the note below (one encrypted dir, many symlinks)
 - Solution 2 : encrypt Bar, then create new dirs under Bar (mkdir Bar/Foo), then move Foo elsewhere.


### Note: afaik you cannot encrypt your homedir (it might break things), but here is my current setting:

```
HOMEDIR/  uncrypted
HOMEDIR/BLA  encrypted, contains everything
HOMEDIR/whatever-1 -> HOMEDIR/BLA/whatever-1
HOMEDIR/whatever-2 -> HOMEDIR/BLA/whatever-2
...
```

## Sources

 - https://github.com/google/fscrypt
 - https://www.kernel.org/doc/html/v4.18/filesystems/fscrypt.html
