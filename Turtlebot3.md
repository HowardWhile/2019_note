# Turtlebot3

[TOC]



### 組裝

先將raspberry pi使用apt更新

```shell
sudo apt update
sudo apt upgrade
```

### ROS更新跳錯誤

它可能看起來像這樣

```bash
pi@raspberrypi:~ $ sudo apt update 
Hit:1 http://linux.teamviewer.com/deb stable InRelease
Hit:3 http://archive.raspberrypi.org/debian stretch InRelease                  
Hit:4 http://raspbian.raspberrypi.org/raspbian stretch InRelease         
Get:2 http://packages.ros.org/ros/ubuntu stretch InRelease [4,661 B]
Err:2 http://packages.ros.org/ros/ubuntu stretch InRelease      
  The following signatures couldn't be verified because the public key is not available: NO_PUBKEY F42ED6FBAB17C654
Fetched 4,661 B in 2s (2,146 B/s)
Reading package lists... Done
Building dependency tree       
Reading state information... Done
5 packages can be upgraded. Run 'apt list --upgradable' to see them.
W: An error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: http://packages.ros.org/ros/ubuntu stretch InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY F42ED6FBAB17C654
W: Failed to fetch http://packages.ros.org/ros/ubuntu/dists/stretch/InRelease  The following signatures couldn't be verified because the public key is not available: NO_PUBKEY F42ED6FBAB17C654
W: Some index files failed to download. They have been ignored, or old ones used instead.
```

原因是ROS的版本庫被攻擊所以他們決定換一下鑰匙[文章連結](https://discourse.ros.org/t/new-gpg-keys-deployed-for-packages-ros-org/9454?fbclid=IwAR1lCDy71YN6irXdBE2Z_S335a6XGkTgPm8SdzN_lq02FW2mOL1PP4YNBw0)

```shell
#更新金鑰就不會出錯了
sudo apt-key adv --keyserver 'hkp://keyserver.ubuntu.com:80' --recv-key C1CF6E31E6BADE8868B172B4F42ED6FBAB17C654
sudo apt update

#刪除舊的金鑰避免下載到偽裝的檔案
sudo apt-key del 421C365BD9FF1F717815A3895523BAEEB01FA116
sudo apt update
sudo apt upgrade
```

### Raspberry PI 時間同步問題

有連上外網時，時間會自動同步，頭痛的是沒有外網可以用的情況。

http://blog.topspeedsnail.com/archives/8165

https://askubuntu.com/questions/14558/how-do-i-setup-a-local-ntp-server

https://stackoverflow.com/questions/21432002/ntp-configuration-without-internet

https://serverfault.com/questions/806274/how-to-set-up-local-ntp-server-without-internet-access-on-ubuntu

https://wiki.utshop.tw/doku.php/linux:ntpd

https://www.tecmint.com/synchronize-time-with-ntp-in-linux/



**上位Server端 192.168.10.1**

用ntp架設一個ntp server

```shell
sudo apt install ntp
```

編輯 `/etc/ntp.conf`在檔案的結尾增加以下訊息，讓server在沒有外網的情況下使用本機時間。

```shell
server 127.127.1.0 prefer
fudge 127.127.1.0 stratum 10
```

保存後重啟service

```shell
sudo systemctl restart ntp.service
```

**Client端**

**方法1**：在ntp.conf加入server開機自動獲取時間

編輯 `/etc/ntp.conf`在檔案中增加以下訊息

```shell
# You do need to talk to an NTP server or two (or three).
#server ntp.your-provider.example
server 192.168.10.1 prefer
restrict 192.168.10.1
```

保存後重啟service

```shell
sudo systemctl restart ntp.service
```

要等待一段時間(幾分鐘)才會更新，可以透過指令看看目前的

```shell
ntpq -p
```



或是使用方法2強制同步

**方法2**：利用預設的ntpdate強制更新，如果有安裝過ntp要先停止對應的service

```shell
#sudo systemctl stop ntp.service
sudo ntpdate 192.168.10.1
#sudo systemctl start ntp.service
```

需要顯示debug的訊息可以使用

```shell
ntpdate -d 192.168.10.1
```

### 使用Cartographer

http://emanual.robotis.com/docs/en/platform/turtlebot3/slam/#run-slam-nodes

要先準備Cartographer的環境

```shell
# 安裝Cartographer for ros 但這些還不足以執行
sudo apt-get install ros-kinetic-cartographer*

# 還需要用以下的方法編譯出Cartographer的函示庫
sudo apt-get install ninja-build libceres-dev libprotobuf-dev protobuf-compiler libprotoc-dev

cd ~/catkin_ws/src

git clone https://github.com/googlecartographer/cartographer.git
git clone https://github.com/googlecartographer/cartographer_ros.git
cd ~/catkin_ws

src/cartographer/scripts/install_proto3.sh
rm -rf protobuf/

rosdep install --from-paths src --ignore-src -r -y --os=ubuntu:xenial

# 只能留cartographer的pkg 其他catkin的pkg不能被這個東西編譯
# 編譯完得到3個isolated的資料夾 ( build_isolated, devel_isolated, install_isolated ) 在 catkin_ws

catkin_make_isolated --install --use-ninja

```

運行

```shell
#有source catkin_ws/devel/setup.bash就不一定要source這個? 
source ~/catkin_ws/install_isolated/setup.bash  

roslaunch turtlebot3_slam turtlebot3_slam.launch slam_methods:=cartographer
```

> 2019/06/21 apt install 的 turtlebot3_slam 的slam_flat_world_imu異常沒辦法將topic imu 轉換程 flat_imu，連帶影響到turtlebot3_slam.launch。後來我是直接編譯github的src才成功運行cartographer。
>
> git clone https://github.com/ROBOTIS-GIT/turtlebot3.git 
>
> 只需要turtlebot3_slam  其他使用apt install 的版本



# [Home](./Home)



