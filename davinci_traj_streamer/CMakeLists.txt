cmake_minimum_required(VERSION 2.8.3)
project(davinci_traj_streamer)

find_package(Eigen3 REQUIRED)
find_package(actionlib REQUIRED)
find_package(davinci_interface REQUIRED)

find_package(catkin REQUIRED COMPONENTS davinci_interface actionlib)
find_package(Boost REQUIRED COMPONENTS system thread)

catkin_package(
  INCLUDE_DIRS include
  DEPENDS 
    roscpp
    actionlib
    davinci_interface
  LIBRARIES
  CATKIN_DEPENDS roscpp actionlib davinci_interface
)

include_directories(include ${Boost_INCLUDE_DIR} ${catkin_INCLUDE_DIRS} ${EIGEN3_INCLUDE_DIR})

add_definitions(${EIGEN_DEFINITIONS})

# Executables
add_executable(davinci_traj_interpolator_as src/traj_interpolator_both_as.cpp)
target_link_libraries(davinci_traj_interpolator_as
	davinci_interface
	${catkin_LIBRARIES}
)
