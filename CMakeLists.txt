cmake_minimum_required(VERSION 3.7)

project(procurator)

set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

find_package(Qt5 REQUIRED COMPONENTS Widgets ${QT_PREFIX_HINT})

add_subdirectory(src)