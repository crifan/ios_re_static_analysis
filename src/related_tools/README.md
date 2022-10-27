# 相关工具

对于iOS逆向中的静态分析，其实还有其他一些相关工具，值得介绍。

* `radare2`：成套的逆向工具
  * 包含多个命令行的工具，前面提到的[rabin2](https://book.crifan.org/books/ios_re_static_analysis/website/analysis_content/bin_info/mach_o/rabin2.html)就是其中之一
* `Cutter`：radare2的GUI版本
* Miasm
  * 一句话介绍：用Python实现的逆向工程框架
    * Reverse engineering framework in Python
  * 用途：分析、修改、生成 二进制程序
    * analyze / modify / generate binary programs
  * 特性
    * Opening / modifying / generating PE / ELF 32 / 64 LE / BE
    * Assembling / Disassembling X86 / ARM / MIPS / SH4 / MSP430
    * Representing assembly semantic using intermediate language
    * Emulating using JIT (dynamic code analysis, unpacking, ...)
    * Expression simplification for automatic de-obfuscation
  * 资料
    * GitHub
      * cea-sec/miasm: Reverse engineering framework in Python
        * https://github.com/cea-sec/miasm
    * 官网
      * Home — Miasm's blog
        * https://miasm.re/blog/
