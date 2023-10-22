# ldid

* ldid
  * 是什么：用于修改二进制的entitlement权限的工具
  * 作者：`saurik`
  * 其他作用
    * 对于二进制签名，生成SHA1和SHA256的hash值，以便于iPhone能够正常执行二进制
  * Cydia中叫做：`Link Identity Editor`
  * ldid用法
    * 查看/导出二进制的entitlement权限
      ```bash
      ldid -e <binary>
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
    * 伪签名二进制，无entitlement权限
      ```bash
      ldid -S <binary>
      ```
  * 源码
    * 官网
      * [git.saurik.com Git - ldid.git/summary](https://git.saurik.com/ldid.git)
    * GitHub 的copy
      * [xerub/ldid: Unofficial fork from saurik git repository git://git.saurik.com/ldid.git (github.com)](https://github.com/xerub/ldid)
  * 其他资料
    * [ldid - iPhone Development Wiki](https://iphonedev.wiki/index.php/Ldid)

## 不同版本

* **brew**（安装的Cellar）版本：
  * 位置：`/usr/local/bin/ldid`
    * 其是软链接
      * 实际位置是：`/usr/local/Cellar/ldid/2.1.5/bin/ldid`
  * 大小：`814K`
  * 文件格式：`Mach-O 64-bit executable x86_64`
* **iOSOpenDev**版本
  * 位置：`/opt/iOSOpenDev/bin/ldid`
  * 大小：`383K`
  * 文件格式：
    * `(for architecture i386):    Mach-O executable i386`
    * `(for architecture x86_64):    Mach-O 64-bit executable x86_64`

-> 结论：

* 优先用**brew版本**的`ldid`
  * 尽量不要用iOSOpenDev的ldid
