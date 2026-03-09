cmake_minimum_required(VERSION 3.10)
project(MyFirstCppPlugin)

set(CMAKE_CXX_STANDARD 17)

# Явно указываем полный путь к папке include относительно корня проекта
include_directories(${CMAKE_CURRENT_SOURCE_DIR}/include)

add_library(my_plugin SHARED src/main.cpp)
