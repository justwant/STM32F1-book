# St-Link

硬件：单片机、淘宝版stlink、4根母头杜邦线

软件：`en.stsw-link009.zip`

# 连线方式

使用杜邦线将单片机与stlink上的对应接口相连（stlink上有十根针，只需要连接其中的4根）

连线方式如下

```
GND     --  GND
TCK     --  SWCLK
TMS     --  SWDIO
3.3V    --  3.3V
```

# 安装驱动

将 stlink 插入电脑，在设备管理器中可以看到黄色叹号的 `STM32 Link` 说明，驱动还没有正确安装。

将 `en.stsw-link009.zip` 解包，寻找到 `stlink_winusb_install.bat` 右键管理员运行，按指示安装即可。（如果系统询问是否安装驱动，放行即可）

安装成功后，可以在设备管理中发现黄色叹号已经消失。