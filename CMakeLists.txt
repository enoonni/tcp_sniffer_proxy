cmake_minimum_required(VERSION 3.20)
project(TcpSnifferProxy LANGUAGES CXX)

set(CMAKE_CXX_EXTENSIONS OFF)
set(CMAKE_CXX_STANDARD 20)
set(CMAKE_CXX_STANDARD_REQUIRED ON)
set(CMAKE_CXX_SCAN_FOR_MODULES OFF)
set(CMAKE_EXPORT_COMPILE_COMMANDS ON)

if(NOT CMAKE_BUILD_TYPE)
  set(CMAKE_BUILD_TYPE Debug CACHE STRING "Build type" FORCE)
endif()

add_executable(TcpSnifferProxy 
  src/main.cpp
)

target_include_directories(TcpSnifferProxy PRIVATE
  ${CMAKE_CURRENT_SOURCE_DIR}/src/
)

target_link_libraries(TcpSnifferProxy PRIVATE
)

target_compile_options(TcpSnifferProxy PRIVATE
    -Wall
    -Wextra
    -Wpedantic
)

target_compile_options(TcpSnifferProxy PRIVATE
  $<$<CONFIG:Debug>:-g3 -O0>
)

install(
  TARGETS TcpSnifferProxy
  RUNTIME DESTINATION bin
)
