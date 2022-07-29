This software is published by Neuvition, Inc. www.neuvition.com and mainly describes the interactive interface and SDK integration interface with the company's radar equipment


Related dependencies and instructions are as follows:


1. The curl version

- The default version of curl is CURL_OPENSSL_4

Curl - compile time please according to the system path modification neu_ros_driver/SRC/lib/libcurl. So the corresponding link



2. OpenCV version You can modify the openCV version in cmakelist. TXT under SRC and SRC/SRC



3. The default operating environment of the SDK is X86. The SDK library is stored in neu_ros_driver/ SRC /lib/libneusdk_boost_*.so

The ARM SDK library is also provided. Please modify the link corresponding to neu_ros_driver/ SRC /lib/libneusdk_boost_*. So at compile time, Git branch can be switched to ARM branch


4. Start neuvition_driver

roslaunch neuvition_driver neuvition_driver.launch

Or two terminals, one executing roscore and one executing rosrun neuvition_driver neuvition_node




Frequently Asked Questions:

A. The version of the installed boost library is incompatible with the version of the link library that neu_ros_driver/ SRC /lib/libneusdk_boost. So, causing the crash

- > please check the cat include/boost/version. The HPP version number, if the version is lower than 1.70, the need to modify the soft links pointing to the x86 / libneusdk_boost - 18.04 so. 3.0.3

Modify radar parameters in driverPARAMs. YAMl
