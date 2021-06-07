本软件由 Neuvition, Inc. 发布 www.neuvition.com，主要描述了与本公司雷达设备的交互接口及SDK集成接口

相关的依赖关系及使用说明如下：

1.curl版本
-本SDK链接默认的curl库版本为CURL_OPENSSL_4

2.因本系统依赖openCV3,ROS自带相关库文件版本过低,例如 libimage_proc.so、libcv_bridge.so等等, 这些相关连的库文件需要编译升级，升级方法如下：
2-1.下载ROS_Perception相关模块源码
https://github.com/ros-perception/image_pipeline.git
https://github.com/ros-perception/vision_opencv.git

2-2.checkout与用户系统安装的openCV相同的版本

2-3.运行catkin_make编译，安装更新ROS相关库文件，举例如下(openCV、ros的安装目录需对应修改)
catkin_make -DOpencv_DIR=/usr/share/OpenCV  -DCMAKE_INSTALL_PREFIX=/opt/ros/melodic install


3.编译neuvition_driver，举例如下(openCV、ros的安装目录需对应修改)
catkin_make -DOpencv_DIR=/usr/share/OpenCV  -DCMAKE_INSTALL_PREFIX=/opt/ros/melodic install

4.启动neuvition_driver
roslaunch neuvition_driver neuvition_driver.launch 

5.可以按需要修改 driverparams.yaml 里面的参数，例如IP地址、port端口等



