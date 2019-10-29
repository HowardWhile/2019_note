---
typora-root-url: ./
---



# Drone

### 模擬器

#### tum 

http://wiki.ros.org/tum_simulator



#### hector

模擬的無人機有2D雷射與攝影機

http://wiki.ros.org/hector_quadrotor/

安裝

```shell
cd ~/catkin_ws/src
git clone https://github.com/tu-darmstadt-ros-pkg/hector_quadrotor
cd ~/catkin_ws
rosdep install --from-paths src -i
catkin_make
```

執行

```shell
roscore
roslaunch hector_quadrotor_demo indoor_slam_gazebo.launch
roslaunch hector_quadrotor_teleop xbox_controller.launch 
```

搖桿 (我用PS4的搖桿)

- R1啟動螺旋槳 (要啟動才能控制)
- O關閉螺旋槳
- 左類比搖桿 上下控制起降 左右控制左右旋轉

- 右類比搖桿 上下控制前後 左右控制左右平移





# [Home](./Home.md)

