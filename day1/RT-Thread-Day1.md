## 星火一号环境安装

* RT-Thread 源码

* Env工具

* OpenOCD工具

* VSCode编辑器

*  VSCode Extensions 里下载并安装支持 C/C++ 的调试插件：

![image-20240729172654396](D:\Typora\Typora\images\image-20240729172654396.png)

![image-20240729172712765](D:\Typora\Typora\images\image-20240729172712765.png)

![image-20240729172756597](D:\Typora\Typora\images\image-20240729172756597.png)

![image-20240729172834664](D:\Typora\Typora\images\image-20240729172834664.png)

下载并解压 **env-windows-v2.0.0.7z** 到系统任意目录，双击 env.exe 进入 env 环境，进行首次使用环境初始化。



## **注意事项**

首次使用需要联网安装pip依赖，请等待依赖安装完成，若安装失败：请手动删除 env-windows 目录下的.venv 目录，再次打开 env.exe 进行重新依赖安装即可。

安装后重新启动Env工具，右键settings-->Integration-->register

![image-20240729173054187](D:\Typora\Typora\images\image-20240729173054187.png)

右键显示ConEmu here 就安装成功了

Env使用

* scons --target=vsc 生成VSCode工程，重写c_cpp_properties.json的路径
* scons -j12 编译工程
* scons --dist 打包bsp工程
* code . 打开工程

### **Git**

![image-20240729173143276](D:\Typora\Typora\images\image-20240729173143276.png)

很早之前安装过了，详细请看PDF。

## **vscode下载调试**

创建launch.json

```C
{
    "version": "0.2.0",
    "configurations": [
        {
            "name": "rt-spark-openocd",
            "executable": "${workspaceRoot}/rt-thread.elf",
            "request": "launch",
            "type": "cortex-debug",
            "runToEntryPoint": "main",
            "targetId": "STM32F407ZG",
            "servertype": "openocd",
            "configFiles": [
                "interface/stlink-v2.cfg",
                "target/stm32f4x.cfg"
            ],
            "armToolchainPath": "D:/RTsummer/env-windows-v2.0.0/env-windows/tools/gnu_gcc/arm_gcc/mingw/bin", // ！！！需要修改为自己的GCC 工具链路径 ！！！
            "gdbPath": "D:/RTsummer/env-windows-v2.0.0/env-windows/tools/gnu_gcc/arm_gcc/mingw/bin/arm-none-eabi-gdb.exe" // ！！！需要修改为自己的GDB 路径 ！！！
        }
    ]
}

```

settings.json加上openocd的路径

```c
{
    "files.associations": {
        "*.txt": "dockercompose",
        "board.h": "c",
        "rtthread.h": "c",
        "drv_gpio.h": "c",
        "rtdevice.h": "c",
        "hello.h": "c",
        "rtdbg.h": "c",
        "drv_matrix_led.h": "c"
    },
    "cortex-debug.openocdPath": "D:/RTsummer/openocd-20231002/OpenOCD-20231002-0.12.0/bin/openocd.exe"
}
```

最后按下F5全速运行，进行下载调试。