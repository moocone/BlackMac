本来想下载XCode的，发现系统版本低无法安装：

![macOS High Sierra](https://github.com/zzylovecode/BlackMac/blob/master/img/macOS%20High%20Sierra.png)



然后看到如下的教程

> 直接升级安装

 App Store 下载 macOS High Sierra 安装包 直接在已有系统内升级安装。这样更省心一些，只要更新一下已有系统的  Clover、FakeSMC 到最新版本，并且在 EFI 分区中添加上 APFS 的驱动，然后登录 App Store，下载 macOS  High Sierra 一步步安装就可以了。

 用到的工具如下所示（点击链接即可下载对应项目）：

Clover r4220：下载之后双击安装到原来的 EFI  所在磁盘分区即可。FakeSMC-v6.21：下载之后解压缩，将解压缩出来的文件替换原来 EFI 分区中的 FakeSMC.kext  文件。APFS.efi 驱动：下载之后放进 /EFI/CLOVER/drivers64UEFI/。



做好一切工作后开始升级10.13.6

![macOS High Sierra_03](https://github.com/zzylovecode/BlackMac/blob/master/img/macOS%20High%20Sierra_01.png)

![macOS High Sierra_02](https://github.com/zzylovecode/BlackMac/blob/master/img/macOS%20High%20Sierra_02.png)



![macOS High Sierra_03](https://github.com/zzylovecode/BlackMac/blob/master/img/macOS%20High%20Sierra_03.png)

然后就报错了，后来在某论坛上看到有人回复：“是更新版本跨度太大造成的”

于是先安装10.13 重复上述操作

### 成功

![macOS High Sierra_02](https://github.com/zzylovecode/BlackMac/blob/master/img/black%20apple%20boot.jpeg) 

![屏幕快照 2018-10-10 下午3.41.56](https://github.com/zzylovecode/BlackMac/blob/master/img/%E5%B1%8F%E5%B9%95%E5%BF%AB%E7%85%A7%202018-10-10%20%E4%B8%8B%E5%8D%883.41.56.png)

然后安装事先准备好的显卡驱动，以下的链接为教程网站

PS:这里有一点我的硬盘是HFS+然后是HDD 转换为APFS比较亏，这里使用代码进行安装，将自动转换APFS关闭

https://www.tonymacx86.com/threads/update-directly-to-macos-high-sierra.232707/

https://www.tonymacx86.com/threads/nvidia-releases-alternate-graphics-drivers-for-macos-high-sierra-10-13-0-378-10-10-10-15.225522/

---

后来又马上更新了10.13.6

结果出了问题，黑苹果进度条跑2/3不动了

**卡在 IOConsoleUsers: gIOScreenLockState 3, hs 0, bs 0 now**

后来折腾了半天，取消勾选nvda_drv=1，并勾选nv_disable=1

成功！

# Summary

台式机无痛升级 四点

在 EFI 分区上 ，更新以下

1. Clover
2. FakeSMC 
3. APFS 的驱动
4. 显卡驱动

到最新版本

boot的时候先关闭独立显卡
