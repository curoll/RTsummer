# RT-Thread-Day2

**RT-Thread启动流程**



![image-20240723193842013](D:\Typora\Typora\images\image-20240723193842013.png)

rtthread_startup()之后流程

关闭中断--->初始化板子外设(串口...)--->打印启动的Logo--->初始化定时器--->初始化调度器--->信号初始化--->应用初始化--->线程初始化

idle一般默认线程，与FreeRTOs类似

**线程**

![image-20240723195125096](D:\Typora\Typora\images\image-20240723195125096.png)

![image-20240723195319309](D:\Typora\Typora\images\image-20240723195319309.png)

![image-20240723195510915](D:\Typora\Typora\images\image-20240723195510915.png)

![image-20240723195613068](D:\Typora\Typora\images\image-20240723195613068.png)

这里线程状态转化与FreeRTOS基本一样，直接看函数即可。**实际上main函数也是一个线程，通过入口函数进来的**

```c
static void thread1_entry(void *parameter)//参数可不选
{
	rt_uint32_t count =0;
    while(1)
    {
      rt_kprintf(".....");
      rt_thread_mdelay(500);
    }
}
```

![image-20240723200551932](D:\Typora\Typora\images\image-20240723200551932.png)

![image-20240723200627191](D:\Typora\Typora\images\image-20240723200627191.png)

作业：创建一个线程

```c
#include <board.h>
#include <rtthread.h>
#include <drv_gpio.h>
#include <rtdevice.h>

#define GPIO_LED_R    GET_PIN(F, 12)

/* 线程入口函数 */
static void thread_entry(void *parameter)
{
    while (1)
    {
        rt_kprintf("thread is running... LED ON\n");
        rt_pin_write(GPIO_LED_R , PIN_HIGH);  // LED灯亮
        rt_thread_mdelay(500);                // 亮500毫秒

        rt_kprintf("thread is running... LED OFF\n");
        rt_pin_write(GPIO_LED_R, PIN_LOW);     // LED灯灭
        rt_thread_mdelay(500);                // 灭500毫秒
    }
}

int main()
{
    rt_pin_mode(GPIO_LED_R, PIN_MODE_OUTPUT);  // 设置GPIO_LED_R为输出模式
    /* 创建线程 */
    const char* thread_name = "thread1";
    rt_thread_t thread = rt_thread_create(thread_name, 
                                           thread_entry, 
                                           RT_NULL, 
                                           1024, 
                                           25, 
                                           10);
    
    if (thread != RT_NULL)
    {
        /* 启动线程 */
        rt_thread_startup(thread);
    }
    else
    {
        rt_kprintf("create thread failed!\n");
    }
    
    return 0;
}
```

板子上的LED0.5s闪烁一次，串口打印LED的状态

![image-20240723204917746](D:\Typora\Typora\images\image-20240723204917746.png)