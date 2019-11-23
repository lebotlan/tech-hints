# tech-hints
Unordered list of misc. technical hints.


# Linux encryption

## Steps to encrypt a directory in linux.

### Install packages
`sudo apt-get install libpam-fscrypt`

You probably don't need these:
```
sudo pam-auth-update
sudo fscrypt setup
```

### Prepare device and parent directories(?) for encryption
```
sudo tune2fs -O encrypt /dev/device
fscrypt status

sudo fscrypt setup /
sudo fscrypt setup /home
fscrypt status
```

I don't know if you need to fscrypt setup all the parent dirs.

`fscrypt encrypt file-or-dir`

Beware, it creates a new 'policy' for each new encrypted dir (and asks for a password). 

 - Solution 1 : see the note below (one encrypted dir, many symlinks)
 - Solution 2 : create new dirs below an already encrypred one (mkdir Bar/Foo), then move Foo elsewhere.


### Note: afaik you cannot encrypt your homedir, but here is my current setting:

```
HOMEDIR/  uncrypted
HOMEDIR/BLA  encrypted
HOMEDIR/whatever-1 -> HOMEDIR/BLA/whatever-1
HOMEDIR/whatever-2 -> HOMEDIR/BLA/whatever-2
...
```

## Sources

https://github.com/google/fscrypt
https://www.kernel.org/doc/html/v4.18/filesystems/fscrypt.html
