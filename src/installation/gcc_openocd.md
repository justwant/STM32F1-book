# GCC + OpenOCD

> **Alert**  
> 
> 本部分内容对于不熟悉相关工具的同学而言可能比较困难  
> 对于零基础的同学推荐配置 Keil MDK 环境
>
> 本部分内容较为简略，请学会合理利用搜索引擎以及向开源社区寻求帮助

本部分完成和 GCC-ARM 和 OpenOCD 环境的配置，所需要的工具均为开源软件。本文讲述如何在 Windows 平台下配置相关环境，但 Linux 也可以使用，且一般而言在 Linux 下配置环境会更为容易一些

对于大多数 Linux 发行版，可以通过包管理器直接安装 `arm-none-eabi-gcc` 和 `OpenOCD`

对于 windows 系统，可以在以下网址下载 [arm-none-eabi-gcc](https://developer.arm.com/open-source/gnu-toolchain/gnu-rm/downloads)
和 [OpenOCD](gnutoolchains.com/arm-eabi/openocd/)。
安装后，将两者的 `bin` 文件夹加入 Path 环境变量中。

安装完成后，使用以下命令检查安装是否成功，如果成功会输出相应的版本信息。如果提示找不到文件，请检查安装与环境变量配置是否正确。

```
arm-none-eabi-gcc -v
openocd -v
```

# OpenOCD 测试

首先安装 stlink 的驱动，可参考本教程的 [ST-LINK 安装](./stlink.md) 部分。成功后执行以下操作检测 OpenOCD 能否正常使用

在 OpenOCD 安装目录下打开命令行窗口，执行以下命令
```
openocd -f interface\stlink-v2.cfg -f board\stm3210c_eval.cfg
```
如果窗口陷入阻塞状态，且无错误信息产生，则说明可以正常使用。

# 生成 Makefile 文件

> **Alert**  
> 
> 如果您不太了解 Makefile 是什么，可以使用搜索引擎了解相关内容  

STM32CubeMX 本身支持生成 Makefile 文件，只需在导出工程文件时将 `Toolchain \ IDE` 改为 `Makefile` 即可生成一份 Makefile 文件。

# 使用 GDB 进行调试

假设生成的目标文件为 `Blink.elf`

启动 OpenOCD 后，可以另打开命令行窗口，使用
```
arm-none-eabi-gdb blink.elf
```
命令启动 GDB 后，再在 GDB 命令行内执行以下命令
```
target remote localhost:3333
load
monitor reset
```
之后可以正常使用 GDB 命令进行调试

## 远程调试

不要求 GDB 和 OpenOCD 必须在同一台电脑上运行。GDB 与 OpenOCD 间的通信使用 socket 完成，只需要配置好网络环境，将 localhost 改换为对应的 ip 地址，即可实现远程调试。

> **Alert**  
>
> 远程调试需要开放对应端口，务必注意网络安全
