# class-dump

TODO：

* 【基本解决】砸壳抖音ipa后导出iOS抖音头文件

---

* class-dump
  * 一句话描述：iOS逆向中导出ObjC的头文件的常用工具
    * 用于处理`Objective-C`的`Mach-O`文件信息的命令行工具，可以导出类的定义、分组和协议。
      * command-line utility for examining the Objective-C segment of Mach-O files
  * 说明
    * 和`otool -ov`导出的信息是一样的
      * 但是显示为`Objective-C`定义，更易读
  * 原理
    * 利用了`Objective-C`语言的运行时的特性
      * 将存储在`Mach-O`文件中的头文件信息提取出来，并生成对应的`.h`文件
  * 用途
    * 查看闭源的`应用`、`frameworks`、`bundles`
      * 查看其中的头文件信息
    * 对比一个 APP 不同版本之间的接口变化
      * 通过导出不同版本的库的头文件的对比看出来
    * 对一些私有`frameworks`做些有趣的试验

## 版本和下载

* `class-dump`版本
  * 概述
    * 推荐：支持Swift和ObjC混淆的版本
      * `MonkeyDev`中的`class-dump`
        * https://github.com/AloneMonkey/MonkeyDev/blob/master/bin/class-dump
  * 详解
    * 官网的版本
      * 安装包
        * [class-dump-3.5.dmg](http://stevenygard.com/download/class-dump-3.5.dmg)
      * 相关资料
        * GitHub
          * nygard/class-dump: Generate Objective-C headers from Mach-O files.
            * https://github.com/nygard/class-dump
        * 官网
          * class-dump - Steve Nygard
            * http://stevenygard.com/projects/class-dump/
        * 源码
          * [class-dump-3.5.tar.gz](http://stevenygard.com/download/class-dump-3.5.tar.gz)
            * 或：[class-dump-3.5.tar.bz2](http://stevenygard.com/download/class-dump-3.5.tar.bz2)
    * 升级版=优化版：支持swift和ObjC混淆
      * 有多个源
        * 比如
          * `MonkeyDev`中的`class-dump`
            * https://github.com/AloneMonkey/MonkeyDev/blob/master/bin/class-dump
        * 其他：待研究
          * https://github.com/0xced/class-dump
            * swift分支=swift版本
              * https://github.com/0xced/class-dump/tree/swift-binaries

## 用法

典型用法：

```bash
./class-dump --arch <arch> -H -o <outputFolder> <inputBinaryFile>
```

* 参数说明
  * `--arch`：指定架构
    * 最常见的值：`arm64`
    * 默认可以省略
      * 但如果是`FAT`=`胖二进制`时，则必须指定对应架构
  * `-H`：输出头文件
  * `-o`：输出目录

举例：

* `AwemeCore`
  ```bash
  MonkeyDev/bin/class-dump --arch arm64 -H AwemeCore -o /Users/crifan/dev/DevRoot/iOSReverse/Aweme/class_dump_output
  ```
* `Aweme`
  ```bash
  AloneMonkey/MonkeyDev/bin/class-dump --arch arm64 -H Aweme -o /Users/crifan/dev/DevRoot/Aweme/classDumpResult/17.8.0/Aweme
  ```
* `YouTube`
  ```bash
  class-dump --arch arm64 -H ../ipa/YouTube_17.08.2_dumped/Payload/YouTube.app/YouTube -o .
  ```
* `MusicallyCore`
  ```bash
  ./class-dump --arch arm64 -H ipa/Payload/TikTok.app/Frameworks/MusicallyCore.framework/MusicallyCore -o tiktok_headers_26.8.0
  ```
* 其他
  * class-dump AppKit
    * `class-dump /System/Library/Frameworks/AppKit.framework`
  * class-dump UIKit
    * `class-dump /Developer/Platforms/iPhoneOS.platform/Developer/SDKs/iPhoneOS4.3.sdk/System/Library/Frameworks/UIKit.framework`
  * class-dump UIKit and all the frameworks it uses
    * `class-dump /Developer/Platforms/iPhoneOS.platform/Developer/SDKs/iPhoneOS4.3.sdk/System/Library/Frameworks/UIKit.framework -r --sdk-ios 4.3`
  * class-dump UIKit (and all the frameworks it uses) from developer tools that have been installed in /Dev42 instead of /Developer
    * `class-dump /Dev42/Platforms/iPhoneOS.platform/Developer/SDKs/iPhoneOS5.0.sdk/System/Library/Frameworks/UIKit.framework -r --sdk-root /Dev42/Platforms/iPhoneOS.platform/Developer/SDKs/iPhoneOS5.0.sdk`

## 常见问题

TODO：

* 【记录】支持iOS的Swift和ObjC混编的class-dump
* 【已解决】class-dump导出Framework二进制AwemeCore报错：Cannot find offset for address in dataOffsetForAddress
* 【未解决】Mac中无法删除临时目录出现没有权限Operation not permitted
* 【已解决】砸壳后抖音ipa安装失败：DeviceNotSupportedByThinning

---

### class-dump导出头文件是空的

* 现象：抖音的二进制`AwemeCore`，用`class-dump`导出头文件是空的
* 原因：抖音内部代码应该是`Swift`和`ObjC`混编代码，原版`class-dump`只支持`ObjC`的，不支持`Swift`和`ObjC`混编，所以导出是空的。
* 解决办法：找支持Swift的版本的class-dump去导出，即可
  * 比如
    * `MonkeyDev`中的`class-dump`
      * https://github.com/AloneMonkey/MonkeyDev/blob/master/bin/class-dump
        * 相关命令
          ```bash
          MonkeyDev/bin/class-dump --arch arm64 -H AwemeCore -o crifan/Aweme/class_dump_output
          ```

## help帮助语法

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

## 使用心得

### 从`Generated by class-dump`可以看出原始用到了`class-dump`

之前从[WebDriverAgent](https://github.com/appium/WebDriverAgent)的源码中看到很多头文件的头部都有：`Generated by class-dump`

举例：

`refer/WebDriverAgent/PrivateHeaders/XCTest/XCTestDriver.h`

```c
//
//     Generated by class-dump 3.5 (64 bit).
//
//     class-dump is Copyright (C) 1997-1998, 2000-2001, 2004-2013 by Steve Nygard.
//
```

-》说明这些文件都是通过`class-dump`从库文件中导出生成的。
