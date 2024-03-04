cmake_minimum_required(VERSION 3.25)
project(Cryptia VERSION 0.0.1 LANGUAGES CXX DESCRIPTION "A standalone cryptographic library in C++.")

set(CMAKE_CXX_STANDARD 20)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

list(APPEND CRYPTIA_LINK_LIBRARIES Cryptia.cxx)

if (CRYPTIA_STATIC_LIBRARY)
    add_library(Cryptia STATIC ${CRYPTIA_LINK_LIBRARIES})
else()
    add_library(Cryptia SHARED ${CRYPTIA_LINK_LIBRARIES})
endif()

set_target_properties(Cryptia PROPERTIES VERSION ${PROJECT_VERSION})
set_target_properties(Cryptia PROPERTIES MAJOR_VERSION ${PROJECT_VERSION_MAJOR})
set_target_properties(Cryptia PROPERTIES MINOR_VERSION ${PROJECT_VERSION_MINOR})
set_target_properties(Cryptia PROPERTIES PATCH_VERSION ${PROJECT_VERSION_PATCH})

target_include_directories(Cryptia PUBLIC ${CMAKE_CURRENT_SOURCE_DIR}/inc)