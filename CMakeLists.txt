cmake_minimum_required(VERSION 3.21)
project(Engine)

set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED True)

set(SRC_LIST
	src/main.cpp
	src/Core/MacApplication.mm
	src/Core/AppDelegate.mm)
set(HEADER_LIST 
	src/Core/MacApplication.h
	src/Core/AppDelegate.h)

set(RESOURCE "platforms/mac/res/MainMenu.xib")

source_group(TREE ${CMAKE_CURRENT_SOURCE_DIR} FILES ${SRC_LIST} ${HEADER_LIST} ${RESOURCE})

add_executable(${PROJECT_NAME} MACOSX_BUNDLE ${SRC_LIST} ${HEADER_LIST} ${RESOURCE})

target_link_libraries(${PROJECT_NAME} "-framework Cocoa")

set_target_properties(${PROJECT_NAME} PROPERTIES 
	MACOSX_BUNDLE_INFO_PLIST "platforms/mac/Info.plist"
	RESOURCE "${RESOURCE}")
