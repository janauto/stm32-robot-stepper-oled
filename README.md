# STM32 Robot Stepper OLED 资料与工程集

`stm32-robot-stepper-oled` 是一个 STM32 嵌入式学习与项目资料仓库，集中保存了步进电机控制、0.96 寸 OLED 显示屏示例资料，以及机械臂/机器人底盘控制工程。仓库内容主要面向 STM32F1 系列开发板、Keil MDK-ARM 工程、HAL 库工程和基础机器人运动控制实验。

当前仓库不是一个单一应用，而是多个嵌入式工程和资料包的集合。使用时建议先根据目标场景进入对应目录，再打开对应的 Keil 工程文件。

## 仓库内容概览

```text
.
├── stpeper/
│   ├── stepper/
│   │   ├── Core/
│   │   ├── Drivers/
│   │   ├── MDK-ARM/
│   │   ├── Solf/
│   │   └── bsp/
│   ├── stepper.rar
│   └── 0.96寸OLED显示屏/
│       ├── 01-程序源码/
│       ├── 02-参考文档/
│       ├── 03-取模软件/
│       ├── 04-编码转换软件/
│       ├── 05-商家资料/
│       └── 课件及课程相关资料/
└── 机械臂底盘代码/
    └── Robot/
        ├── Core/
        ├── Drivers/
        ├── Hardware/
        ├── MDK-ARM/
        ├── Middlewares/
        └── TASK/
```

## 适用场景

- STM32F103 系列入门和工程模板学习。
- 步进电机驱动、启停、方向控制和 PWM 输出实验。
- 0.96 寸 SSD1306 OLED 显示屏 I2C/SPI 示例验证。
- OLED 取模、图片显示、菜单显示和编码转换学习。
- PS2 手柄读取与机器人底盘遥控实验。
- 四电机底盘运动解算、PWM 占空比输出和 FreeRTOS 任务调度实验。
- 机械臂底盘或移动机器人底盘控制代码留档。

## 主要模块说明

### 1. `stpeper/stepper`

这是步进电机控制工程，包含 STM32 HAL 工程结构和 Keil MDK-ARM 工程文件。

关键目录：

| 路径 | 说明 |
| --- | --- |
| `stpeper/stepper/Core/` | STM32CubeMX/HAL 生成的主工程代码 |
| `stpeper/stepper/Drivers/` | CMSIS 与 STM32F1 HAL 驱动 |
| `stpeper/stepper/MDK-ARM/stepper.uvprojx` | Keil 工程入口 |
| `stpeper/stepper/Solf/` | 菜单、业务逻辑等用户代码 |
| `stpeper/stepper/bsp/` | 板级支持代码 |

从 `Core/Src/main.c` 可以看到，该工程包含：

- TIM3 PWM 初始化。
- DWT 时间轴初始化。
- OLED 初始化。
- 步进电机初始化。
- 电机使能/失能控制。
- 电机方向切换。
- 平滑启动或速度过渡逻辑。
- OLED 菜单或壁纸显示。

推荐入口：

```text
stpeper/stepper/MDK-ARM/stepper.uvprojx
```

### 2. `stpeper/0.96寸OLED显示屏`

这是 0.96 寸 OLED 显示屏资料集合，包含程序源码、参考文档、取模软件、编码转换软件和商家资料。

主要内容：

| 路径 | 说明 |
| --- | --- |
| `01-程序源码/` | OLED 示例工程源码，包含 I2C 和 SPI 示例 |
| `02-参考文档/` | OLED 产品规格书、原理图、SSD1306 数据手册 |
| `03-取模软件/` | PCtoLCD2002 取模工具 |
| `04-编码转换软件/` | UltraCodingSwitch 编码转换工具 |
| `05-商家资料/` | 商家提供的数据手册、结构图、示例程序和使用文档 |
| `课件及课程相关资料/` | 教学课件、示例和模板 |

常见工程入口：

```text
stpeper/0.96寸OLED显示屏/01-程序源码/OLED-V1.0/01-OLED功能函数测试-4针脚I2C接口/Project.uvprojx
stpeper/0.96寸OLED显示屏/01-程序源码/OLED-V1.0/02-OLED功能函数测试-7针脚SPI接口/Project.uvprojx
stpeper/0.96寸OLED显示屏/01-程序源码/OLED-V1.1/01-OLED功能函数测试-4针脚I2C接口/Project.uvprojx
```

资料包中还包含压缩文件。`0.96寸OLED显示屏` 目录下有一个提示文件：

```text
解压密码：oled
```

### 3. `机械臂底盘代码/Robot`

这是机械臂/机器人底盘控制工程，包含 FreeRTOS、PS2 手柄读取、四电机底盘运动控制和 Keil 工程文件。

关键目录：

| 路径 | 说明 |
| --- | --- |
| `机械臂底盘代码/Robot/Core/` | STM32 HAL 主工程代码 |
| `机械臂底盘代码/Robot/Drivers/` | CMSIS 与 STM32F1 HAL 驱动 |
| `机械臂底盘代码/Robot/Middlewares/` | FreeRTOS 等中间件 |
| `机械臂底盘代码/Robot/Hardware/` | 电机控制、PS2 手柄底层驱动 |
| `机械臂底盘代码/Robot/TASK/` | FreeRTOS 任务层代码 |
| `机械臂底盘代码/Robot/MDK-ARM/Robot.uvprojx` | Keil 工程入口 |

推荐入口：

```text
机械臂底盘代码/Robot/MDK-ARM/Robot.uvprojx
```

核心源码：

| 文件 | 说明 |
| --- | --- |
| `Hardware/moto_control.c` | 四电机 PWM 输出与底盘运动解算 |
| `Hardware/moto_control.h` | 电机结构体、方向宏和底盘参数定义 |
| `Hardware/ps2.c` | PS2 手柄通讯、按键读取、震动控制 |
| `Hardware/ps2.h` | PS2 引脚和按键定义 |
| `TASK/Chassis_TASK.c` | 底盘周期控制任务 |
| `TASK/REMOTE_TASK.c` | 遥控输入相关任务 |

底盘任务主要流程：

```text
Chassis_Task
  -> MC_Solving()
  -> MOTO_RUN()
  -> osDelay(1)
```

其中 `MC_Solving()` 根据 `moto_x`、`moto_y`、`moto_yaw` 计算 4 个电机速度和方向；`MOTO_RUN()` 将计算结果转成 TIM3 各通道 PWM 比较值并输出到电机驱动。

## 开发环境

建议环境：

- Windows 10/11
- Keil MDK-ARM 5
- STM32CubeMX，可用于重新生成或检查 HAL 配置
- ST-Link 或兼容调试器
- STM32F1 系列开发板，工程中主要出现 STM32F103 相关配置
- USB 转串口工具，可用于调试输出

可选工具：

- PCtoLCD2002：OLED 字模/图片取模。
- UltraCodingSwitch：编码转换。
- 7-Zip、WinRAR 或其他压缩包工具。

## 如何打开工程

### 打开步进电机工程

1. 安装 Keil MDK-ARM 5。
2. 安装 STM32F1 相关 device pack。
3. 打开：

```text
stpeper/stepper/MDK-ARM/stepper.uvprojx
```

4. 选择正确芯片和下载器。
5. 编译工程。
6. 连接开发板并下载。

### 打开机械臂底盘工程

1. 安装 Keil MDK-ARM 5 和 STM32F1 device pack。
2. 打开：

```text
机械臂底盘代码/Robot/MDK-ARM/Robot.uvprojx
```

3. 检查 `main.h` 中的 GPIO 定义是否和实际硬件一致。
4. 检查 TIM、PWM、FreeRTOS 配置。
5. 编译并下载。
6. 上电测试前建议悬空底盘或断开电机负载，先确认方向和占空比。

### 打开 OLED 示例工程

根据你的屏幕接口选择工程：

- 4 针 I2C 屏幕：打开 I2C 接口工程。
- 7 针 SPI 屏幕：打开 SPI 接口工程。

示例：

```text
stpeper/0.96寸OLED显示屏/01-程序源码/OLED-V1.0/01-OLED功能函数测试-4针脚I2C接口/Project.uvprojx
```

## 硬件连接提示

### OLED

常见 4 针 I2C OLED：

| 引脚 | 说明 |
| --- | --- |
| VCC | 3.3V 或 5V，按模块规格接线 |
| GND | 地 |
| SCL | I2C 时钟 |
| SDA | I2C 数据 |

常见 7 针 SPI OLED：

| 引脚 | 说明 |
| --- | --- |
| VCC | 电源 |
| GND | 地 |
| D0/SCL | SPI 时钟 |
| D1/SDA | SPI 数据 |
| RES | 复位 |
| DC | 数据/命令选择 |
| CS | 片选 |

实际接线以工程 `main.h`、商家原理图和模块丝印为准。

### PS2 手柄

`ps2.c` 注释中给出的默认连接关系：

| 信号 | 默认引脚 |
| --- | --- |
| DAT | PA0 |
| CMD | PA1 |
| CS | PA4 |
| CLK | PA5 |

如果硬件接线不同，需要同步修改 `ps2.h` 或 CubeMX GPIO 配置。

### 底盘电机

底盘控制使用 TIM3 多通道 PWM。测试时建议：

- 先不接电机，只用示波器或逻辑分析仪查看 PWM。
- 再低电压、低占空比测试单个电机。
- 确认每个电机方向宏与真实安装方向一致。
- 最后再进行整车运动测试。

## 调试建议

- 编译报 device pack 缺失：安装 STM32F1xx Keil pack。
- 编译报 include 找不到：检查 Keil 工程 include path 是否保持原目录结构。
- OLED 不显示：检查供电、电平、I2C/SPI 接线、屏幕地址和初始化函数。
- 电机不转：检查驱动供电、使能脚、PWM 脚、方向脚和定时器通道。
- 电机方向反：调整方向宏或电机接线。
- PS2 无响应：检查 DAT/CMD/CS/CLK 引脚、手柄供电、时序延时和模式配置。
- 下载失败：检查 ST-Link 驱动、BOOT0 状态、SWD 接线和芯片型号。

## 仓库维护建议

这个仓库包含源码、文档、压缩包、PDF 和 Windows 工具，体积较大。后续维护建议：

- 新增工程时单独建目录，并在 README 中补入口路径。
- 保留 Keil 工程文件 `.uvprojx`，避免只上传源码导致无法直接打开。
- 编译产物、临时文件和个人调试配置不建议继续提交。
- 商家资料和第三方工具如需公开分发，应确认授权边界。
- 如果仓库继续增长，建议把大压缩包迁移到 Release 或 Git LFS。

## 已知限制

- 部分源码注释存在编码不一致，直接在 UTF-8 环境查看可能出现乱码。
- 仓库含有商家资料、工具软件和压缩包，许可证状态需要按来源单独确认。
- 当前没有统一的一键构建脚本，不同工程需要分别用 Keil 打开。
- 工程面向特定硬件接线，直接下载到其他板子前必须检查 GPIO、TIM 和外设配置。

## License

当前仓库没有统一开源许可证。公开使用、二次分发或商用前，请先确认其中商家资料、第三方工具、ST HAL/CMSIS 代码和个人源码各自的授权要求。
