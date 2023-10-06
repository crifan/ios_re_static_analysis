# 静态分析内容

iOS逆向的静态分析，主要针对的是：

* iOS的二进制格式：`Mach-O`
  * `Mach-O`工具
    * 概述
      * 查看解析Mach-O
        * `MachOView`
        * `rabin2`
        * `jtool2`
        * `otool`
      * FAT瘦身
        * `lipo`
    * 详解
      * 独立子教程
        * [可执行文件格式：Mach-O](https://book.crifan.org/books/exec_file_format_macho/website/)
  * 其他处理
    * 导出字符串等资源：用于后续研究搜索函数、类等用途
      * `nm`
      * `strings`
    * 处理签名：重新签名避免运行崩溃
      * `ldid`
      * `codesign`
    * 导出头文件：研究类的具体函数和属性
      * `class-dump`
    * 分析代码逻辑：分析研究代码实现逻辑和其他各种细节
      * `IDA`
      * `Hopper`
