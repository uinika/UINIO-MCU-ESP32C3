# UINIO-MCU-ESP32C3 核心板

[**UINIO-MCU-ESP32C3**](https://github.com/uinika/UINIO-MCU-ESP32C3) 是一款基于 [**上海乐鑫科技**](https://www.espressif.com.cn) **ESP32-C3** 微控制器的核心板电路设计，该微控制器基于开源的 **RISC-V** 指令集，主频高达 `160MHz`，并且同时具备 **2.4GHz Wi-Fi** 与 **Bluetooth5** 两种物联网接入能力。

![](./Images/PCB-3D-1.png)

![](./Images/PCB-3D-2.png)

## 核心板简介

- 完整兼容官方的 [Arduino-ESP32](https://docs.espressif.com/projects/arduino-esp32/en/latest/) 板级支持包；
- 采用 LDO 低压差线性稳压芯片 `ME6211C33M5G` 提供 `3.3V` 电源；
- 预留 **TQFN** 封装的 USB 转 UART 串口芯片 **CH343P** 位置，可以按需进行贴装，不贴装时可以采用右上角的 4 线杜邦针外接串口下载模块；
- 预留有 2.4G 微带天线 **π 型阻抗匹配电路**位置，如果对于信号的收发功率没有严格要求，则可以将位号为 `L1` 的串联电感替换为 `0R` 电阻；
- 预留有 4 个 `1mm` 沉头螺丝开孔，可以用于固定核心板；

## 使用注意事项

1. 上电之前不能下拉 `IO9/BOOT` 的电平状态，否则 **ESP32-C3** 将会进入**下载模式**；
2. `IO8` 引脚默认进行了上拉，因为如果其为低电平状态，则不能使用串口进行固件下载；
3. `GPIO11` 默认为 SPI 接口 Flash 存储器的 `VDD` 引脚，需要配置之后才能作为 GPIO 使用；
4. 外置的 `W25Q128JVSSIQ` 型 Flash 存储器，其 `VDD` 已经连接至 `3.3V` 电源，使用时无需再行配置，Flash 采用普通的两线制 SPI 总线进行通信；
5. `IO12`、`IO13` 在 **QIO** 模式下被复用为 SPI 信号线 `SPIHD` 和 `SPIWP`，本开发板采用两线制 SPI 的 **DIO** 模式，使用时需要注意将 Flash 配置为 **DIO** 模式；
