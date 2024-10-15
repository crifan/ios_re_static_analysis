# codesign

* `codesign`
  * 用法概述
    * 二进制文件
      ```bash
      codesign -d --entitlements - BinaryFile
      ```
      * 举例
        ```bash
        codesign -d --entitlements - debugserver
        codesign -d --entitlements - amsaccountsd_orig
        ```
    * app
      ```bash
      codesign -d --entitlements - xxx.app
      ```
      * 举例
        ```bash
        codesign -d --entitlements - Preferences.app
        ```
  * 详见子教程
    * [codesign · iOS逆向开发：签名和权限](https://book.crifan.org/books/ios_re_codesign_ent/website/common_tools/codesign/)
