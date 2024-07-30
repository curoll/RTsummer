# RT_Thread_Day5

**用阿里云测试mqtt**，env工具下执行menuconfig 

配置阿里云并改前四个参数

![image-20240730180836000](D:\Typora\Typora\images\image-20240730180836000.png)

配置温湿度传感器ATH10外设

![image-20240730180912070](D:\Typora\Typora\images\image-20240730180912070.png)

![image-20240730180945142](D:\Typora\Typora\images\image-20240730180945142.png)



aliyun代码修改注释

![image-20240730181121719](D:\Typora\Typora\images\image-20240730181121719.png)

测试结果

**文件系统结合FAL配置W25Q64**

1. 开启板上外设

   ![文件系统开关1](D:/qqFiles/RSOC/Pictures/文件系统开关1.png)

2. 配置自动挂载

   ![文件系统开关2](D:/qqFiles/RSOC/Pictures/文件系统开关2.png)

3. 配置Component组件

   ![文件系统开关3](D:/qqFiles/RSOC/Pictures/文件系统开关3.png)

4. 配置DFS

   ![文件系统开关4](D:/qqFiles/RSOC/Pictures/文件系统开关4.png)

5. 配置elmFat

   ![文件系统开关5](D:\Typora\Typora\images\文件系统开关5.png)

6.测试结果

同上，输入list device可以看见块设备，输入cd fal，进入fal目录，键入echo "hello" hello.txt在目录下创建hello.txt文件。
输入mkdir dir创建dir文件夹。输入ls即可查看。