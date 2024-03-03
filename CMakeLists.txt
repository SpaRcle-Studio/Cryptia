cmake_minimum_required(VERSION 3.10)
project(Cryptia VERSION 0.0.1 LANGUAGES CXX DESCRIPTION "A standalone cryptographic library in C++.")

set(CMAKE_CXX_STANDARD 20)

set(CRYPTIA_INCLUDE_DIR ${CMAKE_CURRENT_SOURCE_DIR}/inc)
set(CRYPTIA_SOURCE_DIR ${CMAKE_CURRENT_SOURCE_DIR}/src)

add_library(Cryptia SHARED Cryptia.cxx)

set_target_properties(Cryptia PROPERTIES VERSION ${PROJECT_VERSION})
set_target_properties(Cryptia PROPERTIES MAJOR_VERSION ${PROJECT_VERSION_MAJOR})
set_target_properties(Cryptia PROPERTIES MINOR_VERSION ${PROJECT_VERSION_MINOR})
set_target_properties(Cryptia PROPERTIES PATCH_VERSION ${PROJECT_VERSION_PATCH})

set_target_properties(Cryptia PROPERTIES PUBLIC_HEADER Cryptia.h)

target_include_directories(Cryptia PUBLIC ${CRYPTIA_INCLUDE_DIR})
target_include_directories(Cryptia PUBLIC ${CRYPTIA_SOURCE_DIR})

include(GNUInstallDirs)

install(TARGETS Cryptia
        LIBRARY DESTINATION ${CMAKE_INSTALL_LIBDIR}
        PUBLIC_HEADER DESTINATION ${CMAKE_INSTALL_INCLUDEDIR})