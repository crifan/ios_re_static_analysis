# 导出头文件

iOS逆向的静态分析中，往往涉及到：从二进制文件中，导出ObjC的类的头文件，简称：导出头文件。

* 导出头文件的前提
  * iOS的app的二进制是已经[砸壳](https://book.crifan.org/books/ios_re_crack_shell_ipa/website/)后的 = 解密后的
  * 待确认：iOS的app的代码是ObjC的

## 一些经验和心得

* 关于其中：待确认：iOS的app的代码是ObjC的
  * ObjC由于底层机制（Runtime运行时的原因？），使得导出ObjC的类的头文件，成为可能
    * 而iOS的新的编程语言Swift，从底层机制上说，就无法导出Swift的类的头文件
  * 从而使得=导致：
    * 对于iOS的app的实现是ObjC和Swift混合都有的话，之前旧版本class-dump在导出时会报错，导致无法导出头文件
      * 需要找到新版，支持ObjC和Swift混合代码，才能继续导出（ObjC的类的）头文件
    * 从iOS正向防护角度，增加逆向导出头文件的难度：尽量把iOS的代码从ObjC改为Swift
      * 待确认：即可避免头文件被导出
