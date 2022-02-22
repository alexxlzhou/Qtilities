cmake_minimum_required(VERSION 2.9)
project(QtilitiesProjectManagement)

set(SOURCE_FILES
    source/CodeEditorProjectItemWrapper.cpp 
    source/ObserverProjectItemWrapper.cpp 
    source/Project.cpp 
    source/ProjectManagementConfig.cpp 
    source/ProjectManager.cpp 
    source/ProjectsBrowser.cpp 
	)

set(HEADER_FILES
    source/CodeEditorProjectItemWrapper.h 
    source/IProject.h 
    source/IProjectItem.h 
    source/ObserverProjectItemWrapper.h 
    source/Project.h 
    source/ProjectManagementConfig.h 
    source/ProjectManagementConstants.h 
    source/ProjectManagement_global.h 
    source/ProjectManager.h 
    source/ProjectsBrowser.h 
	)

set(UI_FILES 
    source/ProjectManagementConfig.ui 
    source/ProjectsBrowser.ui 
	)
	
set(QRC_FILES 
	)

add_definitions(-DPROJECT_MANAGEMENT_LIBRARY)

include_directories(${Qtilities_header_dir}/QtilitiesLogging)
include_directories(${Qtilities_header_dir}/QtilitiesCore)
include_directories(${Qtilities_header_dir}/QtilitiesCoreGui)

#set(CMAKE_INCLUDE_CURRENT_DIR ON)
add_library(${PROJECT_NAME} ${HEADER_FILES} ${SOURCE_FILES} ${UI_FILES} ${QRC_FILES})

target_link_libraries(${PROJECT_NAME} PUBLIC QtilitiesCoreGui
    Qt${QT_VERSION_MAJOR}::Core 
    Qt${QT_VERSION_MAJOR}::Gui 
    Qt${QT_VERSION_MAJOR}::Widgets
    Qt${QT_VERSION_MAJOR}::PrintSupport
)
#need xml?

set_target_properties(${PROJECT_NAME} PROPERTIES AUTOMOC TRUE)

install(TARGETS ${PROJECT_NAME}
    RUNTIME DESTINATION ${CMAKE_INSTALL_PREFIX}/bin
    LIBRARY DESTINATION ${CMAKE_INSTALL_PREFIX}/lib
    ARCHIVE DESTINATION ${CMAKE_INSTALL_PREFIX}/lib
)
