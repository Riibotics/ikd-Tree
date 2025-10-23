find_package(pcl_ros REQUIRED)
find_package(pcl_conversions REQUIRED)
find_package(PCL REQUIRED COMPONENTS common io)

set(DEPENDENCIES
  pcl_ros
  pcl_conversions
)

add_library(ikd-Tree STATIC ikd_Tree.cpp)

# Include directories for third-party headers
target_include_directories(ikd-Tree PUBLIC
    $<BUILD_INTERFACE:${CMAKE_CURRENT_SOURCE_DIR}>
    $<INSTALL_INTERFACE:include>
    ${PCL_INCLUDE_DIRS}
)

# Add ikd_Tree.cpp to the build
target_link_libraries(ikd-Tree Eigen3::Eigen ${PCL_INCLUDE_DIRS})