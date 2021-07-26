This Software License is hold by Neuvition, Inc. www.neuvition.com
Which describes the interface of interact with Lidar devices.
 

The dependences:
1.curl version
-the SDK defaultly linked with version CURL_OPENSSL_4 of curl.
-need you change the linker of 'neu_ros_driver/src/lib/libcurl.so' according to your system path. 

2.As the compiled SDK depends on openCV3, you need update your ROS's related components such as libimage_proc.so、libcv_bridge.so... and so on.
you may need downloading ROS_Perception source code and compile-installing the modules. you refer to the following steps:

2-1. download the source code from github
https://github.com/ros-perception/image_pipeline.git
https://github.com/ros-perception/vision_opencv.git

2-2. checkout the source code to the same version of your installed openCV

2-3. run catkin_make to do compile，then install the components. for example: (you need change the INSTALL_PREFIX to your openCV path and ros path)
catkin_make -DOpencv_DIR=/usr/share/OpenCV  -DCMAKE_INSTALL_PREFIX=/opt/ros/melodic install


3.compile the source code of neuvition_driver(you need change the INSTALL_PREFIX to your openCV path and ros path)
catkin_make -DOpencv_DIR=/usr/share/OpenCV  -DCMAKE_INSTALL_PREFIX=/opt/ros/melodic install

4.the default SDK library is for 'x86' arch, which locates in 'neu_ros_driver/src/lib/libneusdk_boost_1_65.so'. 
  you can modify this linker for 'arm' architecture as well. 

5. launch neuvition_driver
roslaunch neuvition_driver neuvition_driver.launch 

6. you can change the parameters in 'driverparams.yaml' if need


