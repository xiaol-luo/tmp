

INCLUDE(${CMAKE_SOURCE_DIR}/cmake/Utils.cmake)

cmake_policy(SET CMP0048 NEW)
PROJECT(cg)

IF (NOT CMAKE_BUILD_TYPE)
	SET(CMAKE_BUILD_TYPE Debug CACHE STRING "set Debug or Release")
ENDIF()

INCLUDE_DIRECTORIES(${CMAKE_SOURCE_DIR})
INCLUDE_DIRECTORIES(${CMAKE_SOURCE_DIR}/third_party)
INCLUDE_DIRECTORIES(${CMAKE_SOURCE_DIR}/third_party/learnopengl)
INCLUDE_DIRECTORIES(${CMAKE_SOURCE_DIR}/third_party/glm)
INCLUDE_DIRECTORIES(${CMAKE_SOURCE_DIR}/third_party/glfw-3.3.4/include) 
INCLUDE_DIRECTORIES(${CMAKE_SOURCE_DIR}/third_party/glad/include)
INCLUDE_DIRECTORIES(${CMAKE_SOURCE_DIR}/third_party/assimp/include)
LINK_DIRECTORIES(${CMAKE_BINARY_DIR})
LINK_DIRECTORIES(${CMAKE_SOURCE_DIR})


SET(CMAKE_ARCHIVE_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR}) 
SET(CMAKE_LIBRARY_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR}) 
SET(CMAKE_RUNTIME_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR})

ADD_COMPILE_OPTIONS(-DSTB_IMAGE_IMPLEMENTATION)
ADD_COMPILE_OPTIONS(-DSOL_CHECK_ARGUMENTS=1)
ADD_DEFINITIONS(/MP)
ADD_COMPILE_OPTIONS(/wd4200 /bigobj)
ADD_COMPILE_OPTIONS(-D_CRT_SECURE_NO_WARNINGS -D_WINSOCK_DEPRECATED_NO_WARNINGS)
set(CMAKE_CXX_FLAGS "-std=c++14 ${CMAKE_CXX_FLAGS}")
ADD_COMPILE_OPTIONS(/Zc:__cplusplus)

ADD_SUBDIRECTORY(third_party/glfw-3.3.4)
ADD_SUBDIRECTORY(third_party/glad)
ADD_SUBDIRECTORY(third_party/glm)
ADD_SUBDIRECTORY(third_party/assimp)
ADD_SUBDIRECTORY(third_party/learnopengl)
ADD_SUBDIRECTORY(test_main)
ADD_SUBDIRECTORY(examples)



