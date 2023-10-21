# ldid的help语法

## Mac中的（用brew安装的）ldid

```bash
 /usr/local/bin/ldid --version
usage: /usr/local/bin/ldid -S[entitlements.xml] <binary>
  /usr/local/bin/ldid -e MobileSafari
  /usr/local/bin/ldid -S cat
  /usr/local/bin/ldid -Stfp.xml gdb
```

## iPhone11中的：ldid

（XinaA15越狱后的，TrollStore安装出的？）iPhone11中的：ldid

```bash
iPhone11-151:~ root# which ldid
/var/bin/ldid
iPhone11-151:~ root# ldid --version
Usage: ldid [-Acputype:subtype] [-a] [-C[adhoc | enforcement | expires | hard |
            host | kill | library-validation | restrict | runtime]] [-D] [-d]
            [-Enum:file] [-e] [-H[sha1 | sha256]] [-h] [-Iname]
            [-Kkey.p12 [-Upassword]] [-M] [-P[num]] [-Qrequirements.xml] [-q]
            [-r | -Sfile.xml | -s] [-u] [-arch arch_type] file ...
Common Options:
  -S[file.xml]  Pseudo-sign using the entitlements in file.xml
  -Kkey.p12     Sign using private key in key.p12
  -Upassword    Use password to unlock key.p12
  -M            Merge entitlements with any existing
  -h            Print CDHash of file

More information: 'man ldid'
```
