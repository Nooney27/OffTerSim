
# Installation instructions:
Simulator build on top of OffTerSim : https://github.com/dvij542/OffTerSim/tree/main


1. Clone this repo
```
https://github.com/Nooney27/OffTerSim.git
```
Unity Project:
If you want to modify the unity environment follow steps 2 to 7 otherwise go directly to gym environment: 
2. Download and install unity hub: https://unity.com/unity-hub 
3. Open Unity hub and navigate to Projects, Add
4. Add the new Project by pointing to this repo. Unity should suggest you to Download an editor version (2021.3.24f1), install it. Otherwise open the Installs tab on the left hand side of the unity hub menu. Then, click on Install Editor button and install the 2021.3.XXXX
5. Open the Project
6. If the Train_env scene is not open by default, open it from Assets/Karting/Scenes.
7. Click on Play and if everything worked fine, it should take about 10-15s to generate a new environment and spawn the buggy car.

Making a gym environment:
8. Follow the unity ml-agents installation guide: https://github.com/Unity-Technologies/ml-agents/blob/develop/docs/Installation.md
We are using python 3.10.12, mlagents 1.1.0.dev0 (check installed_packages.txt)
```
conda create -n mlagents python=3.10.12 && conda activate mlagents

```
9. Run test_env_windows.py to see if the installation is successful

Extra:

ROS2 interface

You can also interact with the simulator as a ROS2 node. Full ROS2 integration is a WIP. To get started, follow the given steps:-

1. Install [ROS2](https://docs.ros.org/en/foxy/Installation.html) (Foxy, Iron or any other version)
2. Install dependencies :-
```
sudo apt-get install ros-<ROS_VERSION>-ackermann-msgs
sudo apt-get install ros-<ROS_VERSION>-sensor-msgs
sudo apt-get install ros-<ROS_VERSION>-geometry-msgs
```
3. If on linux, also install [mono-project](https://www.mono-project.com/download/stable/#download-lin) required for reading images within the application
4. Change permissions of the ros2-env built environment with :-
```
cd ros2-env
sudo chmod 777 *
cd ..
```
5. Your params.yaml file should be in the same directory you run from. It should contain the path to the heightmap, the spawn position and which sensors to use. Run 'ros2_interface.py'
```
source /opt/ros/<ROS_VERSION>/setup.bash
python3 ros2_interface.py
```
This should open a new simulator session with ROS2 wrapper. You can see the available topics with 'ros2 topic list' in a new terminal and it should list all sensor topics, pose, velocity and acceleration topics and the /cmd topic from where it listens to acceleration and throttle commands
6. (optional) You can launch the example keyboard teleop script under Scripts/keyboard_controller.py that publishes to '/cmd' topic from the arrow keys to control the car. You may need to install pygame to run the script
```
source /opt/ros/<ROS_VERSION>/setup.bash
python3 Scripts/keyboard_controller.py
```
7. (optional) You can open rviz2 to visualize the sensor readings

```
source /opt/ros/<ROS_VERSION>/setup.bash
rviz2
```
