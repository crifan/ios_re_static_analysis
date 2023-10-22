# ldid的help语法

## ldid的help语法

### Mac中的（用brew安装的）ldid

```bash
 /usr/local/bin/ldid --version
usage: /usr/local/bin/ldid -S[entitlements.xml] <binary>
  /usr/local/bin/ldid -e MobileSafari
  /usr/local/bin/ldid -S cat
  /usr/local/bin/ldid -Stfp.xml gdb
```

### iPhone11中的：ldid

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

## ldid的man page

```bash
LDID(1)               FreeBSD General Commands Manual                LDID(1)

NAME
     ldid – Link Identity Editor

SYNOPSIS
     ldid [-aDdehMPqu] [-Acputype:subtype]
          [-C[adhoc | enforcement | expires |
          hard | host | kill | library-validation | restrict | runtime]]
          [-Kkey.p12] [-r | -Sfile | -s] [-Ttimestamp] file ...

DESCRIPTION
     ldid adds SHA1 and SHA256 hashes to a Mach-O file so that they can be run
     on a system that has validation but not signature verification.

     -a       Print the CPU types and subtypes in hexadecimal.

     -Acputype:subtype
              When used with -a, -D, -e, -h, -q, or -u, only act on the slice
              specified by cputype and subtype.  cputype and subtype should
              both be integers.

     -C[adhoc | enforcement | expires | hard | host | kill |
              library-validation | restrict | runtime]
              Specify the option flags to embed in the code signature.  See
              codesign(1) for details about these options.

     -D       Reset the cryptid.

     -d       Print the cryptid in the binaries if it exists.  For
              compatibility reasons it also acts as -h, but this will be
              removed in the future.

     -e       Print the entitlements in each slice, or the slice specified by
              -A, to stdout.

     -h       Print information about the signature, such as hash types,
              flags, CDHash, and CodeDirectory version to stdout.

     -Kkey.p12
              Sign using the identity in key.p12.  This will give the binary a
              valid signature so that it can be run on a system with signature
              validation.  key.p12 must not have a password.

     -M       When used with -S, merge the new and existing entitlements
              instead of replacing the existing entitlements, this is useful
              for adding a few specific entitlements to a handful of binaries.

     -P       Mark the Mach-O as a platform binary.

     -Qfile   Embed the requirements found in file.

     -q       Print embedded requirements of the binaries.

     -r       Remove the signature from the Mach-O.

     -S[file]
              Pseudo sign the Mach-O binaries.  If file is specified then the
              entitlements found in file will be embedded in the Mach-O.

     -s       Resign the Mach-O binaries while keeping the existing
              entitlements.

     -Ttimestamp
              When signing a dylib, set the timestamp to timestamp.  timestamp
              should be an UNIX timestamp in seconds, if timestamp is a single
              dash (‘-’), the timestamp will be set to a hash of the Mach-O
              header.

     -u       If the binary was linked against UIKit, then print the UIKit
              version that the Mach-O binaries was linked against.

EXAMPLES
     The command:

           ldid -S file

     will fakesign file with no entitlements.

     The command:

           ldid -Cadhoc -K/path/to/key.p12 -Sent.xml file

     will sign file using the key in /path/to/key.p12 with the entitlements
     found in ent.xml, and mark it as an adhoc signature.

     The command:

           ldid -Sent.xml -M file

     will add the entitlements in ent.xml to the entitlements already in file.

     The command:

           ldid -e file > ent.xml

     will save the entitlements found in each slice of file to ent.xml.

SEE ALSO
     codesign(1)

HISTORY
     The ldid utility was written by Jay "Saurik" Freeman.  iPhoneOS 1.2.0 and
     2.0 support was added on April 6, 2008.  -S was added on June 13, 2008.
     SHA256 support was added on August 25, 2016, fixing iOS 11 support.  iOS
     14 support was added on July 31, 2020 by Kabir Oberai.  iOS 15 support
     was added on June 11, 2021.

iPhoneDevWiki                   October 8, 2021                  iPhoneDevWiki
```
