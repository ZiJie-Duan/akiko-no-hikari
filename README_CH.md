# 晶子の光 (Akiko-no-Hikari)
# 墨尔本城市微缩灯光模型

## 项目概述
这是为我的朋友所做的离别礼物，为了纪念在墨尔本的生活，因此这是一个墨尔本城市微缩模型，在原有模型基础上加入了光影的效果，可以模拟日出日落和夜晚的效果。

**效果展示视频**：https://youtu.be/LcSbfyCi86A

![项目概览](Imgs/overview.jpg)

这个项目是一个涉及3D打印，电子焊接，单片机编程等多步骤的项目。我会在接下来的文本中介绍如何构建这个项目。

## 材料清单
- **3D打印机** (我使用的是Bambu Lab A1)
- **3D打印材料**：
  - PLA_Matte（框架部分）
  - PETG_Transparent（透光LED轨道）
  - Bambu Lab 官方材料
- **电子元件**：
  - Raspberry Pi Pico RP2040（邮票焊盘版本）
  - WS2812 LED灯带（48个，144个灯珠/米高密度版本）
- **工具**：
  - 电子焊接工具（焊锡、烙铁、线材等等）
  - 强力胶水（用于粘合PLA_Matte和PETG_Transparent材料）

![Raspberry Pi Pico](Imgs/pi.jpg)

## 制作流程

制作大致分为三个步骤：
1. 3D打印 
2. 组装焊接
3. 程序刷写

### 1. 3D打印
在项目文件夹下的`3D_models`文件夹中，有三个文件：
- `akiko_no_hikari_project.f3d`：整体模型（可通过Fusion 360编辑）
- `frame.stl`：框架和各种部件（使用PLA_Matte材料打印）
- `solar_track.stl`：透光LED轨道（使用PETG_Transparent材料打印）

![3D模型](Imgs/3d_model_project.png)

如果你有自行编辑模型的需求，可以直接下载akiko_no_hikari_project.f3d并通过Fusion 360打开进行编辑。

如果你只是想要打印并组装模型，可以直接下载frame.stl和solar_track.stl进行打印。

frame.stl需要使用PLA Matte材料打印，solar_track.stl需要使用PETG Transparent材料打印。

**打印注意事项**：
- 打印`solar_track.stl`时，需调整支撑选项：
  - 仅使用树状支撑
  - 支撑只允许从底部向上生长（不允许模型内部有支撑）
  - 注意控制打印速度和温度

### 2. 组装焊接
1. **连接Raspberry Pi Pico**：
   - 焊接三根线缆至邮票焊盘上，共三根线：
     - 5V电源线
     - GND地线
     - Data数据线（Pin 22）
   - 5V和GND的焊盘位置请参考上面3D模型打印出来的PI支架中预留的位置
   - 焊接时要注意线缆的方向，因为raspberry pi pico最终会被放置在一个特制的支架中，所以线引出的方向要和支架预留的线槽方向一致
   
   ![线缆连接](Imgs/cables.jpg)

2. **LED灯带安装**：
   - 将LED灯带塞入光轨中
   - 将Pi支架和右侧支撑外壳以及光轨组装，并测量三根线到达LED灯带焊盘的大致位置
   - 剪裁电线（要是太短或者太长都会有问题），随后将电线焊接至LED灯带上
   - 如果不方便，你可以把LED灯带抽出来焊接完再塞回光轨中，为什么我们要提前把LED灯带放进去的原因是为了测量线材的长度
   - 焊接三根裁剪好的电线和LED灯带
   
   ![Pi安装](Imgs/pi_install.jpg)

3. **组件组装**：
   - 将灯轨和左侧支架，右侧支架（支撑外壳），PI支架组合好并用强力胶水粘连牢固 
   - 将Pi支架的底部面板扣上去（这不需要胶水，因为后续允许我们按压开发板上的重置按钮）

   ![左侧支架](Imgs/LeftHolder.jpg)
   ![Pi外壳](Imgs/Pi_Shell.jpg)
   ![拆卸图](Imgs/disattach.jpg)

### 3. 程序刷写
1. 按照网络上的步骤为Pi安装MicroPython
2. 将`code/main.py`文件传入Pi中
3. 上电测试

## 技术规格
- **控制器**：Raspberry Pi Pico (RP2040)
- **LED类型**：WS2812可编程RGB LED
- **LED数量**：48个
- **数据引脚**：GPIO 22
- **通信方式**：PIO (可编程输入/输出)状态机
- **时钟频率**：8MHz

## 功能特点
- 使用高斯函数模拟自然光分布
- 通过调整高斯参数控制光位置和扩散范围
- 动态调整RGB颜色值模拟不同时段和色温变化

![成品展示](Imgs/overview2.jpg)

## 注意事项
组装焊接部分可能存在一些问题，选择稍细一点的线组装起来比较容易。

## 联系方式
希望你会喜欢这个模型。如果有任何问题，可以提交issue或发邮件来联系我。