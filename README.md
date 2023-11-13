# Install jessiarm code
cd ~/catkin_ws/src
git clone https://github.com/zeta0707/jessiarm.git
cd ~/catkin_ws
cd ~/Downloads/opencvDownTo34
sudo patch -p1 /opt/ros/melodic/share/cv_bridge/cmake/cv_bridgeConfig.cmake -p1 < cv_brige.patch
cd ~/catkin_ws
cma
#Teleop by keyboard
jetson@jp4612GCv346Py37:~/catkin_ws$ git clone https://github.com/ros-teleop/teleop_twist_keyboard.git
jetson@jp4612GCv346Py37:~/catkin_ws$ cma
launch 파일로 실행
roslaunch jessiarm_control teleop_keyboard.launch
#Verify USB camera
ls /dev/video*
/dev/video0가 출력된다
nvgstcapture-1.0 --camsrc=0 --cap-dev-node=/dev/video0
