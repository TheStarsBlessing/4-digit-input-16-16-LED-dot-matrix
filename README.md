# 4-digit-input-16-16-LED-dot-matrix
一个可以通过四位输入信号以2个时钟信号为周期的速度驱动16*16led阵列的扫描式led显示板。
## 项目简介
一个可以通过四位输入信号以2个时钟周期的速度驱动`16*16`led阵列的扫描式led显示板。
这个简单的LED点阵是我为我的4位CPU（就是著名的TD4CPU）做的外设（4位CPU每个指令周期仅能输出4bit数据，因此需要将两个指令周期的信号合并起来才能驱动`16*16`的LED点阵），电路简单，板子大小在`100*100（mm）`以内，并添加了许多漂亮的图片，总体来说比较漂亮。

本工程在立创开源平台也有发布，请参考https://oshwhub.com/the_starts-blessing/4-bit-input-1616led-dot-matrix

## 项目功能
1.欣赏老婆们(划掉)（太刑了），感谢嘉立创的彩色丝印！
2.通过内部寄存器整合两个四bit数据，在译码后输出至`16*16`LED点阵上，每两个指令周期可点亮点阵上任意一个LED灯。
3.通过左右两侧的排针可以对任意行或列LED进行直接操作。

## 项目参数
5V电源输入，4位控制信号输入，输入时钟频率不低于`48*(需要点亮的LED数目)`Hz，不高于10MHz（参考值）。

## 原理解析（硬件说明）
时钟信号通过一个jk触发器（74hc112）进行二分频，Q与Q#分别作为前端一个与后端两个74hc161(可预置四位二进制计数器)的时钟信号，在第一个时钟周期下降沿，前端74hc161对输入第一个4bit数据进行锁存：在第二个时钟周期下降沿，后端输入侧74hc161对前端进行读取并锁存，输出侧74hc161对输入信号进行锁存，此时后端74hc161输出信号输入至74hc154（4-16线译码器）进行译码，最后输入侧通过两个74hc540进行反相控制列，输出侧控制行，在（行/列）处点亮一个LED。
proteus仿真如下图所示：

![image](https://github.com/user-attachments/assets/735195a7-ac22-46fe-a42a-20a7deaf1bd9)

## 注意事项
1.彩色丝印若发生异常重叠，请剪切后粘至原位置，再次渲染即可恢复。
2.本工程原则上禁止商用，但允许在删除所有彩色丝印图片后进行商用。（依据原神周边相关规定，带有官图的产品不可用商用，具体规定请参考https://m.bilibili.com/opus/596519933203383519 ）
## 参考图
原理图

![image](https://github.com/user-attachments/assets/23c05919-b60d-4cb8-acab-0bb339ca4122)

仿真图

![image](https://github.com/user-attachments/assets/93607fa6-1880-44a1-9f7d-a64ffa692d83)
![image](https://github.com/user-attachments/assets/3eabc957-451e-42ca-87de-0a001bb9da79)

## 实物图

![df0a0603b7d04e6f968344df1b82a6c8](https://github.com/user-attachments/assets/e6b4840c-002c-47d5-a21c-71110de96d46)
![微信图片_20250403235254](https://github.com/user-attachments/assets/30cd263e-884e-4946-a881-92ecdb2a41e3)

与TD4组合测试

![微信图片_20250404000537](https://github.com/user-attachments/assets/78bde76b-c7c9-4288-8ff3-8ffa084b59ef)

## 版本更新
2024.11.18  调整了部分丝印
  
2025.4.3 重新上传了电路图
  
未来我会写一个可以为这个灯板进行可视化编程的窗口程序，敬请期待！
