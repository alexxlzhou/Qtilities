cmake_minimum_required(VERSION 2.9)
project(QtilitiesSessionLogPlugin)

set(SOURCE_FILES
    source/SessionLogMode.cpp    
    source/SessionLogPlugin.cpp    
	)

set(HEADER_FILES
    source/SessionLogMode.h    
    source/SessionLogPluginConstants.h    
    source/SessionLogPlugin_global.h    
    source/SessionLogPlugin.h    
	)

set(UI_FILES  
	)
	
set(QRC_FILES 
    resources/SessionLogPlugin.qrc        
	)

add_definitions(-DSESSION_LOG_PLUGIN_LIBRARY)

include_directories(${Qtilities_header_dir}/QtilitiesLogging)
include_directories(${Qtilities_header_dir}/QtilitiesCore)
include_directories(${Qtilities_header_dir}/QtilitiesCoreGui)
include_directories(${Qtilities_header_dir}/QtilitiesExtensionSystem)

#set(CMAKE_INCLUDE_CURRENT_DIR ON)
add_library(${PROJECT_NAME} ${HEADER_FILES} ${SOURCE_FILES} ${UI_FILES} ${QRC_FILES})

target_link_libraries(${PROJECT_NAME} PUBLIC QtilitiesExtensionSystem
    Qt${QT_VERSION_MAJOR}::Core 
    Qt${QT_VERSION_MAJOR}::Gui 
    Qt${QT_VERSION_MAJOR}::Widgets
    Qt${QT_VERSION_MAJOR}::PrintSupport
)

set_target_properties(${PROJECT_NAME} PROPERTIES 	
	AUTOMOC ON
    AUTORCC ON
    AUTOUIC ON)
	
set_target_properties(${PROJECT_NAME} PROPERTIES FOLDER "Plugins")

install(TARGETS ${PROJECT_NAME}
    RUNTIME DESTINATION ${CMAKE_INSTALL_PREFIX}/bin
    LIBRARY DESTINATION ${CMAKE_INSTALL_PREFIX}/lib
    ARCHIVE DESTINATION ${CMAKE_INSTALL_PREFIX}/lib
)
