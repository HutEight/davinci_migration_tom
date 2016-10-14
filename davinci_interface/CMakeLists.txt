cmake_minimum_required(VERSION 2.8.3)
project(davinci_interface)

find_package(Eigen3 REQUIRED)

catkin_package(
  INCLUDE_DIRS include
  DEPENDS 
    roscpp
  LIBRARIES davinci_interface
  CATKIN_DEPENDS roscpp
)

include_directories(${catkin_INCLUDE_DIRS} ${EIGEN3_INCLUDE_DIR} davinci_interface include)

add_definitions(${EIGEN_DEFINITIONS})

# Libraries
add_library(davinci_interface src/davinci_interface.cpp)
target_link_libraries(davinci_interface ${catkin_LIBRARIES} ${GAZEBO_LIBRARIES})
