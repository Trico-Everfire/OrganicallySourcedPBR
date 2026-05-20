cmake_minimum_required(VERSION 3.31)
project(OrganicallySourcedPBR)

set(CMAKE_CXX_STANDARD 23)
set(CMAKE_AUTOMOC ON)
set(CMAKE_AUTORCC ON)
set(CMAKE_AUTOUIC ON)

find_package(Qt6 COMPONENTS
        Core
        Gui
        Widgets
        REQUIRED)

add_executable(OrganicallySourcedPBR main.cpp
        res/res.qrc
        src/nl_NL.ts
        src/mainwindow.cpp
        src/mainwindow.h)


set(SOURCEPP_LIBS_START_ENABLED OFF CACHE INTERNAL "" FORCE)
set(SOURCEPP_USE_FSPP ON CACHE INTERNAL "" FORCE)
set(SOURCEPP_USE_TOOLPP ON CACHE INTERNAL "" FORCE)
set(SOURCEPP_USE_VTFPP ON CACHE INTERNAL "" FORCE)

add_subdirectory(libs/sourcepp)

target_link_libraries(OrganicallySourcedPBR
        Qt::Core
        Qt::Gui
        Qt::Widgets
        sourcepp::vtfpp
        sourcepp::fspp
        sourcepp::toolpp
)

