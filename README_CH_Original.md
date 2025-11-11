# akiko-no-hikari
Miniature Melbourne City Lighting Model

这是为我的朋友所做的离别礼物，为了纪念在墨尔本的生活，因此这是一个墨尔本城市微缩模型，在原有模型基础上加入了光影的效果，可以模拟日出日落和夜晚的效果。

以下是效果展示视频：https://youtu.be/LcSbfyCi86A

这个项目是一个涉及3D打印，电子焊接，单片机变成等 多步骤的项目。我会在接下来的文本中介绍如何构建这个项目。

材料清单：
- 3D打印机 (我使用的是Bambu Lab A1)
- 3D打印材料（PLA_Matte 和 PETG_Transparent, Bambu Lab 官方材料）
- 电子焊接工具（焊锡，烙铁，线材 等等）
- 单片机（Raspberry Pi Pico RP2040 邮票焊盘版本）
- WS2812 LED 灯带（48个， 144个灯珠/米 高密度版本）
- 强力胶水 （可以用来粘 PLA_Matte 和 PETG_Transparent）

制作大致分为三个步骤
1, 3D打印 
2, 组装焊接
3, 程序刷写

# 3D打印
在项目文件夹 下的 3D_models 文件夹中，有三个文件：
- akiko_no_hikari_project.f3d （整体模型）
- frame.stl (PLA_Matte 材料打印的框架 和 各种部件)
- solar_track.stl (PETG_Transparent 材料打印的透光LED轨道)

如果你有自行编辑模型的需求，可以直接下载akiko_no_hikari_project.f3d并通过Fusion 360 打开进行编辑。

如果你只是想要打印并组装模型，可以直接下载frame.stl和solar_track.stl进行打印。

frame.stl 需要使用 PLA Matte 材料打印，solar_track.stl 需要使用 PETG Transparent 材料打印。

注意，在打印 solar_track.stl 时，需要调整支撑选项，只允许使用树状支撑，并且支撑只允许从底部向上生长（不允许模型内部有支撑）。然后注意打印速度和温度控制。


# 组装焊接
1, 将线缆焊接至 raspberry pi pico 的邮票焊盘上，共三根线
- 5V 电源线 
- GND 地线
- Data 数据线 Pin 22
5V和GND的焊盘位置请参考上面3D模型打印出来的 PI 支架中预留的位置。
焊接时要注意线缆的方向，因为 raspberry pi pico 最终会被放置在一个特制的支架中，所以线引出的方向要和支架预留的线槽方向一致。
（Pi 在支架中，并且线缆已经连接完成 /home/zijie/akiko-no-hikari/Imgs/cables.jpg）
2, 将led灯带塞入光轨中
3, 将Pi支架和右侧支撑外壳 以及 光轨组装，并测量三根线到达LED灯带焊盘的大致位置
4, 剪裁电线（要是太短或者太长都会有问题），随后将电线焊接至LED灯带上。（如果不方便，你可以把LED灯带抽出来 焊接完再塞回光轨中，为什么 我们要提前把LED灯带放进去的原因是为了测量线材的长度）
5, 焊接三根裁剪好的电线和LED灯带。
6, 将灯轨 和 左侧支架 ，右侧支架（支撑外壳），PI支架 组合好并用强力胶水粘连牢固 
7, 将Pi支架的底部面板扣上去（这不需要胶水，因为后续允许我们按压开发板上的重置按钮）

# 程序刷写
1, 按照网络上的步骤为Pi 安装 Micropython
2, 将/home/zijie/akiko-no-hikari/code/main.py 文件传入Pi中
3，上电测试

以上就是整个模型组装的所有步骤，这个模型的 组装焊接部分可能存在一些问题，选择稍细一点的线组装起来比较容易。

希望你会喜欢这个模型。如果有任何问题，可以提交issue或发邮件来联系我。