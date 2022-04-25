# Minigeki v0.3-a

## ----------中文---------

这是一款为SEGA的街机音游ONGEKI（音击）设计的迷你控制器。

这是一款基于Lee大佬的魔改版本，指路[原设计](https://github.com/KaiXuan233/Minigeki)。

原设计被发布在了BEMANICN上：[[图一乐\]音击迷你控制器的制作 - BEMANICN](https://bemani.cc/d/142)。

注：我在设计时图方便直接用了嘉立创的EDA，所以source files里的pcbDoc文件是用立创EDA重新导出的，所以AD在读取的时候可能会遇到些问题。

## 结构

与原设计的五层板不同，我只用了一块1.6mm的PCB板。板子的周围预留了8个直径3mm的孔，可以自行加装M3铜柱作为支撑。因为板子的尺寸有250mm * 200mm，所以击打按键的噪音会比普通键盘大很多。如果你想要减小噪音，一方面可以在用于支撑的铜柱下加装橡胶垫（例如家具用的防撞硅胶粒），另一方面可以选择在底部加装一块与PCB尺寸和开孔一致的板子，二者之间填充键盘吸音棉，再用螺丝固定起来。选用非段落轴也可以在一定程度上减小噪音（极力推荐极光紫轴，手感棒噪音小）。

单片机选用了SparkFun Pro Micro，芯片为与Arudino Leonardo一致的ATMega32U4。由于这个单片机存在输出电压3.3V和5V的版本，而LED的工作电压是5V，如果你不慎买到了3.3V的，可以将USB接口左侧预留的J1接口用焊锡连接起来，这样VCC输出将会切换到USB直通的5V，与此同时电路噪音也不会被单片机内部的电路过滤。

整块板子需要用到10颗键轴，6颗用于按键，2颗用于侧键，两颗用于menu键，每一个都需要配备一颗6028封装（国内一般称之为3528反贴）的W2812B LED和凯华的热插拔座。侧键推荐使用1.75U的键帽。因为这个方案没有设计定位板，为了避免打歌的时候太用力把键轴打飞，请尽量选择五脚轴而非三脚轴。

参照原设计，我选择了75mm的调音台推子作为摇杆的替代品，我选用的具体型号是NOBLE XJV60GPV15C-15A20K。上面还可以再加装一个3D打印的仿官机手柄（由原作者设计）。

要想完成组装，你还至少需要电烙铁和螺丝刀。

## 软件

我使用了[XxLittleCxX/ongeki-io: Yet another ongeki io (github.com)](https://github.com/XxLittleCxX/ongeki-io)中的io，控制器部分则魔改了里面的mu3controller固件。Lee还写了[基于键鼠的IO固件](https://github.com/mallow5359/Minigeki/blob/v0.4/Minigeki%20keyboard%20firmware.zip)。无论你选择何种固件，都需要用PlatformIO进行编译和上传。

在烧录好固件后，请在设备管理器中将控制器的串口号设置为COM3，并将比特率改为115200。

## 版权

您可以以商用或非商用目的自由复制、分发、改造本项目，并基于本项目继续构建，但请在authors.txt或文档中标注原作者。

## ----------English Version----------
This is a mini controller for SEGA's arcade rhythm game ONGEKI.

This is a modified version based on [Lee's design](https://github.com/KaiXuan233/Minigeki).

The original design also has been posted on BEMANICN forum (in Chinese): [[图一乐\]音击迷你控制器的制作 - BEMANICN](https://bemani.cc/d/142)

## Structure

Unlike the original dseign, there's only one layer in my solution which is a 1.6mm thick PCB. There's 8 holes around the board so it's a good choice using some copper pillars to support the board. It can be really noisy during your playing since the size of the PCB is 250mm * 200mm. In this situation, add another board under the PCB with exact same size, fill the gap with sponge or something like it, and fix them with screws. 

For the microcontroller, you will need a SparkFun Pro Micro (ATMega32U4) or its "improved" (counterfeit) version. I used a type-c version.

You will need 10 MX key switches for the 6 buttons, 2 side buttons and 2 menu buttons, each with a 6028 WS2812B and a hot swap socket from kalih. I recommend to use 1.75U (1.75 times width) keycaps for the side buttons. To prevernt switches from lossening or even falling off, I really recommend using 5-pin switch rather than the 3-pin one.

A 75mm linear potentiometer is a good replacement of the lever on the original arcade. In my case, I used NOBLE XJV60GPV15C-15A20K. It becomes even better when you have a 3D printed mini knob on it made by the original designer.

To assemble the all the components into a working controller, you will need a soldering iron and a screw driver.

## Software

You can use [XxLittleCxX/ongeki-io: Yet another ongeki io (github.com)](https://github.com/XxLittleCxX/ongeki-io) with my slightly modified version of mu3controller firmware; Or, use the keyboard (and mouse for lever) firmware [wrote by Lee](https://github.com/mallow5359/Minigeki/blob/v0.4/Minigeki%20keyboard%20firmware.zip). Either of which requires PlatformIO to compile and upload.

After burning the firmware, please change the COM id of the controller to COM3, and set the bit rate at 115200.

## License

You can copy, distribute, modify, or build on this project freely, even for commercial purposes, under the condition that you must attribute the work (include me in authors.txt or mention my name in documents).

