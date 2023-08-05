

#  3. FLY_Config 的使用

* FLY-Config用来简化系统配置等，适用于Klipper全家桶，免去进入ssh写命令的麻烦
* 只能在FLY定制Armbian系统运行
* 对初学者友好
* 直接配置Klipper及周边

## 3.1 打开 FLY_Config

1. 如果您已经制作好SD卡，请使用读卡器连接到电脑。此时电脑应该会弹出资源管理器并且有一个“**可移动磁盘BOOT**” .如果未出现，请重新拔下 sd 卡，再插入电脑

   eMMc进入BOOT盘方法，请参考：[通过usb为emmc烧录系统镜像](/board/fly_pi/FLY_π_description1?id=_2-通过usb为emmc烧录系统镜像)

   ![open_boot](../../images/boards/fly_pi/open_boot.png)

   

2. 打开BOOT盘下的FLY-Config.conf

   ![open_flyconfig](../../images/boards/fly_pi/open_flyconfig.png)

## 3.2 可用配置

* 配置主板型号（仅限Gemini系列，其他系列默认即可）
* 配置WIFI
* 配置Klipperscreen
* 配置屏幕

## 3.3 连接WiFi

   找到WIFI配置，将WIFI处的flase改成true，并将WiFi名称和密码填写上，保存，插回上位机。等待几分钟后，进入路由器后台管理界面查看IP地址。
   ![connect_wifi](../../images/boards/fly_pi/connect_wifi.png)

## 3.4 Klipperscreen的配置

找到下图所示选项，将``klipperscreen=flase``修改为``klipperscreen=true``，则可启用klipperscreen屏幕。

![config1](../../images/boards/fly_pi/config1.png)

另外还需要指定使用的屏幕类型才能够正常使用！！！按下图中的提示修改为对应的配置即可。

![hdmi](../../images/boards/fly_pi/hdmi.png)

## 3.5 屏幕旋转

> [!TIP]
> 请不要随意修改系统的触摸配置

找到下图所示选项，将``FBTFT=FLY-TFT-V1``注释，将``FBTFT=FLY-TFT-V1-h``取消注释，则可旋转屏幕。

![tft](../../images/boards/fly_pi_lite2/FBTFT.png)

！！！按下图中的提示修改为对应的配置即可。

![tft](../../images/boards/fly_pi_lite2/FBTFT1.png)

## 3.6 mainsail切换

在浏览器输入ip+:81即可切换mainsail

例如将``192.168.1.123``修改为``192.168.1.123:81``
