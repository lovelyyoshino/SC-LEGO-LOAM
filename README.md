# SC-LEGO-LOAM
本项目解读了SC-LeGO-LOAM的相关代码，具体操作步骤如下：

**1.Ubuntu** and **ROS**

Ubuntu 64-bit 18.04.

ROS Melodic. [ROS Installation](http://wiki.ros.org/ROS/Installation)

**2.** 安装 **GTSAM**

最好安装4.0.0-alpha2的GTSAM版本

```bash
wget -O ~/Downloads/gtsam.zip https://github.com/borglab/gtsam/archive/4.0.0-alpha2.zip
cd ~/Downloads/ && unzip gtsam.zip -d ~/Downloads/
cd ~/Downloads/gtsam-4.0.0-alpha2/
mkdir build && cd build
cmake ..
sudo make install
```

**3.** 安装 **SC-LeGO-LOAM**

```bash
cd ~/catkin_ws/src
git clone https://github.com/lovelyyoshino/SC-LEGO-LOAM.git
cd ..
catkin_make
source devel/setup.bash
```

**4.** 下载 **KITTI数据集**

下载[KITTI sequence 05](https://drive.google.com/open?id=18ilF7GZDg2tmT6sD5pd1RjqO0XJLn9Mv) 或者 [KITTI sequence 07](https://drive.google.com/open?id=1VpoKm7f4es4ISQ-psp4CV3iylcA4eu0-)，这两个都是标准的ros的bag包，如果自己需要可以使用kitti2bag来自行转换

```bash
sudo apt-get install unzip 
cp ~/Downloads/2011_09_30_0027.zip ~/catkin_ws/src/SC-LEGO-LOAM/SC-LeGO-LOAM/LeGO-LOAM/dataset/
cd ~/catkin_ws/src/SC-LEGO-LOAM/SC-LeGO-LOAM/LeGO-LOAM/dataset/
unzip 2011_09_30_0027.zip
```

**5.** 运行代码

```bash
#实时运行
roslaunch lego_loam run.launch
rosbag play 2011_09_30_0027.bag
#根据pcd来绘制地图
roslaunch lego_loam map_loader.launch
```

![1621391821](https://github.com/lovelyyoshino/SC-LEGO-LOAM/blob/main/image/1621391821(1).jpg)
