# 4. 固件烧录

> [!TIP]
> SHTV2预装了CanBoot，只支持CAN烧录，烧录前请使用CAN连接到上位机

## 4.1 编译固件

> [!TIP]
> **2023年9月20号之前**CanBoot固件默认500k

>[!TIP]
>**2023年9月20号之后**CanBoot固件默认1M

请先阅读[连接到SSH](/introduction/conntossh "点击即可跳转")文档

这里只简要介绍固件编译参数，详细固件编译步骤请查看：[编译klipper固件](/board/fly_super8/firmware?id=_1-编译klipper固件 "点击即可跳转")。 看到第 **13** 步即可！！！

**固件配置方法**

1. 修改klipper编译配置

    ```bash
    cd && cd ~/klipper && rm -rf .config && make menuconfig
    ```

> [!TIP]
> 注意，在2022-10-18 **前** 购买的主控芯片为GD32F103；在2022-10-18 **后** 购买的主控芯片为APM32F072；在2023-05-01 **后** 购买的主控为STM32F072



> [!TIP]
>
> 注意，在2023-09-20 **前** 购买的SHT36-V2使用的canboot速率为500K；在2023-09-20 **后** 购买的SHT36-V2使用的canboot速率为1M



<!-- tabs:start -->

#### ****GD32F103****

![config](../../images/boards/fly_sht_v2/config.png ":no-zooom")

#### ****APM32F072 & STM32F072****

![config](../../images/boards/fly_sht_v2/config_072.png ":no-zooom")

<!-- tabs:end -->

3. 编译

    ```bash
    make clean && make -j4
    ```
    
     最后出现**Creating hex file out/klipper.bin**则编译成功

## 4.2 查找uuid

> [!TIP]
> 请使用UTOC或者其他支持klipper USB桥接CAN的主板将SHTV2与上位机通过CAN总线连接

> [!TIP]
> 如果已经烧录过klipper并且在正常运行，可跳过查找uuid，使用配置文件中的uuid进行烧录

> 由于SHTV2预装了katapult，只支持CAN烧录，因此在固件烧录前需要读取uuid后才能烧录固件

首先进入ssh，然后依次输入以下指令

```
cd && git clone https://github.com/Arksine/katapult
```

![1](../../images/boards/fly_sht_v2/1.png)

```bash
cd && cd ~/klipper && python3 ~/klipper/lib/canboot/flash_can.py -q
```

请注意，搜索到id后是显示``Application: Canboot``前面才是工具板id

<img src="../../images/boards/fly_sht_v2/uuid.png" alt="uuid" style="zoom:80%;" />

下图中高亮部分``365f54003b9d``就是这块SHTv2板的uuid，这个uuid每块板子都不一样。同一块SHTv2板烧录固件后uuid是不会变的



> [!TIP]
> 如果找不到CAN ID，请检查：

* 接线是否正确，例如CANH 和 CANL是否接反或者接触不良
* SHT36 V2板上的120Ω跳线帽是否插上
* 您的镜像内核是否支持CAN

如果确认没有上述问题，则可以尝试在**通电状态**下强制进入CanBoot来解决。此方法也可以在刷错固件连不上工具板之后尝试。进入CanBoot的方法如下，请小心使用！！！以免损坏SHT工具板！！！

<img src="../../images/boards/fly_sht_v2/canboot.png" alt="canboot" style="zoom:80%;" />

如果成功进入Canboot，下图中的LED灯会以一定的频率闪烁

![config](../../images/boards/fly_sht_v2/statusled.png ":no-zooom")

## 4.3 烧录固件

将下面命令中的``365f54003b9d``替换为[查找uuid](#_2-查找uuid "点击即可跳转")中查找到的uuid

```bash
python3 ~/klipper/lib/canboot/flash_can.py -u 365f54003b9d
```

如下图，出现``CAN Flash Success``则烧录成功

如果需要更新固件可以在klipper连接起来下直接执行下方命令来更新sht36固件

```bash
python3 ~/klipper/lib/canboot/flash_can.py -u 365f54003b9d
```

![config](../../images/boards/fly_sht_v2/flash.png ":no-zooom")

* 如果需要更新固件只需要编译好固件后重新执行烧录指令就可以更新固件
* 请保证能找到ID或者KIPPER已经连接上

```
python3 ~/klipper/lib/canboot/flash_can.py -u  <MCU ID>
```

检查

如果正确配置编译并烧录成功，则SHTv2板的这个灯会常亮

![config](../../images/boards/fly_sht_v2/statusled.png ":no-zooom")