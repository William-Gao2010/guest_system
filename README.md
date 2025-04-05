# 迎宾系统程序

## 项目简介
这是一个基于STC8G系列单片机的迎宾系统程序，主要用于通过雷达传感器检测人员接近，并根据检测到的速度信息触发不同的语音提示。系统通过串口接收雷达数据，解析特定格式的数据包，并根据解析结果控制语音模块发出相应的语音指令。

## 程序功能
1. **串口通信初始化**：
   - 初始化串口1，设置波特率为9600 bps，用于接收雷达数据和发送语音指令。
   - 使用定时器1作为波特率发生器。
2. **数据接收与解析**：
   - 通过中断接收雷达模块发送的数据，并存储到缓冲区中。
   - 检测特定格式的数据包（以`0xAA, 0xFF, 0x03, 0x00`开头，以`0x55, 0xCC`结尾），并提取其中的速度信息。
3. **语音提示控制**：
   - 根据解析到的速度信息，触发不同的语音提示：
     - 当速度小于128时，触发语音指令`0x01`。
     - 当速度大于等于128时，触发语音指令`0x03`。
     - 当速度为负值时，触发语音指令`0x02`。
4. **延时功能**：
   - 提供精确的延时功能，用于控制语音指令的发送间隔。

## 硬件需求
- STC8G系列单片机开发板
- 雷达模块（通过串口与单片机连接）
- 语音模块（通过串口与单片机连接）
- 串口转USB模块（用于调试和数据转发）
- 连接线
- 电源（5V）

## 硬件连接
1. 将雷达模块的串口TX（发送）引脚连接到单片机的P3.1（串口1接收引脚）。
2. 将语音模块的串口RX（接收）引脚连接到单片机的P3.0（串口1发送引脚）。
3. 将串口转USB模块的TX和RX引脚分别连接到单片机的P3.0和P3.1。
4. 确保所有设备的电源和地线连接正确。

## 使用方法
1. **编译程序**：
   - 使用STC-ISP软件将程序编译并烧录到单片机中。
2. **运行程序**：
   - 接通电源后，雷达模块开始发送数据。
   - 单片机通过串口接收雷达数据，解析速度信息，并根据解析结果触发语音提示。
3. **调试与验证**：
   - 使用串口调试助手（如PuTTY、串口助手等）连接到串口转USB模块，观察雷达模块发送的数据和语音模块接收的指令。
   - 调整雷达模块的检测距离和灵敏度，确保系统能够准确检测人员接近并触发语音提示。

Emai:17156310913ghj@gmail.com
