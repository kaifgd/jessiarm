# Install jessiarm code
#jessiarm install on Jetson
cd ~/catkin_ws/src
git clone https://github.com/zeta0707/jessiarm.git
cd ~/catkin_ws
#cv_bridge 빌드
cd ~/Downloads/opencvDownTo34
sudo patch -p1 /opt/ros/melodic/share/cv_bridge/cmake/cv_bridgeConfig.cmake -p1 < cv_brige.patch
cd ~/catkin_ws
cma
#Teleop by keyboard
#teleop_twist_keyboard 설치
jetson@jp4612GCv346Py37:~/catkin_ws$ git clone https://github.com/ros-teleop/teleop_twist_keyboard.git
jetson@jp4612GCv346Py37:~/catkin_ws$ cma
launch 파일로 실행
roslaunch jessiarm_control teleop_keyboard.launch
#위의 teleop_twist_keyboard 기본 기능에서 Jessiarm은 아래의 기능으로 변경했습니다.
j l: 로봇암 좌우
i , : motor1 기울어짐
o . : motor2 기울어짐
u m : motor3 기울어짐
t b: gripper 닫힘, 열림 
U, M: motor4 회전, 기능 삭제
#Verify USB camera
#Jetson에서 카메라 동작 확인
ls /dev/video*
/dev/video0가 출력된다
nvgstcapture-1.0 --camsrc=0 --cap-dev-node=/dev/video0
