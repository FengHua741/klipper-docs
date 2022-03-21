# 引脚分布

## Gemini-v1.1引脚

### 步进电机驱动部分

<!-- tabs:start -->

#### **X驱动**

* X电机

| 驱动 | 功能 | 引脚号 |
| :----: | :----: | :----- |
| X | EN | ***PB2*** |
| X | STEP | ***PC13*** |
| X | DIR | ***PC1*** |
| X | UART | ***PB11*** |

#### **Y驱动**

* Y电机

| 驱动 | 功能 | 引脚号 |
| :----: | :----: | :----- |
| Y | EN | ***PD2*** |
| Y | STEP | ***PC14*** |
| Y | DIR | ***PC4*** |
| Y | UART | ***PB9*** |

#### **Z驱动**

* Z电机

| 驱动 | 功能 | 引脚号 |
| :----: | :----: | :----- |
| Z | EN | ***PC12*** |
| Z | STEP | ***PC15*** |
| Z | DIR | ***PC5*** |
| Z | UART | ***PB8*** |

#### **E驱动**

* E电机

| 驱动 | 功能 | 引脚号 |
| :----: | :----: | :----- |
| E | EN | ***PC11*** |
| E | STEP | ***PC3*** |
| E | DIR | ***PC8*** |
| E | UART | ***PB7*** |

#### **驱动SPI**

* 驱动SPI

| 驱动 | 功能 | 引脚号 |
| :----: | :----: | :----- |
| X,Y,Z,E | MOSI | ***PB5*** |
| X,Y,Z,E | MISO | ***PB4*** |
| X,Y,Z,E | CLK | ***PB3*** |
| X,Y,Z,E | CS | **UART** |

<!-- tabs:end -->


### 限位

| 限位 | 引脚号 |
| :----: | :----- |
| X | ***PA3*** |
| Y | ***PB1*** |
| Z | ***PB10*** |

### 加热控制

| 功能 | 引脚号 |
| :----: | :----- |
| 挤出加热 | ***PA0*** |
| 热床加热 | ***PA2*** |

### 温度传感器

| 功能 | 引脚号 |
| :----: | :----- |
| 挤出温度 | ***PC0*** |
| 热床温度 | ***PC2*** |

### 舵机与探针

| 功能 | 引脚号 |
| :----: | :----- |
| 舵机 | ***PB0*** |
| 探针 | ***PA1*** |

### EXP接口

<!-- tabs:start -->

#### **EXP1**

| 功能 | 引脚号 |
| :----: | :----- |
| EXP1_1 | ***PC9*** |
| EXP1_2 | ***PB6*** |
| EXP1_3 | ***PA13*** |
| EXP1_4 | ***PA10*** |
| EXP1_5 | ***PA9*** |
| EXP1_6 | ***PA8*** |
| EXP1_7 | ***NC*** |
| EXP1_8 | ***NC*** |
| EXP1_9 | ***GND*** |
| EXP1_10 | ***5V*** |

#### **EXP2**

| 功能 | 引脚号 |
| :----: | :----- |
| EXP2_1 | ***PB14*** |
| EXP2_2 | ***PB13*** |
| EXP2_3 | ***PA15*** |
| EXP2_4 | ***PB12*** |
| EXP2_5 | ***PA14*** |
| EXP2_6 | ***PB15*** |
| EXP2_7 | ***PC10*** |
| EXP2_8 | ***RST*** |
| EXP2_9 | ***GND*** |
| EXP2_10 | ***NC*** |

<!-- tabs:end -->