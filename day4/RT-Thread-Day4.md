##  RT-Thread-Day4

![image-20240730004107979](D:\Typora\Typora\images\image-20240730004107979.png)

![image-20240730004122766](D:\Typora\Typora\images\image-20240730004122766.png)

![image-20240730004135083](D:\Typora\Typora\images\image-20240730004135083.png)

![image-20240730004150178](D:\Typora\Typora\images\image-20240730004150178.png)

* 创建、销毁设备

  rt_device_t rt_device_create(int type, int attach_size); • void rt_device_destroy(rt_device_t device);

* 注册、销毁设备

​       rt_err_t rt_device_register(rt_device_t dev, const char*   name,rt_uint8_t flags); 

​       rt_err_t rt_device_unregister(rt_device_t dev)

![image-20240730004432570](D:\Typora\Typora\images\image-20240730004432570.png)

![image-20240730004451020](D:\Typora\Typora\images\image-20240730004451020.png)

![image-20240730004503319](D:\Typora\Typora\images\image-20240730004503319.png)

![image-20240730004546923](D:\Typora\Typora\images\image-20240730004546923.png)

![image-20240730004558749](D:\Typora\Typora\images\image-20240730004558749.png)

![image-20240730004612547](D:\Typora\Typora\images\image-20240730004612547.png)

![image-20240730004623833](D:\Typora\Typora\images\image-20240730004623833.png)

![image-20240730004632805](D:\Typora\Typora\images\image-20240730004632805.png)

![image-20240730004645950](D:\Typora\Typora\images\image-20240730004645950.png)

![image-20240730004656406](D:\Typora\Typora\images\image-20240730004656406.png)

![image-20240730004711242](D:\Typora\Typora\images\image-20240730004711242.png)

![image-20240730004724204](D:\Typora\Typora\images\image-20240730004724204.png)