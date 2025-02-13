# 第 2.6 节 普通电脑下载安装哪个镜像，如何刻录镜像？

## 我该下载哪个镜像？

> **警告**
>
> **请不要** 问我在安装中应该选用哪个镜像站这类问题，那是因为你的错误操作导致的。
>
> **不要** 选用带有`bootonly`字样的镜像文件，除非你真的知道自己在干什么。
>
> **也不要** 不看图文教程就全选所有的组件，要按照前文教程进行选择。

使用 **U 盘** 安装应该选用 `img` 结尾的镜像，例如 [FreeBSD-14.1-RELEASE-amd64-memstick.img](https://download.freebsd.org/ftp/releases/amd64/amd64/ISO-IMAGES/14.1/FreeBSD-14.1-RELEASE-amd64-memstick.img)

只有当使用 **光盘/虚拟机** 安装时才应选用 `iso` 结尾的镜像。这是因为 FreeBSD 的 ISO 镜像没做 Hybrid 混合启动，写入 U 盘会产生错误。见 [Bug](https://bugs.freebsd.org/bugzilla/show\_bug.cgi?id=236786)。

> **警告**
>
>**iso 镜像并不适用于物理机（普通电脑），物理机（普通电脑）请使用 img 镜像。** **除非你有光盘，否则不要下 ISO；** **也不要没事找事用 Ventoy，下载个 img 刻录并不费事。** **如果安装中出现任何问题，请回过头来看看这里这句话。**

> **注意**
>
>**FreeBSD 所有安装介质包括不限于虚拟机文件都没有提供图形界面，均需要自行安装。**

> **注意**
>
> 如果要在 VMware 虚拟机使用 UEFI，必须使用 FreeBSD 13.0-RELEASE 及以上，否则启动会花屏。

### FreeBSD 镜像 BT 种子下载地址

<https://fosstorrents.com/distributions/freebsd/>

## 我该如何刻录 FreeBSD 镜像到 U 盘？

刻录工具 Windows 应该选用 **Rufus**，Linux 直接使用 `dd`命令即可。

rufus 下载地址：[https://rufus.ie/zh](https://rufus.ie/zh)

> **警告**
>
> **不建议** 使用 FreeBSD 手册推荐的 win32diskimager，有时会出现校验码错误的情况（实际上文件校验码正常）。**只有在 rufus 无效的情况下才应使用 win32diskimager。** 下载地址 <https://sourceforge.net/projects/win32diskimager/files/Archive/>，点击 `win32diskimager-1.0.0-install.exe` 即可下载。
>
> 不要使用 Ventoy 引导实体机安装，有时会报错找不到安装文件。
>
> 请 **老老实实用 rufus。**




## 存档内容

Q：联想笔记本无电池如何升级 BIOS？

A：如果找不到电池，请解压缩`78cn25ww.exe`文件（BIOS 文件请自行去联想美国官网获取），用记事本打开`platform.ini`，查找：

```sh
[AC_Adapter]
Flag=1
BatteryCheck=1
BatteryBound=30
```

将以上所有数值都修改为`0`：

```sh
[AC_Adapter]
Flag=0
BatteryCheck=0
BatteryBound=0
```

保存后，双击`InsydeFlash.exe`即可。

**如果断电，后果自负**
