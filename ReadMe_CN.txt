本软件由 Neuvition, Inc. 发布 www.neuvition.com，主要描述了与本公司雷达设备的交互接口及SDK集成接口

相关的依赖关系及使用说明如下：

1.curl版本
-本SDK链接默认的curl库版本为CURL_OPENSSL_4
-编译时请根据系统curl路径修改 neu_ros_driver/src/lib/libcurl.so 对应的链接


2.openCV版本问题可修改目录 src 和　src/src 下CMakelist.txt中的opencv版本


3.本SDK默认运行环境为X86, SDK library存放在neu_ros_driver/src/lib/libneusdk_boost_*.so 
  同时也提供了arm的SDK library. 请在编译时相应修改neu_ros_driver/src/lib/libneusdk_boost_*.so对应的链接，git分支可切换到arm分支

4.启动neuvition_driver 
roslaunch neuvition_driver neuvition_driver.launch 
或者两个终端,一个执行roscore，一个执行rosrun neuvition_driver neuvition_node



[常见问题]:
a. 系统安装boost库版本与neu_ros_driver/src/lib/libneusdk_boost.so指向的链接库版本不兼容,导致crash
->请检查 cat include/boost/version.hpp 的版本号, 如果版本低于1.70, 则需要修改软链接指向x86/libneusdk_boost-18.04.so.3.0.3




