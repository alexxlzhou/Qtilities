cmake_minimum_required(VERSION 2.9)
project(Qtilities)

set(CMAKE_MODULE_PATH ${CMAKE_MODULE_PATH} ${CMAKE_CURRENT_SOURCE_DIR}/CMakeModules)
set_property( GLOBAL PROPERTY USE_FOLDERS ON)

#https://doc-snapshots.qt.io/qt6-dev/cmake-qt5-and-qt6-compatibility.html
find_package(QT NAMES Qt6 Qt5 COMPONENTS Core REQUIRED)
#to support Qt 5 versions older than Qt 5.15:
find_package(Qt${QT_VERSION_MAJOR} 5.5 COMPONENTS Core Gui Widgets Xml PrintSupport Network Help Test REQUIRED)

set(QTILITIES_VERSION_MAJOR     1)
set(QTILITIES_VERSION_MINOR     5)
set(QTILITIES_VERSION_REVISION  0)
set(QTILITIES_FILE_VER  ${QTILITIES_VERSION_MAJOR}.${QTILITIES_VERSION_MINOR})
add_definitions(-DQTILITIES_VERSION_MAJOR=${QTILITIES_VERSION_MAJOR})
add_definitions(-DQTILITIES_VERSION_MINOR=${QTILITIES_VERSION_MINOR})
add_definitions(-DQTILITIES_VERSION_REVISION=${QTILITIES_VERSION_REVISION})

if (UNIX AND NOT APPLE)
    include_directories(${Qt${QT_VERSION_MAJOR}Gui_PRIVATE_INCLUDE_DIRS})
endif()

if(BUILD_STATIC)
    set(CMAKE_STATIC_LIBRARY_SUFFIX "_static${CMAKE_STATIC_LIBRARY_SUFFIX}")
endif()

#if(NOT DEFINED CMAKE_DEBUG_POSTFIX)
#  SET(CMAKE_DEBUG_POSTFIX "d" CACHE STRING "add a postfix, usually d on windows")
#endif(NOT DEFINED CMAKE_DEBUG_POSTFIX)
#SET(CMAKE_RELEASE_POSTFIX "" CACHE STRING "add a postfix, usually empty on windows")
#SET(CMAKE_RELWITHDEBINFO_POSTFIX "rd" CACHE STRING "add a postfix, usually empty on windows")
#SET(CMAKE_MINSIZEREL_POSTFIX "s" CACHE STRING "add a postfix, usually empty on windows")

set(CMAKE_INCLUDE_CURRENT_DIR ON)

set(CMAKE_AUTORCC ON)
set(CMAKE_AUTORCC ON)
set(CMAKE_AUTOUIC ON)

option(QTILITIES_NO_HELP OFF)
option(BUILD_SHARED_LIBS "Build shared library." ON)
option(BUILD_EXAMPLES "Build examples." OFF)
option(BUILD_PLUGINS "Build examples." ON)
option(BUILD_TOOLS "Build examples." ON)
option(BUILD_TESTING "Build examples." OFF)

option(QTPROPERTYBROWSER ON)
IF(QTPROPERTYBROWSER)
	set(QTPROPERTYBROWSER_DIR "" CACHE STRING "directory for QtPropertyBrowser")
	find_package(QtPropertyBrowser REQUIRED)
	message(STATUS "QtPropertyBrowser directory and library: " ${QTPROPERTYBROWSER_INCLUDE_DIR} ";" ${QTPROPERTYBROWSER_LIBRARY})
	add_definitions(-DQTILITIES_PROPERTY_BROWSER)
	include_directories(${QTPROPERTYBROWSER_INCLUDE_DIR})
ENDIF(QTPROPERTYBROWSER)

set(Qtilities_header_dir ${CMAKE_CURRENT_SOURCE_DIR}/include)
include_directories(${Qtilities_header_dir})

add_subdirectory(src)
