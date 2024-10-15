# ldid

* `ldid`/`ldid2`
  * 用法概述
    * 查看/导出二进制的entitlement权限
      ```bash
      ldid -e <binary>
      ```
      * 举例
        ```bash
        ldid -e debugserver
        ldid -e amsaccountsd
        ldid -e Preferences.app/Preferences > Preferences_entitlement.plist
        ```
    * 设置二进制的entitlement权限
      ```bash
      ldid -Sent.xml <binary>
      ```
      * 注：`-S`和文件名`ent.xml`中间**没有空格**！
      * 举例
        * 使用对应的entitlement文件给`debugserver`重新签名
          ```bash
          ldid -S/Users/your/Desktop/Entitlements.xml ./debugserver
          ```
  * 详见子教程
    * [ldid · iOS逆向开发：签名和权限](https://book.crifan.org/books/ios_re_codesign_ent/website/common_tools/ldid/)
