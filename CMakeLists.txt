cmake_minimum_required(VERSION 3.10)

project(SpaceInveni LANGUAGES CXX)
set(CMAKE_CXX_STANDARD 11)

#SFML
set(SFML_DIR "/home/landry/libs/SFML/build/")
find_package(SFML 2.5 COMPONENTS graphics REQUIRED)

set(SPIV_LIB_SOURCES 
	src/SpaceInveni.cpp
    )
    
set(SPIV_LIB_HEADERS 
	include/SpaceInveni.hpp
    )
    
set(SPIV_TESTS_SOURCES
    )

add_library(SPIV_lib ${SPIV_LIB_HEADERS} ${SPIV_LIB_SOURCES})
target_include_directories(SPIV_lib PUBLIC ${CMAKE_CURRENT_SOURCE_DIR}/include)

# Main App
add_executable(SpaceInveni src/main.cpp)
# Our library linking
target_link_libraries(SpaceInveni SPIV_lib)
#SFML library linking
target_link_libraries(SpaceInveni sfml-graphics)

# Unit tests
#add_executable(SpaceInveniTests ${SPIV_TESTS_SOURCES})
# Our library
#target_link_libraries(SpaceInveniTests SPIV_lib)
# Catch2 unit testing library
#target_include_directories(SpaceInveniTests PUBLIC ${CMAKE_CURRENT_SOURCE_DIR}/extern/Catch2)
