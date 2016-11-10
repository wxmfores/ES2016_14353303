#ROS配置
1.设置软件源

`$ sudo sh -c 'echo "deb http://packages.ros.org/ros/ubuntu (lsb_release -sc) main" > /etc/apt/sources.list.d/ros-latest.list`

一旦添加了正确的软件源，操作系统就知道去哪里下载程序，并根据命令自动安装软件。

2.设置密钥

`$ sudo apt-key adv --keyserver hkp://ha.pool.sks-keyservers.net:80 --recv-key 0xB01FA116`

3.安装

首先确认你的Debian的软件包索引是最新的。

`$ sudo apt-get update`

在ROS中有许多不同的函数库和工具，建议是完全安装，也可以根据自己的要求分别安装。完全安装时的工具包括ROS、rqt、可视化环境rviz、通用机器人库robot-generic libraries、2D（如stage）和3D（如Gazebo）仿真环境2D/3D simulators、导航功能包集navigation and 2D/3D（移动、定位、地图绘制、机械臂控制）、感知库perception（如视觉、激光雷达、RGB-D摄像头等）。

`$ sudo apt-get install ros-indigo-desktop-full`

4.初始化rosdep

rosdep不仅能够使你更方便的安装一些系统依赖程序包，而且ROS的一些主要部件的运行也需要rosdep。

`$ sudo rosdep init`

`$ rosdep update`

5.安装rosinstall

rosinstall命令是一个使用的非常频繁的命令，使用这个命令可以轻松的下载许多ROS软件包。

`$ sudo apt-get install python-rosinstall`

6.设置环境

添加ROS的环境变量，这样，当你打开你新的shell时，你的bash会话中会自动添加环境变量。

`$ echo "source /opt/ros/jade/setup.bash" >> ~/.bashrc`

`$ source ~/.bashrc`




