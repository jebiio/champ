
# Setup

```bash
sudo apt install -y python3-rosdep ros-noetic-vision-msgs ros-noetic-geometry-msgs
pip install typing cast_control
mkdir ~/go1auto_ws/src -p
cd ~/go1auto_ws/src
git clone --recursive https://github.com/jebiio/champ.git -b go1auto
git clone https://github.com/chvmp/champ_teleop
git clone https://github.com/jebiio/robots.git -b go1auto
cd ~/go1auto_ws/src/robots
./install_descriptions
git clone https://github.com/jebiio/m-explore.git -b go1auto
git clone https://github.com/jebiio/yolov7-ros.git -b go1auto
cd ~/go1_auto_ws/src/yolov7-ros
pip install -r requirements.txt
cd ~/go1auto_ws
rosdep install --from-paths src --ignore-src -r -y
catkin_make
```

# Run
