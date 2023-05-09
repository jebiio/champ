# Champ
* 4족로봇 개발 플랫폼

## 1. Champ setup방법
### 1.1 Install

```bash
sudo apt install -y python3-rosdep
mkdir ~/champ_ws/src -p
cd ~/champ_ws/src
git clone --recursive https://github.com/chvmp/champ
git clone https://github.com/chvmp/champ_teleop
cd ~/champ_ws
rosdep install --from-paths src --ignore-src -r -y
catkin_make
source ~/champ_ws/devel/setup.bash
```

* error: ‘chrono_literals’ is not a namespace-name
  * champ_gazebo CMakeLists.txt add_compile_options(-std=c++17) 로 수정

### 1.2 Run
[master branch](https://github.com/chvmp/champ) 참조

## 2. go1 auto slam

* Champ(Go1) + Explore-lite + yolov7-ros

### Setup

```bash
sudo apt install -y python3-rosdep ros-noetic-vision-msgs ros-noetic-geometry-msgs
pip install typing cast_control
mkdir ~/go1auto_ws/src -p
cd ~/go1auto_ws/src
git clone --recursive https://github.com/jebiio/champ.git -b go1auto
git clone https://github.com/chvmp/champ_teleop
git clone https://github.com/jebiio/robots.git -b go1auto
git clone https://github.com/jebiio/m-explore.git -b go1auto
git clone https://github.com/jebiio/yolov7-ros.git -b go1auto
cd ~/go1auto_ws/src/robots
./install_descriptions
cd ~/go1auto_ws/src/yolov7-ros
pip install -r requirements.txt
cd ~/go1auto_ws
rosdep install --from-paths src --ignore-src -r -y
catkin_make
```

### Run

1. source env.
```bash
source ~/go1auto_ws/devel/setup.bash
```

2. gazebo

```bash
roslaunch go1_config gazebo.launch
```

3. explore-lite

```bash
roslaunch go1_config slam.launch
```

4. yolo

```bash
roslaunch yolov7_ros my_detect.launch
```
