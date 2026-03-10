cmake_minimum_required(VERSION 3.10)
project(MyFirstCppPlugin)

# Указываем стандарт C++17, который требует Endstone API
set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

# Указываем пути к include, чтобы компилятор видел заголовочные файлы
include_directories(${CMAKE_CURRENT_SOURCE_DIR}/include)

# Создаем библиотеку (имя файла будет libmy_plugin.so)
add_library(my_plugin SHARED src/main.cpp)

# Добавляем флаги для статической линковки библиотек C++
# Это решает проблему: version `GLIBCXX_3.4.32' not found
if(NOT WIN32)
    target_link_options(my_plugin PRIVATE "-static-libstdc++" "-static-libgcc")
endif()

# Опционально: если у тебя есть зависимости от самого Endstone
# find_package(Endstone REQUIRED)
# target_link_libraries(my_plugin PRIVATE Endstone::Endstone)
