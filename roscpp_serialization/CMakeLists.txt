project(roscpp_serialization)

find_package(catkin)

find_package(cpp_common)
include_directories(${cpp_common_INCLUDE_DIRS})

find_package(rostime)
include_directories(${rostime_INCLUDE_DIRS})

find_package(roscpp_traits)
include_directories(${roscpp_traits_INCLUDE_DIRS})

include_directories(include)

add_library(roscpp_serialization src/serialization.cpp)

install(TARGETS roscpp_serialization
    ARCHIVE DESTINATION lib
    LIBRARY DESTINATION lib
  )

install(DIRECTORY include/
        DESTINATION include
        FILES_MATCHING PATTERN "*.h"
        PATTERN ".svn" EXCLUDE)

catkin_project(roscpp_serialization
  LIBRARIES roscpp_serialization
  INCLUDE_DIRS include
  )
