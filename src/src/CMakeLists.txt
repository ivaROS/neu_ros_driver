# build the driver node

add_executable(neuvition_node neuvition_node.cc driver.cc )

add_dependencies(neuvition_node neuvition_driver_gencfg)
set  (LIBCURL ${PROJECT_SOURCE_DIR}/lib/libcurl.so)

set(OpenCV_DIR /usr/share/OpenCV)
find_package(OpenCV 3 REQUIRED)

#${Boost_LIBRARIES}
target_link_libraries(neuvition_node
  ${catkin_LIBRARIES} 
  ${PCL_LIBRARIES}
  ${OpenCV_LIBS}
  ${LIBCURL}
  ${PROJECT_SOURCE_DIR}/lib/libneusdk_boost_1_65.so
)

#${Boost_LIBRARIES}
# build the nodelet version
add_library(neuvdrv_nodelet nodelet.cc driver.cc  )
add_dependencies(neuvdrv_nodelet neuvition_driver_gencfg)
target_link_libraries(neuvdrv_nodelet
  ${catkin_LIBRARIES}
  ${PCL_LIBRARIES}
  ${OpenCV_LIBS}
  ${LIBCURL}
)

# install runtime files
install(TARGETS neuvition_node
        RUNTIME DESTINATION ${CATKIN_PACKAGE_BIN_DESTINATION}
        COMPONENT main
)
install(TARGETS neuvdrv_nodelet
        LIBRARY DESTINATION ${CATKIN_PACKAGE_LIB_DESTINATION}
)

install(TARGETS neuvition_node
  ARCHIVE DESTINATION ${CATKIN_PACKAGE_LIB_DESTINATION}
  LIBRARY DESTINATION ${CATKIN_PACKAGE_LIB_DESTINATION}
  RUNTIME DESTINATION ${CATKIN_PACKAGE_BIN_DESTINATION}
)
