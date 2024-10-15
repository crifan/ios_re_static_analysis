# 导出字符串资源

iOS逆向期间，对于iOS的app，即`Mach-O`二进制，的静态分析，往往涉及到：从二进制中导出字符串等信息和其他资源，供后续研究和分析。

常用的导出字符串等资源的工具有：

* `strings`
* `nm`
* `Mach-O`的工具
  * `rabin2`
  * `jtool2`
  * `otool`
* entitlement和codesign的工具
  * `ldid`/`ldid2`
  * `codesign`

下面详细解释如何操作：
