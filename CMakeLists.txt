cmake_minimum_required(VERSION 2.8.3)
project(measuretemperature)


find_package(catkin REQUIRED COMPONENTS roscpp genmsg) 

set ( CMAKE_CXX_FLAGS "-Ofast -march=native -mno-avx -ggdb")

#add_action_files(
#  DIRECTORY action
#  FILES Fremen2DGrid.action
#)

#generate_messages(
#   DEPENDENCIES actionlib_msgs nav_msgs 
#)

catkin_package()

include_directories(${catkin_INCLUDE_DIRS}) 

add_executable(measureTemperature src/measureTemperature.cpp)

add_dependencies(measureTemperature ${catkin_EXPORTED_TARGETS} ${PROJECT_NAME}_generate_messages_cpp)

#add_library(phaseModel src/CPhaseModelNaive.cpp)

#target_link_libraries (phaseModelSet ${catkin_LIBRARIES} phaseModel)
target_link_libraries (measureTemperature ${catkin_LIBRARIES} usb)

# Mark executables and/or libraries for installation
install(TARGETS measureTemperature 
  ARCHIVE DESTINATION ${CATKIN_PACKAGE_LIB_DESTINATION}
  LIBRARY DESTINATION ${CATKIN_PACKAGE_LIB_DESTINATION}
  RUNTIME DESTINATION ${CATKIN_PACKAGE_BIN_DESTINATION}
)

