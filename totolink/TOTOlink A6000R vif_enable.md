# TOTOlink A6000R V1.0.1-B20201211.2000 Command Injection
## Product Information

Device: TOTOlink A6000R
Firmware Version: V1.0.1-B20201211.2000
Manufacturer's website information：https://www.totolink.net/
Firmware download address ：https://www.totolink.net/home/menu/detail/menu_listtpl/download/id/202/ids/36.html

![](img\1.png)

## Vulnerability Description

When deal with  `vif_enable` request,`iface` parameter is vulnerable to OS command injection.

vuln code in firmware: /usr/lib/lua/luci/controller/mtkwifi.lua, line 507-514

![](img/2.png)



entry: /admin/mtk/wifi/vif_enable/arg

![](img/3.png)

