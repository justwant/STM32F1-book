# STM32CubeMX

本节介绍 STM32CubeMX 的安装。STM32CubeMX 是生成STM32初始化代码的工具，能以图形界面的方式配置STM32所需资源，简化初始化代码的编写。其能够导出适用于多种开发环境的工程文件。

STM32CubeMX可以在Windows、Linux 以及 Mac OS 上运行，但本文只针对 Windows 上的安装与使用进行配置。

# 安装方法

所需文件：
- `en.stm32cubemx.zip`
- `en.stm32cubef1.zip`

将 `en.stm32cubemx.zip` 解包，找到其中 `SetupSTM32CubeMX-4.24.0.exe` 安装即可。

安装完成后，如果启动 Cube 时报错找不到 JRE，则自行下载安装 JRE 即可。

将 `en.stm32cubef1.zip` 解包到任意位置，之后使用 Cube 导出工程时需要其中的内容。（该步骤可忽略，如果导出工程是cube找不到相应的文件，会自动提示下载，但仍推荐提前将该文件下载并解包）

# 生成第一个工程文件

Cube 的具体使用方法会在后面介绍，这里只简要介绍如何生成工程文件。

使用 Cude 打开我们提供的 `blink.ioc` 文件，这也是第一个样例 点亮LED 的 Cube 配置文件。

单击菜单栏 `Project -> Settings ...` 进入工程配置选项，设置好工程名和工程位置，`Toolchain / IDE` 选择为 `MDK-ARM v5`

最下方取消 `Use default Fireware Location` 填入 `en.stm32cubef1.zip` 的解包地址。

以上配置完成，使用 `Project -> Generate Code` 即可成功生成工程文件。