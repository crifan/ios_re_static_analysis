# iOS逆向开发：静态分析

* 最新版本：`v0.9`
* 更新时间：`20221116`

## 简介

介绍iOS逆向开发期间的静态分析。先是静态分析的概览；接着是从ipa中找到要分析的二进制文件；再是静态分析主要涉及的内容，包括用MachOView、jtool2、rabin2等查看Mach-O二进制信息，用strings、nm、otool等导出字符串资源，用class-dump导出ObjC头文件，用IDA、Hopper等分析代码逻辑等等；然后给出一些相关实例；最后再整理一些相关的经验心得。

## 源码+浏览+下载

本书的各种源码、在线浏览地址、多种格式文件下载如下：

### HonKit源码

* [crifan/ios_re_static_analysis: iOS逆向开发：静态分析](https://github.com/crifan/ios_re_static_analysis)

#### 如何使用此HonKit源码去生成发布为电子书

详见：[crifan/honkit_template: demo how to use crifan honkit template and demo](https://github.com/crifan/honkit_template)

### 在线浏览

* [iOS逆向开发：静态分析 book.crifan.org](https://book.crifan.org/books/ios_re_static_analysis/website/)
* [iOS逆向开发：静态分析 crifan.github.io](https://crifan.github.io/ios_re_static_analysis/website/)

### 离线下载阅读

* [iOS逆向开发：静态分析 PDF](https://book.crifan.org/books/ios_re_static_analysis/pdf/ios_re_static_analysis.pdf)
* [iOS逆向开发：静态分析 ePub](https://book.crifan.org/books/ios_re_static_analysis/epub/ios_re_static_analysis.epub)
* [iOS逆向开发：静态分析 Mobi](https://book.crifan.org/books/ios_re_static_analysis/mobi/ios_re_static_analysis.mobi)

## 版权和用途说明

此电子书教程的全部内容，如无特别说明，均为本人原创。其中部分内容参考自网络，均已备注了出处。如发现有侵权，请通过邮箱联系我 `admin 艾特 crifan.com`，我会尽快删除。谢谢合作。

各种技术类教程，仅作为学习和研究使用。请勿用于任何非法用途。如有非法用途，均与本人无关。

## 鸣谢

感谢我的老婆**陈雪**的包容理解和悉心照料，才使得我`crifan`有更多精力去专注技术专研和整理归纳出这些电子书和技术教程，特此鸣谢。

## 其他

### 作者的其他电子书

本人`crifan`还写了其他`150+`本电子书教程，感兴趣可移步至：

[crifan/crifan_ebook_readme: Crifan的电子书的使用说明](https://github.com/crifan/crifan_ebook_readme)

### 关于作者

关于作者更多介绍，详见：

[关于CrifanLi李茂 – 在路上](https://www.crifan.org/about/)
