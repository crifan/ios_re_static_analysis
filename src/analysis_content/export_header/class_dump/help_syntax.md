# class-dump的help语法

```bash
class-dump 3.5 (64 bit)
Usage: class-dump [options] <mach-o-file>

  where options are:
    -a             show instance variable offsets
    -A             show implementation addresses
    --arch <arch>  choose a specific architecture from a universal binary (ppc, ppc64, i386, x86_64)
    -C <regex>     only display classes matching regular expression
    -f <str>       find string in method name
    -H             generate header files in current directory, or directory specified with -o
    -I             sort classes, categories, and protocols by inheritance (overrides -s)
    -o <dir>       output directory used for -H
    -r             recursively expand frameworks and fixed VM shared libraries
    -s             sort classes and categories by name
    -S             sort methods by name
    -t             suppress header in output, for testing
    --list-arches  list the arches in the file, then exit
    --sdk-ios      specify iOS SDK version (will look in /Developer/Platforms/iPhoneOS.platform/Developer/SDKs/iPhoneOS<version>.sdk
    --sdk-mac      specify Mac OS X version (will look in /Developer/SDKs/MacOSX<version>.sdk
    --sdk-root     specify the full SDK root path (or use --sdk-ios/--sdk-mac for a shortcut)
```
