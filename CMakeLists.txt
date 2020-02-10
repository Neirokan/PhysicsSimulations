cmake_minimum_required(VERSION 3.7)
set(PROJECT_NAME PhysicsSimulations)

project(${PROJECT_NAME})
set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -std=c++17 -static")

set(CMAKE_CXX_STANDARD 17)

set(SOURCE_FILES main.cpp settings.h)

if (CMAKE_BUILD_TYPE STREQUAL "Release")
    add_executable(${PROJECT_NAME} WIN32 ${SOURCE_FILES})
else ()
    add_executable(${PROJECT_NAME} ${SOURCE_FILES})
endif ()

set(SFML_DIR "D:/Libraries/SFML/lib/cmake/SFML")
#set(OPENAL_DIR "D:/Libraries/OpenAL/lib/cmake/SFML")

set(SFML_STATIC_LIBRARIES TRUE)

#set(CMAKE_MODULE_PATH "D:/Libraries/SFML/cmake/SFML")

find_package(SFML 2.5.1 COMPONENTS graphics audio REQUIRED)
if (SFML_FOUND)
    include_directories(${SFML_INCLUDE_DIR})
    target_link_libraries(${PROJECT_NAME} sfml-audio sfml-network sfml-graphics sfml-window sfml-system)
endif ()