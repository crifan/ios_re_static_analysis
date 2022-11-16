# jtool2

* `jtool`
  * 新版叫：`jtool2`
  * 类似于`otool`的，解析查看`Mach-O`文件格式信息
    * 区别：添加了许多Mach-O相关的命令
      * jtool比otool功能更完善
  * 支持多种运行平台
    * `OS X`=`Mac`
    * `iOS`
    * `Linux`
  * 功能
    * in-binary search functionality
    * symbol injection
    * built-in disassembler functionality with (limited but constantly improving) emulation capabilities, which already outdo fancy commercial GUI disassemblers.
    * Color terminal output, enabled by JCOLOR=1
  * 资料
    * 官网
      * JTool2 - Taking the O out of otool - squared
        * http://www.newosxbook.com/tools/jtool.html

## 安装jtool2

`Mac`中安装`jtool2`：

* 方式1：`brew`
  ```bash
  brew install --cask jtool2
  ```
* 官网下载二进制
  * 从[JTool2官网](http://www.newosxbook.com/tools/jtool.html)下载[jtool2.tgz](http://www.newosxbook.com/tools/jtool2.tgz)
  * 解压得到：`jtool2`（和`disarm`）
    * 提示：可以把路径加到启动脚本的`PATH`中（再source），使得命令行中可以使用

## 使用jtool2

### 查看基本头文件信息

```bash
jtool2 -h yourBinary
```

举例：

```bash
➜  AwemeCore jtool2 -h v18.9.0/Payload/Aweme.app/Frameworks/AwemeCore.framework/AwemeCore
Magic:    64-bit MachO (Little Endian)
Type:    dylib
CPU:    ARM64 (ARMv8)
Cmds:    133
Size:    18720
Flags:    0x910085
```

### list列出段

```bash
jtool2 -l v18.9.0/Payload/Aweme.app/Frameworks/AwemeCore.framework/AwemeCore
```

### 查看使用了哪些共享库

```bash
jtool2 -L v18.9.0/Payload/Aweme.app/Frameworks/AwemeCore.framework/AwemeCore
```

### 列出符号表 == nm

```bash
jtool2 -S v18.9.0/Payload/Aweme.app/Frameworks/AwemeCore.framework/AwemeCore > AwemeCore_jtool2_S.txt
```

### 分析 -》 导出类和函数名等

```bash
jtool2 --analyze v18.9.0/Payload/Aweme.app/Frameworks/AwemeCore.framework/AwemeCore
```

总体来说，还是有点用的。尤其是`--analyze`

## jtool2相关资料

* 官网
  * [JTool2 - Taking the O out of otool - squared (newosxbook.com)](http://www.newosxbook.com/tools/jtool.html)

### 常见命令的常见用法举例

官网[JTool2 - Taking the O out of otool - squared (newosxbook.com)](http://www.newosxbook.com/tools/jtool.html)中就有语法介绍：

```bash
* Otool Compatible options
* dyldinfo Compatible options
* Advanced options:
    * -pages (get layout)
    * -a (lookup address)
    * -S
* Code Singing options
    * --sig
    * --ent
    * --sign
* Objective-C
* Darn Cool Options
```

对应的别人的中文翻译：

[【OSG】jtool - Taking the O out of otool(1)-iOS安全-看雪论坛-安全社区|安全招聘|bbs.pediy.com](https://bbs.pediy.com/thread-220100.htm)
