# YDLidar 설치

Lidar를 사용하기 위해서 제공하는 드라이버를 설치하는 방법이다. 
설치 OS의 경우 Ubuntu기준이며, Raspbian OS에서도 정상 동작하는 것을 확인하였다.

- 먼저 YDLidar에서 제공하는 드라이버를 설치해야하며 설치 방법은 아래와 같다
1. 터미널을 열고 설치 도구 설치한다 
```shell
sudo apt install cmake pkg-config
```
2. YDLidar SDK 설치
```shell
git clone https://github.com/YDLIDAR/YDLidar-SDK.git
cd YDLidar-SDK
mkdir build
cd build
cmake ..
make
sudo make install
cd
```
3. YDLidar ROS Driver 설치 [위의 제공되는 SDK를 설치한 다음 ROS에서 사용할 수 있게 제공되는 YDLidar-ros-driver를 설치한다]
```shell
cd catkin_ws/src
git clone https://github.com/YDLIDAR/ydlidar_ros_driver.git ydlidar_ros_driver
cd ..
catkin_make
cd
```
4. Create Serial Port Alias [선택사항, Serial Port에 자동적으로 접속하기 위해 등록한다]
```shell
cd catkin_ws
chmod 0777 src/ydlidar_ros_driver/startup/*
sudo sh src/ydlidar_ros_driver/startup/initenv.sh
cd
```
- 여기까지가 YDLidar를 사용하기 위하여 Driver를 설치한 방법이다. YDLidar의 패키지가 정확하게 설치되었는지 실행해본다.

5. YDLidar launch파일 실행
- 먼저 YDLidar제품 중 사용하고 있는 제품을 확인 한다. 
```shell
cd catkin_ws/src/ydlidar_ros_driver/launch
ls
cd
```
- 사용 YDLidar 제품이 X2 제품일 경우 해당하는 파일을 launch한다. (예시 : YDLidar X2 제품 사용 시 X2,launch 실행)
```shell
roslaunch ydlidar_ros_driver X2.launch
```

- 각 해당하는 모델의 스펙을 확인하고 launch 파일 안의 파라메터를 조정하여 테스트 한다.
