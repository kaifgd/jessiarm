https://zeta7.notion.site/zeta7/JessiArm-be431f54912b472fb7f8977e5499612d을 바탕으로 작업했습니다.
# 1장 Install jessiarm code
# jessiarm install on Jetson
cd ~/catkin_ws/src
git clone https://github.com/zeta0707/jessiarm.git
cd ~/catkin_ws
# cv_bridge 빌드
cd ~/Downloads/opencvDownTo34
sudo patch -p1 /opt/ros/melodic/share/cv_bridge/cmake/cv_bridgeConfig.cmake -p1 < cv_brige.patch
cd ~/catkin_ws
cma
# 2장 Teleop by keyboard
# teleop_twist_keyboard 설치
jetson@jp4612GCv346Py37:~/catkin_ws$ git clone https://github.com/ros-teleop/teleop_twist_keyboard.git
jetson@jp4612GCv346Py37:~/catkin_ws$ cma
# launch 파일로 실행
roslaunch jessiarm_control teleop_keyboard.launch
# 위의 teleop_twist_keyboard 기본 기능에서 Jessiarm은 아래의 기능으로 변경했습니다.
j l: 로봇암 좌우
i , : motor1 기울어짐
o . : motor2 기울어짐
u m : motor3 기울어짐
t b: gripper 닫힘, 열림 
U, M: motor4 회전, 기능 삭제
# 3장 Automatic Move
# rosrun으로 ~/catkin_ws에서 joystick, keyboard로 운전한 경우
jetson@jp4612GCv346Py37:~/catkin_ws$ cp automove.txt ~/catkin_ws
jetson@jp4612GCv346Py37:~/catkin_ws$ cp automove.txt ~/catkin_wssrc/jessiarm/jessiarm_control/src/
# roslaunch로 운전한 경우
jetson@jp4612GCv346Py37:~/catkin_ws$ cp ~/.ros/automove.txt ~/catkin_ws/src/jessiarm/jessiarm_control/src
jetson@jp4612GCv346Py37:~/catkin_ws$ cp ~/.ros/automove.txt ~/catkin_ws
# automove 실행
cd catkin_ws
python src/jessiarm/jessiarm_control/src/auto_move.py
# 4장 Verify USB camera
# Jetson에서 카메라 동작 확인
jetson@jp4612GCv346Py37:~$ ls /dev/video*
/dev/video0가 출력된다
jetson@jp4612GCv346Py37:~$ nvgstcapture-1.0 --camsrc=0 --cap-dev-node=/dev/video0
# 5장 blob PicknPlace
# launch로 실행
roslaunch jessiarm_control blob_control.launch
# 6장 Yolo4 PicknPlace
파일에 들어가서 catkin_ws>src>yolov4-for-darknet_ros>darknet_ros>darknet_ros>conflg>ros.yaml을 클릭하여 첫번째 camera_reading의 토픽을 webcam_image로 변경한다.
