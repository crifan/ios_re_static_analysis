# rabin2

## 下载和安装

从官网[radare](https://rada.re/n/radare2.html)，找到下载地址来源，比如

[Releases · radareorg/radare2](https://github.com/radareorg/radare2/releases)

下载对应的版本，比如我此处的：

* Mac
  * Intel Chip
    * [radare2-x64-5.7.8.pkg](https://github.com/radareorg/radare2/releases/download/5.7.8/radare2-x64-5.7.8.pkg)

然后去安装pkg包，安装后，即可有`/usr/local/bin/rabin2`

之前某次安装后的版本：

```bash
➜  ~ rabin2 --version
rabin2: illegal option -- -
rabin2 4.3.1 134 @ darwin-x86-64 git.4.3.1
commit: 815529f204bede6a232fce8b3ac88a905c6943c6 build: 2020-03-06__16:31:10
```

## 用法

### 用rabin2查看抖音AwemeCore二进制的信息

* (1) File Identification
  ```bash
  rabin2 -I v18.9.0/Payload/Aweme.app/Frameworks/AwemeCore.framework/AwemeCore
  ```
* (2)Entrypoint
  ```bash
  rabin2 -e v18.9.0/Payload/Aweme.app/Frameworks/AwemeCore.framework/AwemeCore
  ```
* (3)Imports
  ```bash
  rabin2 -i v18.9.0/Payload/Aweme.app/Frameworks/AwemeCore.framework/AwemeCore
  ```
* (4)Exports
  ```bash
  rabin2 -E v18.9.0/Payload/Aweme.app/Frameworks/AwemeCore.framework/AwemeCore > AwemeCore_rabin2_E.txt
  ```
* (5)Symbols
  ```bash
  rabin2 -s v18.9.0/Payload/Aweme.app/Frameworks/AwemeCore.framework/AwemeCore > AwemeCore_rabin2_s.txt
  rabin2 -sr v18.9.0/Payload/Aweme.app/Frameworks/AwemeCore.framework/AwemeCore > AwemeCore_rabin2_sr.txt
  ```
* (6)Libraries
  ```bash
  rabin2 -l v18.9.0/Payload/Aweme.app/Frameworks/AwemeCore.framework/AwemeCore > AwemeCore_rabin2_l.txt
  ```
* (7)Strings
  ```bash
  rabin2 -z v18.9.0/Payload/Aweme.app/Frameworks/AwemeCore.framework/AwemeCore > AwemeCore_rabin2_z.txt
  rabin2 -zr v18.9.0/Payload/Aweme.app/Frameworks/AwemeCore.framework/AwemeCore > AwemeCore_rabin2_zr.txt
  ```
* (8)Program Sections
  ```bash
  rabin2 -S v18.9.0/Payload/Aweme.app/Frameworks/AwemeCore.framework/AwemeCore > AwemeCore_rabin2_S_section.txt
  rabin2 -Sr v18.9.0/Payload/Aweme.app/Frameworks/AwemeCore.framework/AwemeCore > AwemeCore_rabin2_Sr_section.txt
  ```

## 心得

很多的参数，都可以加上r，表示（输出内容是一致的，但是格式不同）以radare格式输出

举例：

```bash
rabin2 -I
rabin2 -Ir

rabin2 -s
rabin2 -sr

rabin2 -z
rabin2 -zr

rabin2 -S
rabin2 -Sr
```

等等

## rabin2的help语法

```bash
➜  ~ rabin2 --help
rabin2: illegal option -- -
Usage: rabin2 [-AcdeEghHiIjlLMqrRsSUvVxzZ] [-@ at] [-a arch] [-b bits] [-B addr]
              [-C F:C:D] [-f str] [-m addr] [-n str] [-N m:M] [-P[-P] pdb]
              [-o str] [-O str] [-k query] [-D lang symname] file
 -@ [addr]       show section, symbol or import at addr
 -A              list sub-binaries and their arch-bits pairs
 -a [arch]       set arch (x86, arm, .. or <arch>_<bits>)
 -b [bits]       set bits (32, 64 ...)
 -B [addr]       override base address (pie bins)
 -c              list classes
 -cc             list classes in header format
 -C [fmt:C:D]    create [elf,mach0,pe] with Code and Data hexpairs (see -a)
 -d              show debug/dwarf information
 -D lang name    demangle symbol name (-D all for bin.demangle=true)
 -e              entrypoint
 -ee             constructor/destructor entrypoints
 -E              globally exportable symbols
 -f [str]        select sub-bin named str
 -F [binfmt]     force to use that bin plugin (ignore header check)
 -g              same as -SMZIHVResizcld -SS -SSS -ee (show all info)
 -G [addr]       load address . offset to header
 -h              this help message
 -H              header fields
 -i              imports (symbols imported from libraries)
 -I              binary info
 -j              output in json
 -k [sdb-query]  run sdb query. for example: '*'
 -K [algo]       calculate checksums (md5, sha1, ..)
 -l              linked libraries
 -L [plugin]     list supported bin plugins or plugin details
 -m [addr]       show source line at addr
 -M              main (show address of main symbol)
 -n [str]        show section, symbol or import named str
 -N [min:max]    force min:max number of chars per string (see -z and -zz)
 -o [str]        output file/folder for write operations (out by default)
 -O [str]        write/extract operations (-O help)
 -p              show physical addresses
 -P              show debug/pdb information
 -PP             download pdb file for binary
 -q              be quiet, just show fewer data
 -qq             show less info (no offset/size for -z for ex.)
 -Q              show load address used by dlopen (non-aslr libs)
 -r              radare output
 -R              relocations
 -s              symbols
 -S              sections
 -SS             segments
 -SSS            sections mapping to segments
 -t              display file hashes
 -T              display file signature
 -u              unfiltered (no rename duplicated symbols/sections)
 -U              resoUrces
 -v              display version and quit
 -V              Show binary version information
 -w              display try/catch blocks
 -x              extract bins contained in file
 -X [fmt] [f] .. package in fat or zip the given files and bins contained in file
 -z              strings (from data section)
 -zz             strings (from raw bins [e bin.rawstr=1])
 -zzz            dump raw strings to stdout (for huge files)
 -Z              guess size of binary program
Environment:
 RABIN2_LANG:      e bin.lang         # assume lang for demangling
 RABIN2_NOPLUGINS: # do not load shared plugins (speedup loading)
 RABIN2_DEMANGLE=0:e bin.demangle     # do not demangle symbols
 RABIN2_MAXSTRBUF: e bin.maxstrbuf    # specify maximum buffer size
 RABIN2_STRFILTER: e bin.str.filter   #  r2 -qc 'e bin.str.filter=??' -
 RABIN2_STRPURGE:  e bin.str.purge    # try to purge false positives
 RABIN2_DEBASE64:  e bin.debase64     # try to debase64 all strings
 RABIN2_DMNGLRCMD: e bin.demanglercmd # try to purge false positives
 RABIN2_PDBSERVER: e pdb.server       # use alternative PDB server
 RABIN2_SYMSTORE:  e pdb.symstore     # path to downstream symbol store
 RABIN2_PREFIX:    e bin.prefix       # prefix symbols/sections/relocs with a specific string
 R2_CONFIG:        # sdb config file
```

## 资料

* `Radare2`官网资料
  * [Introduction - The Official Radare2 Book](https://book.rada.re/index.html)
    * [Rabin2 - The Official Radare2 Book](https://book.rada.re/tools/rabin2/intro.html)
