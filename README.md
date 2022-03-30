# WSL with Windows 11

We can install wsl2 in windows 10, but we need to take extra steps to visualise the Gazebo simulations.


## Install WSL
```
https://pureinfotech.com/install-wsl-windows-11/

```

## Install Basic Stuff
```
sudo apt update
sudo apt upgrade -y
sudo apt install gedit firefox -y

```
## Install ROS, other packages, Workspaces and simulations
```
# ROS
sudo sh -c 'echo "deb http://packages.ros.org/ros/ubuntu $(lsb_release -sc) main" > /etc/apt/sources.list.d/ros-latest.list'
sudo apt install curl # if you haven't already installed curl
curl -s https://raw.githubusercontent.com/ros/rosdistro/master/ros.asc | sudo apt-key add -
sudo apt update
sudo apt install ros-noetic-desktop-full -y
source /opt/ros/noetic/setup.bash
echo "source /opt/ros/noetic/setup.bash" >> ~/.bashrc
source ~/.bashrc
sudo apt install -y python3-rosdep python3-rosinstall python3-rosinstall-generator python3-wstool build-essential
sudo rosdep init
rosdep update
sudo apt update
sudo apt-get install -y python3 
sudo apt install -y python3-pip
sudo ln -s /usr/bin/python3 /usr/bin/python

# Packages
sudo apt install -y git-all python3-colcon-common-extensions python3-vcstool python3-catkin-tools
sudo apt install -y libcanberra-gtk-module libcanberra-gtk3-module 
sudo apt install -y ros-noetic-moveit ros-noetic-moveit-resources-prbt-moveit-config
sudo apt install -y ros-noetic-pilz-industrial-motion-planner ros-noetic-industrial-core
sudo apt install -y ros-noetic-rviz-visual-tools ros-noetic-moveit-visual-tools ros-noetic-tf-conversions 
sudo apt install -y ros-noetic-gazebo-ros-pkgs ros-noetic-gazebo-ros-control ros-noetic-joint-state-controller ros-noetic-fkie-multimaster
sudo apt install -y ros-noetic-ros-control ros-noetic-ros-controllers ros-noetic-navigation ros-noetic-perception
sudo apt install -y ros-noetic-gazebo-ros ros-noetic-ros-control ros-noetic-control-toolbox ros-noetic-realtime-tools ros-noetic-xacro ros-noetic-kdl-parser
sudo apt install -y git-core python3-vcstools ros-noetic-control-msgs ros-noetic-xacro ros-noetic-tf2-ros ros-noetic-rviz ros-noetic-cv-bridge ros-noetic-actionlib ros-noetic-actionlib-msgs ros-noetic-dynamic-reconfigure ros-noetic-trajectory-msgs ros-noetic-rospy-message-converter

# Pip
pip install argparse
pip3 install --upgrade tensorflow-gpu
pip3 install torch torchvision torchaudio --extra-index-url https://download.pytorch.org/whl/cu113
pip install gym
pip install wandb

# Simulations
source /opt/ros/noetic/setup.bash
mkdir -p ~/simulation_ws/src
cd ~/simulation_ws/
catkin_make
echo "source ~/simulation_ws/devel/setup.bash" >> ~/.bashrc
source ~/.bashrc

# catkin workspace
source /opt/ros/noetic/setup.bash
mkdir -p ~/catkin_ws/src
cd ~/catkin_ws/
catkin_make
echo "source ~/catkin_ws/devel/setup.bash" >> ~/.bashrc
source ~/.bashrc

# Install openai_ros
cd ~/catkin_ws/src
git clone -b kinetic-devel https://github.com/ncbdrck/openai_ros.git
git clone https://ncbdrck@bitbucket.org/theconstructcore/theconstruct_msgs.git
cd ~/catkin_ws
rosdep install --from-paths src --ignore-src -r -y
catkin_make
source devel/setup.bash
rosdep install openai_ros


```

## Useful commands
```
CTRL + Shift + Scroll Up/Down = change window transparency level

# Install PyCharm
https://www.lifewire.com/how-to-install-the-pycharm-python-ide-in-linux-4091033
gedit ~/.bashrc
# add below to the code
# export PATH="/opt/pycharm-*/bin:$PATH"
sudo ln -s /opt/pycharm-*/bin/pycharm.sh /usr/local/bin/pycharm


```
