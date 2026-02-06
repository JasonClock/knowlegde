# 配置clion开发stm32
1. 配置openOCD（在嵌入式开发的设置中）
2. debug改为其中的debug - debug
3. ArmGcc 给其设置好环境变量（所以环境变量是啥？）
4. 配置调试器
5. 第六步：配置调试（就像准备试吃）
````
1 创建调试配置
点击CLion右上角的 Edit Configurations（下拉菜单）

点击左上角的 + 号

选择 Embedded GDB Server

填写配置：

text
Name: STM32 Debug                 # 配置名称

Target:                           # 目标文件
${PROJECT_BINARY_DIR}/STM32_Project.elf

GDB:                              # 调试器
${TOOLCHAIN_BIN}/arm-none-eabi-gdb.exe

'target remote' args:             # 远程连接参数
localhost:3333

GDB Server:                       # OpenOCD路径
E:/OpenOCD/bin/openocd.exe

GDB Server args:                  # OpenOCD参数
-f interface/stlink-v2.cfg -f target/stm32f1x.cfg
6.2 根据开发板修改配置
开发板类型	interface文件	target文件
ST-Link V2	stlink-v2.cfg	根据芯片选择
ST-Link V2-1	stlink-v2-1.cfg	根据芯片选择
CMSIS-DAP	cmsis-dap.cfg	根据芯片选择
常见芯片配置：

STM32F1系列：stm32f1x.cfg

STM32F4系列：stm32f4x.cfg

STM32F7系列：stm32f7x.cfg
````